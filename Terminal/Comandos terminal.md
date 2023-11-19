# Updates e Upgrade
 `sudo apt-get update`
 `sudo apt-get upgrade`
 `sudo snap install --classic code`
 

# Serviços/Protocolos

## SMB
- *Listar todas as shares* que estão na rede `smbclient -L IP`

## REDIS
- Para *entrar na rede Redis*  `redis-cli  -h IP`
- Depois de estar conectado à rede,  para *obter informação e estatísticas do servidor* `Info`
- Para *selecionar uma base de dados* depois de conectado ao servidor `select NUMERODABASEDEDADOS`
- Para *mostrar todas as chaves* na tabela selecionada `keys *`
- Para *mostrar todos os valores das chave* selecionada `get CHAVE`

## MYSQL
- Para *entrar no server* MYSQL `mysql -h IP -u USER`
 - para *mostrar todas as bases-de-dados/tabelas do servidor*`show databases/tables;`
 - Para *selecionar uma base de dados* depois de conectado ao servidor`use NOME`
 - Para *mostrar uma tabela* `describe TABELANOME;`
# Criptografia

### gpg
- ***Decriptar:*** `gpg --output original_message.txt --decrypt message.gpg`
- ***Encriptar:***  `gpg --symmetric --cipher-algo CIPHER message.txt` *Cipher*- nome do algoritmo,  acrescentar a opção``--armour`` para ficar em ASCII
### Openssl
- **Encriptar:** `openssl CIPHER -e -in message.txt -out encrypted_message`*Cipher*- nome do algoritmo, e.g.: `aes-256-cbc`, `-pbkdf2 -iter 10000 `Para aumentar a dificuldade de brute force.
- **Decriptar:** `openssl CIPHER -d -in encrypted_message -out original_message.txt` *Cipher*- nome do algoritmo, e.g.: `aes-256-cbc`.  `-pbkdf2 -iter 10000` decriptar com pbkdf2

### RSA
- **Criar Private  Key**  `openssl genrsa -out private-key.pem 2048`
- **Criar Public key**`openssl rsa -in private-key.pem -pubout -out public-key.pem`
- **Encriptar**  `openssl pkeyutl -encrypt -in plaintext.txt -out ciphertext -inkey public-key.pem -pubin`
- **Decriptar** `openssl pkeyutl -decrypt -in ciphertext -inkey private-key.pem -out decrypted.txt`

### Diffle-Hellman
Para trocar chaves num canal inseguro
- **Criar**  `openssl dhparam -out dhparams.pem 2048`
- **Ver parâmetros**  `openssl dhparam -in dhparams.pem -text -noout`

### Certeficados
- **Ver o certificado** ``openssl x509 -in cert.pem -text`
- **Gerar certificado auto-assinado**  `openssl req -x509 -newkey -nodes rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365` 


# Vulnerabilidades
## PING
- Usar a o apêndice -c3 para fazer apenas 3 pings
## Gobuster
- Para *detectar sub-diretórios* no gestor de ficheiros do servidor `dir --url http://10.129.42.19/ --wordlist /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`
## Nmap
`Script para dar Scan aos portos `

### Flags
-  `-sV` mais informações sobre a versão dos portos 
- **Tipos** `-sT` para portos [[TCP]] 
	- -`-sU` para portos [[UDP]], estes scans são lentos então é boa prática usar `--top-ports <number>`  enabled.  e.g. ( `--top-ports 20`,  vai apenas examinar  os 20 portos mais comuns)
	- `-sS` usado para efetuar um [[Comandos terminal#Syn-scan | Syn Scans]] 
	- `-sn` varredura de IP `- nmap -sn 192.168.0.1-254`, não dá scan a portos, apenas vê os IPs conectados à rede
	- ##### Passar Firewall
	- `-f` Fragmenta os packets fazendo que seja mais fácil escapar à Firewall
	- *Null `-sS` Fin `-sF` e Xmas `-sX` flags usados para passar a firewall* a a partir de não se ligar aos portos
	- `--scan-delay <time>ms` Usado para adicionar delay ao envio de pacotes, útil se a rede for instável
	- `--badsum` Usa pacotes inválidos, usado para detectar a presença de [[##firewall]] ou [[IDS]]
#### Syn-scan
- Scans usados no range de portas [[TCP]], mas diferente do scan [[TCP]] normal .
- Quando o servidor enviar um packet com  as flags [[Siglas#Syn | Syn]] e [[Siglas#Ack | Ack]], o cliente(atacante), responde com um  pacote com a flag [[Siglas#Rst | Rst]].

##### Vantagens
- Capacidade de  *escapar a sistemas de detecção de intrusão mais velhos*,  uma vez que estes apenas estão à procura do [[TCP#Three way Handshake | Three way handshake]]. [[IDS]] mais novos já não são enganados.
- Normalmente estes *scans não são escritos no log*, uma vez que é prática comum só se escrever no log as conexões ja feitas.
- *Mais rápidos*  uma vez que não têm de completar nem desligar dos portos scaneados.

##### Desvantagens
- *Necessitam de permissões de super-utilizador.*
- *Serviços instáveis podem ser levados a baixo* pelos  syn-scans.





## WFUZZ
- Para *descobrir sub-dominios* escondidos que podem ser importantes `wfuzz -w /usr/share/wordlists/dirb/common.txt -u http://jupiter.htb -H "Host: FUZZ.jupiter.htb" --sc 200`  

<abbr title="Hpertext Markup Language">  
HTML  
</abbr>  
<cite title="Inventor of HTML">Sir Tim Berners Lee</cite>  
<dfn title="The popular language of the World Wide Web. Commonly abbreviated to HTML">Hypertext markup language</dfn>  
