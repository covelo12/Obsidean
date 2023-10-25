Rever: modo de cifra
1-
i)- Um cifra de Vernam consiste na pratica de o uso de uma keystream aleatória criada pelos utilizadores e partilhada pelos 2.  Essa keystream têm o mesmo tamanho que a o plaintext  e so dois serão feitos XOR para o resultado ser o criptograma. 
ii)-É impossível de criptografar, no entanto se uma chave for usada mais que uma vez, é facilmente percebida as mensagens e a chave. 
iii)-  Alguns contratempos impediram que a cifra de Vernam fosse vastamente usada:
- Facilidade de passagem de segredo: não é necessário passar a keystream toda, apenas a seed.
- Facilidade de gerar a keystream: Como era impossível gerar uma sequencia aleatória de números, os geradores vieram  fazer isso de maneira mais aleatória possível.
- É desnecessário guardar a keystream toda,  só a seed.  e uma seed dá para todos os plaintexts uma vez que  o gerador pseudo-aleatório gera infinitamente.


2- ShiftRows e MixColumns-  Fazem a informação de uma palavra estar espalhada no texto todo. Como são as operações de shift são as únicas que contribuem para a difusão que é a propriedade em que a informação do texto original está dispersa igualmente no criptograma

3- Eu escolheria o OFB , não tem uniform random access para decifra.

4- Sim , pois  cada byte vai ser substituído por um byte diferente devido ao modo CBC se basear na operação XOR  que apenas substitui bytes por uns diferentes. A definição de poli-alfabética é substituir uma letra por outra, sendo que a letra que substitui diferente cada vez. logo  a definição de poli alfabética aplica-se ao modo CBC.

5-  
Encrypt then MAC-  Encripta-se e calcula-se o MAC do criptograma.
MAC then encrypt-  Calcula-se o MAC e encripta-se a mensagem e o MAC
Encrypt and MAC-  Calcula-se o MAC e encripta-se a mensagem apenas, não o MAC
Assim a melhor para verificar se recebemos uma mensagem inválida seria o Encrypt then MAC e o pior é  o MAC then encrypt, sendo o melhor porque não temos de desencriptar a mensagem e o pior porque temos de desencriptar a mensagem toda e o MAC também.

6- O protocolo serve para combinar um número secreto numa rede não segura. O que o torna seguro é o facto de a partir de  r, p ,A e B
ser muito difícil computar $r^{ab} mod p$

7- 
 Os dois concordam em um elliptic curve e num ponto nela P. Alice decide $\alpha$ e  faz $\alpha P$  e envia a Bob, bob decide $\beta$ e faz $\beta P$ e envia a Alice, os dois conseguem então chegar ao resultado $\alpha \beta P$