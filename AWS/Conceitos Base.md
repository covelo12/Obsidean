- Provem acesso a serviços tecnológicos de salvaguarda de dados, poder de processamento e bases de dados.

# Definições
## Data Warehouse 
	Dados não essencias para o bom funcionamento de um aplicação

# S3 bucket
	Simple storage service
- Corre website estáticos 
- Cada bucket tem de ter um nome único
- Guarda e devolve qualquer tipo de dados 
- Para guardar dados temos de ter um tipo de **contentor**.
- Scripts do servidor têm de estar no S3 bucket com os dados
- Cada objeto é identificado com a combinação bucket + key + version
- ![[Pasted image 20231121142850.png]]
- **S3 Storage class analysis** é uma ferramenta que estima a melhor classe de armazenamento, para um tipo de dados
- **(CRR) Cross-Region Replication** Replicar dados entre regiões
- **(SRR) Same-Region Replication** Replicar dados na mesma região
- **S3 Object Lock** Apenas podes ler os dados e não eliminar
- **S3 Inventory** Lista os objetos e o status de encriptação desses objetos


# EC2
	Elastic Compute Cloud
- Oferece capacidade computacional na cloud

## Instâncias
- **Proposito geral** - Balanço entre CPU, memória e redes e.g.: Webservers
- **Optimizados computacionalmente** - Indicados para trabalhos pesados computacionalmente e.g. Game servers
- **Optimizados na memória** - Indicados para trabalhos pesados para com memoria, com necessidade de grandes conjuntos de dados. e.g. Gandes análises de dados
- **Optimizados para armazenamento** -  Indicados para trabalhos que precisam de acessos à memoria sequencializados,  com grandes conjuntos de dados. e.g. Data Warehouse
- **Accelerated computing** -Com grande GPU Machine Learning
- **HPC optimized** Simulações complexas

## (EBS) Elastic Block Store
	Dá a oportunidade de dar aramzenamento do tipo block a uma instancia EC2

- Possibilidade de mudar de tipo de volumes
-  Comportam se como dados não tratados  nem formatados na nuvem 
- Cada EBS só pode ter uma instância EC2 mas uma instância EC2 pode ter vários EBSs.
- Baixa latência
- Bons para *serviços com muitas transações*.
- Persistência de dados.
### EBS Snapshots
- Uteis para fazer backups 
### Tipos de Volumes
#### SSD
- Otimizado para frequentes operações R/W com pouca informação e.g. Bases de dados
#### HDD
Otimizado para baixa latência e tudo para o que o SSD não da. 
e.g.  Processamento de Logs, Data Warehouse

# VPC 
## Subnet
Parte do range de IPs do VPC
- Uma subnet tem de estar contida numa AZ
- 5 subnets por AZ
- Tem de estar associada a uma route table
- Têm uma [[Redes - Conceitos base#Route tables | Route Table]]

#### (NACL) Network Access Control List
- Vem por default em todas as subnets, deixa passar todo o trafego
- Tem uma lista de regras, que define quem deixa entrar ou não, quanto mais acima estiver a regra, mais prioridade tem
- Security groups não deixam entrar mas deixam sair tudo, por default

# CloudFormation
Maneira de gerir a arquitetura de vários serviços AWS ao mesmo tempo.
- A partir de um JSON definir a configuração  infraestrutura que queremos