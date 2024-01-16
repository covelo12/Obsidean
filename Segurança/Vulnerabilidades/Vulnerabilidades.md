---
Cadeira: "AEV"
Tags: "#Aula"
---
# Conceitos
```dataview 
list 
FROM "Segurança/Vulnerabilidades"
WHERE Tags="#Conceito" AND Cadeira="AEV" and numero = 1 
```
##### CVE VS CWE VS CVSS
**CWE** é um tipo de vulnerabilidades enquanto o **CVE** é a aplicação do **CWE** a  um sistema numa dada versão num dado SO,  podemos dar uma classificação a cada um destes problemas para definir as **CVE** prioritárias, essa classificação chama-se **CVSS**
##### Tracking de Vulnerabilidades
O tracking de Vulnerabilidades pode ser feita *durante a produção* do software, sendo tratadas como bugs e *depois de ser lançado*.
O tracking público e comunidade dinâmica no tracking de vulnerabilidades ajudam: 
- *Focar a discussão* no mesmo problema (Uso de livrarias).
- *Defensores a testar* o seu sistema
- Atacantes em saber que *tipo de vulnerabilidade pode ser usada*
O tracking também pode ser: 
- Privado

##### Divulgação de Vulnerabilidades
- *Não divulgação* que pode levar a zero-day attacks.
- *Coordenada* Se quem a descobriu diz à empresa sobre a vulnerabilidade e depois esta pode ser corrigida
- *Total* Se quem descobriu publica a CVE sem informar a empresa o que leva a ela ter de ser corrigida rápido 