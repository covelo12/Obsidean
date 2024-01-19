# Objetivos
- Assegurar a integridade de um documento 
- Assegurar a identidade do criador
- Não-repudiação

#### Elementos
- **Mensagem** 
##### Data da assinatura 
- Normalmente requerida, uma vez que os pares de chaves tem data de expiração
- Pode ser dada pela *maquina que assinou*, mas não é muito seguro mas também pode ser dada por uma *Time Stamping Authority* 
##### Identidade assinante
- Identificada por um *certificado chave privada x.509* que provê alguns atributos do assinante, a *chave publica* e o espaço temporal em que a chave pode assinar
##### Opcional
- **Localização**
- **Razão**
- **Aparencia**
#### Esquema
##### Recuperação de mensagem
- Mensagem recuperável depois de verificação da assinatura
- Só se pode ver a mensagem depois da verificação
##### Apendix
- Assinatura desanexada da mensagem
- A mensagem pode ser vista a qualquer altura

#### Algoritmos
##### Em recuperação de mensagem
- Criptografia Assimétrica

$$ Ass(doc)= info + E(Key,  doc)

