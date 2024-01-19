---
"Cadeira": "AEV"
Tags: "#Aula"
---
Links:
___ 
```dataview 
list 
from "Segurança/Vulnerabilidades" 
WHERE Cadeira = "AEV" and tags="#Conceito" and numero=4 sort file.cday
```

**Injeção**- Quando um user entra um comando com código de maneira a que o seu comando seja executado pelo servidor ou computadores de outros.

Como evitar: 
- *Não confiar em fontes externas*
- *Não misturar dados* e comandos
- *Sanitizar todos os dados*

O servidor deve ter todas as propriedades [[ACID]]

##### Tipos de SQLI
**In Band** - SQLI normal
**In Band -  Error Based** : Baseia-se num erro  enviado pelo server
**In Band - Union Based**: Explora a utilização do operador UNION
**Blind**: Baseado na mudança do resultado do servidor consoante a veracidade do Quarry SQL
**Blind- Time based**: Baseado no tempo que o servidor  demora a responder com um operador  WAITFOR
**Out of band**: Resultado extraído de outros canais