## Aulas
```dataview
list from "Segurança/Vulnerabilidades" WHERE Cadeira = "AEV" and tags="#Aula" sort file.cday
```

### Vulnerability assessment 
`Processo de analizar evaliar e rever entidades`
`Identificar e categorizar problemas e lidar com elesassertadamente `

### Tecnologias defensivas

**Firewall**-Bloqueia conexões 
**WAF** - Para não executar pedidos HTTP  com malware
**IDS** - Monotoniza pedidos esquisitos 

~´

#### Limites dos assessments
**Tempo**- temos um determinado tempo
** Temos de estar a par das vulnerabilities** 
**Limitados ao scope** - O que os hackers não estão e se for preciso mandar o sistema abaixo mandam 

## Approaches
### Blackbox
Não consegue saber nada tem de entrar ás escuras
### Whitebox
Sabe tudo, Código fonte etc. e até pode esclarecer duvidas

### Greybox
Alguma documentação mas não toda, ex:  Domínio e credenciais mas não acesso ao código fonte
## Tipos de Ataques 
##### Ativo`Desrruptir a espresa/Networks` 
###### Passivo ``Monotorizar o trafego,  logo tem pouco impacto``
##### Externo `Tentar atacar de forma externa`
##### Host Based `Tirar a vantagem das más configurações existentes`
##### Network `Tentar encontrar vunerabilidades na rede, sabemos que há comunicação e tentar identificar quais são as máquinas`
##### Wireless `A partir de redes wireless`
##### **Applications** `Tentar tirar partido das aplicacoes de um usuario`

## Ciclo de vida de gestão de vulnerabilidade
- **Baseline** O que vamos corrigir e o que não vamos corrigir, as mais perigosas,  as que podem ter remendo e o que pode ser ignorado por agora
- **Assessment** Construir relatório com as vulnerabilidades descobertas, zonas afetadas e como as afeta, que recomendações a oferecer para quem vai resolver **Métodos**: [[#Aplicação]] **Estratégias**:[[#Blackbox]], [[#Whitebox]] , [[#Graybox]]
- **Risk Management** Documentação do que vamos/quando e como quando vamos corrigir
- **Remediation** Empresa tenta implementar os métodos de correções propostos
- **Verificação**-Verificar que a remediação funciona
- **Monitorização**- Detectar a vulnerabilidades não resolvidas estão a ser exploradas

##### Aplicação
**Estática**- Vai ver o código e tenta identificar as vulnerabilidades.
**Dinâmica**- Interage com a aplicação, tenta um username muito grande, ou sem pass etc.
Component Analysis- Wireshark,  

##### Processo
OSINT/ Social Engineering - Tentar receber informações por métodos sociais. 

# #3 - Enumeration and Information Leakage

## Network Access
	-Para saber qual é o tipo de software que corre num servidor temos de fazer "Perguntas" e assim perceber a verssã e os cves accossiados.

### Information Leak
	-Entities provide information enabling the discovery of known vulnerabilities
#### Erros
	Mensagens podem fornecer demasiada informação
##### Mitigações 
	Não dar erros com demasiada informação aos users
	Dar um código de erro 
	Autenticação é bem-succedido ou não
	Ficheiro pode ser accedido ou não

#### Ficheiros de Suporte 
	Acesso a ficheiros de suporte que não deviam e que dão informação adicional

#### Cookies
	A Maneira como estão organizados dizem qual a versão/framework estão a ser gerados

#### Ports
	Comportam-se maneira diferente conforme se estão abertos/fechados
	Cada porto costuma ter um serviço acossiado(TCP port 88 etc)

#### Banners 
	Alguns conjuntos de texto providdos proa lguns servicos
##### Mitigações
	Falsos banners
	Restringir banners
	Limitar o verbose de Banners

#### Fingerprints
	A maneira como ele responder pode dar informação sobre o sistema

##### Mititgações 
	Menos portos abertos
	Detetar enumerações

#### 
### Vetor de ataque
	-Serviço que pode ser uma vulnerabilities
	- Conjunto de vulnerabilities que dão accesso ao sistema

### Port-Knocking 
	Cadeia de  portos que temos de acessar para abrir a porta qeu queriamos inicialmente

# Injection 
Várias falhas:
- Divulgação de informação importante
- Falha de autenticação
- Perda de integridade dos sistemas
- Perda de não-repudiação
- Execução de código
## Como evitar
- Não confiar em fontes externas
- Não misturar dados com código
- Sanitizar todos os dados
  Não confiar em fontes externas desde dados dados pelo utilizador, pela API, ou pela base de dados.

## Base de dados ACID
- Atomicity: transactions are either completed or not.
-  Consistency: the database is in a valid state.
-  Isolation: a transaction is made in a isolated context, until a final commit.
- Durability: after a commit a change is persisted.
Organizadas em:
- Base de dados
- Tabelas
- Nome Colunas
- Linhas
- Colunas
# Broken Authentication
Cookie de autenticação- String que deixa o utilizador estar no servidor sem a continua autenticação, para assim não precisar de uma autenticação por click.
- Uma técnica comum é  os ataques por dicionário, tentar as passwords mais conhecidas 
## Web-request
- A partir do domínio  vai se buscar o IP
- A partir do IP liga-se ao servidor
- Normalmente [[HTTPS]]