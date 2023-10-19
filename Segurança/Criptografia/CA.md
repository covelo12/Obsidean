
# Classic Crypto

## Confusão vs Difusão
### Confusão
é uma técnica criptográfica concebida para aumentar a imprecisão do texto cifrado. Em palavras simples, a técnica garante que o texto cifrado não dá pistas sobre o texto simples.
### Difusão 
É uma técnica criptográfica inventada para aumentar a redundância do texto simples para obscurecer a estrutura estatística do texto simples para evitar tentativas de deduzir a chave. Na difusão, a estrutura estatística do texto simples pode desaparecer nas estatísticas de longo alcance do texto cifrado e a relação entre elas é complexa, de modo que ninguém pode deduzir a chave original.



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
A mensagem dividida em N bits
Vai  criar um loop
mix the keystream with the plaintext to get the ciphertext
Encripta-se o IV com a key, assim podemos usar a mesma key várias vezes e temos apenas de mudar o IV nas mensagens
![[Pasted image 20230922154615.png]]

#### Padding
- Para alinhar a mensagem para poder ser encriptada pelo CBC
- Calcula-se  o número de bytes do padding e depois,  nos bytes de padding põe-se esse valor para identificar o padding. No entanto se tudo tiver alinhado tem de se mandar um bloco completo de padding.

### (CFB) Ciphertext Generator
- Pode [[CA#Self Syncronation]]
- A decriptação como é obvio começa sempre do início também, como em todas
- Para decriptação basta pegar em uma parte do  criptograma e inserir no iv e decriptar até ao final
- Não há uniform random access

![[Pasted image 20230929091528.png]]
### (CTR) Counter
- O counter é o estado  do modo 
- Muito prático, pois tens Uniform Random Access logo podes ter computação paralela e podes ter pré-processamento

### DESX
-  Duas novas keys, uma para XOR o input e  outra para XOR o output, adicionando confusão

# Digest Function

#### Colisões
- Quando dois inputs geram o mesmo output
- Quanto menos colisões melhor

## Hash vs Digest????
#### Hash 
- Colisões são fáceis de encontrar
- Não faz mal  encontrar a função inversa
#### Digest 
- **Collision resistance** - Colisões não conseguem ser encontradas( eg. MD5 é fraca com colision resistance mas algumas utilizações não faz mal se for por exemplo com password pois precisas de saber uma password em primeiro lugar, não podemos usar para assinar )
- **Preimage resistance** - Não se pode prever a função inversa, logo a partir do output não se encontra o input.
- **Second Preimage resistance** - ==A partir de um  texto== impossível encontrar um outro com o mesmo digest

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

# Aritmética modular
*SAIU*`Temos uma gama finita bem defenida de valores, que facilmente permite guardar informacao. E pode ser implementada eficientemente em todos os computadores. E tem muitas aplicações criptográficas. `
## Notation
![[Pasted image 20231006092436.png]]
Scramble information in a way that is very difficult to unscramble without the key.

