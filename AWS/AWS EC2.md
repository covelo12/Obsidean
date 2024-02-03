---

---
Links: [[Projeto AWS]], [[Conceitos Base]]
___

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