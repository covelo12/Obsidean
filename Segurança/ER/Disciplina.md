1º projeto de Android- 20%
2º projeto de Aplicações -25%
3º projeto de Dispositivos- 25%
Exame final - 30%

D- 
P- Foremost & Binwalk 
# Definições
*Engenharia reversa* é o processo de extração de features e identificação de componentes e a sua correlação de algum produto feito por humanos e assim obter um representação do produto com um nível de abstração.
*Interatividade* é quanto os humanos são precisos para engenharia reversa
*Completude/completeness* nível de detalhe na abstração

# Níveis

- *Ao nível do sistema*- Observar as chamadas ao sistema (mudar, ler ficheiros etc.). 
- *Ao nível de Código*-Extrair conceitos de design a partir de binários

###### Reversão de software
- Um compilador pode converter em código máquina(executados no CPU) ou em bytecode (código executado por interpretador ou middleware)

# Files and filetypes
- Extensões ajudam humanos a perceber o tipo dos dados
- *File/magic headers* primeiros  3-5 bytes que PODEM corresponder a certos tipos de documentos
- Visualização direta pode ajudar
### Poliglotas
- *Poliglotas* são ficheiros que têm diferentes tipos simultaneamente que pode levar à  evasão de medidas anti-malware.
- *Stacks* quando o segundo ficheiro é mandado num segundo ficheiro.
- *Cavities* Extensões podem ter "lixo" e se 2 apps considerarem o código da outra lixo, podemos ter dois files no mesmo file.
- *Parasitas* Usa comentários e metadata 
- *Zippers* Comentários mútuos

# Magic Headers
| EXT | Magic Headers |
| ---- | ---- |
| ape | 4C 4F 43 55 53 |
| arm | 7F 45 4C 46 01 |
| avi | 52 49 46 46 86 |
| bmp | 42 4D 3A C7 2D |
| bsd | 7F 45 4C 46 02 |
| cmd | 4D 5A 90 00 03 |
| docx | 50 4B 03 04 14 |
| epub | 50 4B 03 04 0A |
| exe | 7B 22 70 61 79 |
| gbk | 4C 4F 43 55 53 |
| gif | 47 49 46 38 39 |
| gz | 1F 8B 08 08 6C |
| jcamp | 23 23 54 49 54 |
| jdx | 23 23 54 49 54 |
| jpg | FF D8 FF E0 00 |
| json | 5B 0A 20 20 20 |
| mp4 | 00 00 00 20 66 |
| odp | 50 4B 03 04 14 |
| pdf | 25 50 44 46 2D |
| png | 89 50 4E 47 0D |
| pps | D0 CF 11 E0 A1 |
| ppsx | 50 4B 03 04 14 |
| ppt | D0 CF 11 E0 A1 |
| pptx | 50 4B 03 04 14 |
| so | 7F 45 4C 46 02 |
| tif | 4D 4D 00 2A 00 |
| xyz | 20 20 20 32 35 |
