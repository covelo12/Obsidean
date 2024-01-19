---
"Cadeira": "AEV"
Tags: "#Aula"
---
Links:
___ 
```dataview 
list 
from "Segurança/Vulnerabilidades" 
WHERE Cadeira = "AEV" and tags="#Conceito" and numero=5 sort file.cday
```
##### Como evitar
*Sincronização de tokens*: Cada form dentro de um HTML tem um  *token diferente aleatório*, fazendo scripts não funcionarem.
*Cookie-to-header*: O servidor manda um cookie, e este cookie será utilizado no método get ( index/cookie)
*SameSite atribute:* Scripts externos não têm acesso ao cookie
*Double Cookie*: Um para identificar o user durante a sessão e outro que muda a cada request
*Same origin policy*: Website não pode ler a recursos que não venham do mesmo domínio

**CORS** - Maneira de usar recursos externos em cima de SOP
