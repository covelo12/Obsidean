Hypertext Transfer Protocol Secure
- Protocolo Web que verifica a autenticidade de uma ou as duas partes
# Primeira interação
- Cliente pede o certificado TLS/SSL do servidor
- Servidor dá o certificado assinado 
- Cliente valida se o certificado é válido, ele decripta a hash que vêm com o certificado com a chave publica que o assinou e vê se a hash que ele próprio gerou é igual.