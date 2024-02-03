Links: [[Projeto AWS]], [[Conceitos Base]]
___

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
