# Definições
## Data Warehouse 
	Dados não essencias para o bom funcionamento de um aplicação



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

