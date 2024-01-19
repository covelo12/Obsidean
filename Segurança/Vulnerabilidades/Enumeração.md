---
"Cadeira": "AEV"
Tags: "#Aula"
---
Links:
___ 
```dataview 
list 
from "Segurança/Vulnerabilidades" 
WHERE Cadeira = "AEV" and tags="#Conceito" and Numero=3 sort file.cday
```

O acesso indevido a redes pode ser o *ponto inicial para um ataque* visto que acedendo a rede pode se *evitar várias medidas de segurança.* (Leis, Edifícios) e atacantes podem obter vários tipos de informação perigosa.

#### Recolha de informação
##### Erros
Mensagens de erros podem conter demasiada informação sobre processos, dados, ou  versões do software

**Como mitigar:**
- *Não pôr erros com muito detalhe* para o utilizador,  pôr no log
- Para o utilizador, temos de focar na *operação como um todo*. (Operação teve sucesso ou falhou)

##### Ficheiros de suporte
Ficheiros com *demasiada informação* sobre o funcionamento do sistema podem ter sido deixados pelos developers.( Logs, backups)

##### Cookies
Cookies enviados têm *informação sobre o sistema* que corre no server

##### Portos
Estes comportam se de maneira diferente dependendo se estão *abertos/fechados* e do tipo de *protocolos* que correm e a *existência de uma firewall*. Podemos mitigar a enumeração de portos *com uma firewall.*

##### Banners
Podem conter informação sobre o *software que corer no servidor*. Para mitigar podemos *restringi-los*, *banners falsos, e limitar o detalhe* que estão contidos nele
##### OS Fingerprint 
Cada stack de network tem um *comportamento diferente*,  que pode ser usado para *perceber que stack* está a ser usada com probes ou observando respostas. Para mitigar podemos restringir o número de portos abertos, usar uma firewall para detetar enumeração.