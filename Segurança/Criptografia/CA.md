
# Classic Crypto
## Segurança do ponto de vista teórico vs Computacional
### Teórico 
- Todas as mensagens são possíveis
- Todos os criptogramas são possíveis
- Todas as keys são possíveis
### Computacional
- Número de keys finito,  é ainda menor que o número de mensagens
- Segurança depende do poder computacional de quem quer quebrar a cifra
- Demonstração da segurança pode ser dada através da comparação com problemas


## Confusão vs Difusão
### Confusão
Em palavras simples, a técnica garante que o texto cifrado não dá pistas sobre o texto simples. *Esconde padrões* entre chave e texto cifrado.
### Difusão 
Isso significa espalhar as propriedades estatísticas do texto original de forma mais uniforme possível no texto cifrado. A ideia é que qualquer alteração mínima no texto original resulte em *grandes mudanças no texto cifrado*.

## Transposição
- Texto original embaralhado
## Substituição
### Mono-alfabeticas
- substitui-se uma letra por uma letra.
- Não escondem padrões
- Análise estatística facilmente quebra. 
### Poli-alfabeticas
- substitui-se uma letra por uma letra, mas não sempre a mesma.
- Assim que o período é sabido podemos criptoanaliza-se como se fossem *N* monoalfabéticas
- Homophonic: Substitui-se uma letra por muitas.


## Critérios de Shannon 
Critérios utilizados para saber se um cifra é boa ou não 
- A quantidade de secrecidade necessária deve determinar a quantidade de trabalho a encriptar e decriptar
- Complexidade da seleção da chave
- Simplicidade de implementação
- Propagação de erro não deve acontecer 
- O tamanho da cifra não deve ser muito maior que o tamanho do texto 
## A cifra deve ser resistente 
- A saberem o algoritmo
- Terem amostras  de muitos criptogramas com a mesma chave 
- Saberem parte do texto original 




# Modern Symmetric cryptography 

## Moderns Cyphers

### Concerning operations
#### Block Cyphers
Use blocks of bits to encrypt a message
#### Stream Cypher 
Misturar a chave com o texto, normalmente com o XOR,
P XOR K = C
C XOR K =  P
P- plaintext K-key C-cypher

