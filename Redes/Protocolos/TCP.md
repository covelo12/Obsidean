# TCP
### Three way Handshake
`Maneira de o cliente e o servidor  começarem a "Conversar"`
- Cliente: Packet com a flag **[[Siglas#Syn | Syn]]** Server com as flags **Syn** e **[[Siglas#Ack |Ack]]** , Cliente com a flag **Ack**
-  Caso o porto esteja fechado Client-> Syn, Server -> **[[Siglas#Rst | Rst]]**
- Pode estar protegida por uma [[firewall]], nesse caso *não retorna flag nenhuma*, ou para enganar hackers pode também retornar um packet **Rst**