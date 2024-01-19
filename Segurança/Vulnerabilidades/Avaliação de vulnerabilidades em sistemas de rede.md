---
"Cadeira": "AEV"
Tags: "#Aula"
---
Links:
___ 
# Conceitos
```dataview 
list 
from "Segurança/Vulnerabilidades" 
WHERE Cadeira = "AEV" and tags="#Conceito" and numero = 2 sort file.cday
```
# Objetivo 
Analisar avaliar e rever entidades
Encontrar e categorizar vulnerabilidades

### Avaliação
Normalmente usados 3 métodos:
- [[Auditoria]]
- [[Avaliação  (Assesment)]]
- [[Penetration Test]]


Esta avaliação é necessária para sabermos *quais as vulnerabilidades* do sistema, *o que temos de resolver* e *em que ordem*
##### Limitações
- Avaliação apenas válida num ponto de tempo
- Investigador precisa de estar a par das ultimas vulnerabilidades
- Limitado pelo Scope 
- Testa entidades especifica e não controlos gerais

#### Tipos de Avaliação
##### Ativo
- *Usa tools* para *descobrir hosts e vulnerabilidades*
- *Disruptivo* de sistemas
##### Passivo
- Usa tools para *capturar trafego*
- *Observa logs e dumps*
- Impacto mínimo
##### Externo
- Foca em *coisas publicas* (IP's, Portos,  Firewalls, DNS)
- Encontra métodos para *evitar Firewalls*
##### Interno

##### Host-Based
- Foca em erros pequenos (má configurações, permissões, falta de Updates)
- Erros podem ser *explorados por infiltrados* ou alguém que *ganhe acesso ao sistema*
##### Network
- Foca nas ligações da infraestrutura de comunicações
- Encontra Informação que pode ser privada
##### Application
- Foca numa *aplicação ou serviço*
- *Bugs e Flaws*
##### Wireless
- Foca na *ligações wireless* da infraestrutura
- Igual a Network mas com tools de autenticação


#### Ciclo de vida de gestão de vulnerabilidade
- **Baseline** O que vamos corrigir e o que não vamos corrigir, as mais perigosas,  as que podem ter remendo e o que pode ser ignorado por agora
- **Assessment** Construir relatório com as vulnerabilidades descobertas, zonas afetadas e como as afeta, que recomendações a oferecer para quem vai resolver **Métodos**: [[#Aplicação]] **Estratégias**:[[#Blackbox]], [[#Whitebox]] , [[#Graybox]]
- **Risk Assessment** Acessar o risco de cada vul
- **Remediation** Empresa tenta implementar os métodos de correções propostos
- **Verificação**-Verificar que a remediação funciona
- **Monitorização**- Detectar a vulnerabilidades não resolvidas estão a ser exploradas

##### Aplicação
**Estática**- Vai ver o código e tenta identificar as vulnerabilidades.
**Dinâmica**- Interage com a aplicação, tenta um username muito grande, ou sem pass etc.
Component Analysis- Wireshark,  