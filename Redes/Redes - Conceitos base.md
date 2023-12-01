## Definições
**Client-Server Model** - Implica duas máquinas uma dela o servidor que fica a  ouvir o cliente, e o cliente pode pingar ou pedir serviços ao servidor

**Named-based Virtual hosting** - Maneira de por dois domínios em um único servidor com um único IP

## Protocolo de Rede 
Um protocolo de rede é um conjunto de regras e convenções que permite a comunicação entre dispositivos em uma rede de computadores. Especificamente, ele define os procedimentos e formatos que os dispositivos em uma rede usam para trocar informações.
e.g. [[HTTPS]] ,[[FTB]],[[TCP]],[[SMB]],[[UDP]], 

## VLANS
	Virtual lan

### Portos
#### Portos de acesso
- Comunicam-se com os aparelhos de forma normal por tramas internet
- Apenas ganham o ID da VLAN quando chegam ao switch

#### Portos TRUNK


### 802.1Q
	.1Q
- Adiciona um campo de 4 bytes num pacote na rede, *0 equivale a sem  VLAN*  e o número *1 é associado à VLAN administradora* .
-  Um pacote Broadcast(F::F) apenas atinge *aparelhos na mesma VLAN*, no entanto
- Uma VLAN pode ser usada para cada tipo de utilizador( Administradores, Convidados, Managers, etc.)
#### 802.1AD
	Q-in-Q , Stacked Vlans
- Podemos empilhar campos 802.Q1 para que possamos usar várias VLANS empilhadas umas nas outras, sendo uma para um possível para prestador de internet e outro para o cliente.

## Route tables
- Tem um conjunto de regras chamado *routes*, para determinar para onde o trafego da subnet é direcionada. Têm de se usar uma subnet publica para serviços conectados com a internet e privada para os que não estão conectados.
- 