Como as keys eram muito grandes precisamos de usar um gerador [[CA#Gerador pseudo-aleatorio]]

##### Gerador pseudo-aleatorio
- A partir de uma chave conhecida gera uma sequencia pseudo aleatória  (==keystream==) de caracteres que então podem ser usado para fazer o XOR assim não precisamos de uma chave muito grande.
- No entanto isto tem um problema uma vez que a keystream pode tem um ==período==.
- Apenas podemos usar cada keystream uma vez, que fazendo XOR de duas cifras o resultado será a mesma coisa que o XOR dos dois textos
- As keystreams não têm [[CA#Confusão vs Difusão]]
- Normalmente sem [[CA#Random Access]] nem [[CA#Self Syncronation]]



##### Random Access
Podem ter ou não acesso aleatório, ou seja podes prever os bits numa determinada posição sem calcular o que vem antes. EG: ChaCha
Algumas podem ter Random Access na encriptação e não na decriptação.

##### Self Syncronisation 
Quando há um shift na keystream e o plaintext não se perde toda  

### Concerning the key
#### Symmetric Cyphers 
- A chave secreta era partilhada por 2 pessoas e serve para confidenciar uma mensagem entre duas pessoas,  também pode servir para **autenticar** as mensagens.
- ==Boa performance==
- ==É chato ter que distribuir as chaves secretas==

##### Symmetric block cyphers

#### Asymmetric Cyphers 

## Cryptography algorithms

### Feistel Networks
![[Pasted image 20230922133651.png]]
### DES
- Usa 16 Feistel Networks
- Usa Subkeys calculated a partir da chave principal
- Feita para ser fácil de implementar em Hardware
- As ==chaves são muito pequenas==,  mas mais tarde foi descoberto como aumentar o tamanho das chaves
- Podemos fazer três encriptações, (EDE) Encrypt-Decrypt-Encrypt  para faze-las retrocompatíveis com maquinas que só faziam uma encriptação  
![[Pasted image 20230922134927.png]]
### AES
- Substitution permutation networks
- ![[Pasted image 20230922141454.png]]
- ![[Pasted image 20230922141503.png]]
- ### (LFSR) Linear Feedback Shift Register
- Utilizado para criar keystreams nos geradores pseudo-aleatórios
- Temos de ter cuidado para não termos uma sequência de 0's uma vez que 0 é o estado absorvente 
- ![[Pasted image 20230922150935.png]]
# Cypher modes

## For block cyphers

### EBC 
- Dividir a mensagem em blocos, encriptar cada bloco com a mesma chave e concatenar para obter o criptograma, para decriptar,  fazer o reverso,  o ==ultimo bloco tem de levar padding==
- ==Mono-alfabetico==
- Necessário introduzir confusão, criando [[CA#CBC]]
### CBC
- Utilizar o ultimo bloco na encriptação do próximo
- A encriptação não pode ocorrer paralelamente, embora a decriptação pode
- Ao mudar um bit, o bloco do bit fica todo mudado e muda um bit do proximo bloco.
- ==Poli-alfabético==, introduzindo confusão
- (IV) Initialization Vector - Valor que pode ou não ser secreto para a encriptação do primeiro bloco

### OFB
- Cifra de blocos
- IV inicial aleatório
- Encriptar o IV com a key → Plaintext XOR E(IV) → *Últimos N bits de E(IV) vão para o inicio do IV para o próximo bloco*
- Assim como é preciso do ultimo bloco encriptado para calcular o iv do proximo bloco, *não há parallel processing*  
![[Pasted image 20230922154615.png]]

#### Padding
- Para alinhar a mensagem para poder ser encriptada pelo CBC
- Calcula-se  o número de bytes do padding e depois,  nos bytes de padding põe-se esse valor para identificar o padding. No entanto se tudo tiver alinhado tem de se mandar um bloco completo de padding.

### (CFB) Ciphertext Feedback
- Pode [[CA#Self Syncronation]]
- A decriptação como é obvio começa sempre do início também, como em todas
- Para decriptação basta pegar em uma parte do  criptograma e inserir no iv e decriptar até ao final
- Não há uniform random access


![[Pasted image 20230929091528.png]]
### (CTR) Counter
- Igual ao OFB
- O estado do IV é baseado num counter permitindo que  se possa calcular facilmente o estado do IV para cada um dos blocos.
- Muito prático, pois tens Uniform Random Access logo podes ter computação paralela e podes ter pré-processamento

### DESX
-  Duas novas keys, uma para XOR o input e  outra para XOR o output, adicionando confusão

# Digest Function

#### Colisões
- Quando dois inputs geram o mesmo output
- Quanto menos colisões melhor
#### Digest 
- **Collision resistance** - Colisões não conseguem ser encontradas( eg. MD5 é fraca com colision resistance mas algumas utilizações não faz mal se for por exemplo com password pois precisas de saber uma password em primeiro lugar, não podemos usar para assinar )
- **Preimage resistance** - Não se pode prever a função inversa, logo a partir do output não se encontra o input.
- **Second Preimage resistance** - ==A partir de um  texto== impossível encontrar um outro com o mesmo digest

## Rainbow Tables
- Consiste na computação de hashes para encontrar colisões
- Para um input é calculado o seu hash, esse hash é passado a uma função que determina o próximo input da função de hashing
- A função que determina o input é provável de gerar colisões


## Merkle-Damgård construction
	- Comprimir iterativamente até chegar ao tamanho ideal
	- Padding com  o formato 1(zeros)(Tamanho da mensagem) de maneira a fazer um output mais variado
## Sponge functions
- Não é uma função de hash, output não fixo,  bloco fundador das funções de hash
- **Absorption** - Constante atualização do estado interno para a geração de 
- **Squeezing** - O Output tem um tamanho arbitrário dependendo do estado interno
## (MACS) Message Authentication Codes
	- Usado em criptografia, para perceber se as  mensagens foram alteradas e/ou foram enviadas pelo emissor

### Tentativas de MACS

#### CBCMAC
	- O MAC era apenas  a ultima parte da mensagem encriptada com CBC
	- Muito pesado

#### KeydMD5
	- Pôr na  calculação do MAC a chave, e como só alguns sabem a chave é complicado mudar o MAC para os interceptores

## Authenticated Encryption 
	- Quando fazes autenticação e encriptação ao mesmo tempo 
	- Se mudares alguma coisa no criptograma quem decodificar a mensagem irá saber

### (GCM) Galois/Counter Mode
- [[CA#(CTR) Counter]] com autenticação
- Numero, que vai ser multiplicado com o cyphertext de forma a ter um numero final, ou seja se mudarmos o criptograma o numero vai mudar
### (CCM) Counter with CBC-Mac
#### Encrypt then MAC
	-O MAC é feito pelo criptograma
	-Tem de haver 2 chaves
	-Não tens de decriptar a mensagem para ver se a mensagem é real

#### Encrypt and MAC
	-Mac feito do plaintext
	-Só podes validar o texto após o decriptar

#### Mac then encrypt
	-MAC a partir do  texto
	-Encriptar o texto e o MAC 
	-Não se  consegue ver o MAC  então é complicado de chetar

# Gerenciamento de chaves assimétricas
## Geração de chaves
*Bons geradores aleatórios*
Os geradores de chaves devem ser o mais aleatórios possível

*Chaves publicas eficientes*
- Poucos bits, normalmente $2^{k+1}$ 
- Assim as  operações são rápidas e eficientes
- Não há problemas de segurança

*Auto-geração de chaves publicas*
- Melhora a privacidade
- Não é necessário caso não se envolva assinaturas

## Exploração de chaves
### Uso correto de chaves
*A chave representa uma pessoa*
- Assim tem de ser segura
- E um backup físico tem de existir
*O acesso à chave tem de ser controlado*
- Com uma password ou pin
- Aplicações que usam a chave como adobe reader tem de ser corretas com o seu uso
### Confinamento de chaves
*A chave tem de estar contida em um domínio seguro do sistema*

## Chaves  publicas

**Distribuição para quem vai enviar informação confidencial**
- Manual 
- Usando Diffle-Hellman
- Usando certificados digitais
**Distribuição para quem vai receber a informação confidencial**
- Usando certificados digitais
**Distribuição de chaves publicas**
- Através de caminhos de confiança
- Se *A* confia em **B** e **B** confia em <span style="color:#ffc000">S</span> então *A* confia em <span style="color:#ffc000">S</span>
- Isto gera as hierarquias de certificação
- Pode-se fazer mandar uma assinatura do documento e ao mesmo tempo uma certificação em que a chave publica que podes usar para verificar a assinatura é minha.

### Certificados digitais
- Certificados produzidos por [[#Entidade certificadora]]
- ligam uma entidade/pessoa a uma chave
- São documentos públicos
- São seguros criptograficamente
#### Usados para distribuir chaves de maneira segura
- O receptor de um certificado pode autenica-lo e valida-lo
- Se quem assinar o certificado é confiado e a assinatura do certificado está correta então o receptor pode confiar na chave publica que está no certificado

#### Entidade certificadora



## PKCS #11
