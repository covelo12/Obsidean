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

##### Autenticação
-  Determina  a identidade de um utilizador
- Baseia-se em verificar uma propriedade da pessoa que se quer autenticar(o que ele é, tem , ou sabe)

##### HTTP
- HTTP Requests *não têm estado* tokens e cookies incluídos para manter um estado, *não se deve usar URL para estado* pois é visível e facilmente extraído por outros
-  HTTP protocolo genérico operado em TCP(port 80)
- Como não existe segurança no client-side o controlo tem de existir na parte do servidor
- Usa header de Autorização
###### Referer Header 
- Contém o address da pagina que está a fazer o request
- Deixa o server ver em que página da pessoa que está a aceder está
- User-controllable
###### Session ID
- Valor dado pelo Servidor
- URL's em HTTP tem o SSID
###### Cookies
