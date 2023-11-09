# AAS
## Conceitos

### Supervised vs unsupervised
#### Supervised  
vs unsupervised learning - Quando a aprendizagem é supervisionada, os dados tem de estar etiquetados. 
#### Unsupervised learning
Dados não têm de estar etiquetados e é bom para lidar com dados brutos.  Ou só tens dados de entrada e não tens dados de saída

#### Tokenization
Transformação de uma string em uma lista de tokens

#### lemmatization
Transformação de palavras complexas na sua forma mais simples.
better → good
rock → Rocks

#### (TF)Term Frequency
Mensuração de quantas vezes um termo aparece em um texto

##### Word Clouds
Maneira de representar [[#Term Frequency]] em uma maneira gráfica

#### (TF-IDF) Term Frequency Inverse Document Frequency
- Termo que representa quão importante é um termo para um conjunto de documentos.
- Multiplicação do TF por o número de vezes que esse termo aparece em vários documentos.
- Assim se uma palavra aparecer em todos os documentos ela não é importante
## Spam
### Text mining
Deriving high-quality information  informations from text
Nenhum modelo tem accuracy de 100% pois os spammers estão sempre a explorar os limites do programa

### Blind optimization 

## Anomaly detection 
Técnica de descobrir padrões que não são conforme o comportamento esperado. Remoção de ruído e descoberta de novidades
### Tipos de anomalias
**Point anomalies** - Ponto de dados que está muito distante do resto 
**Contextual Anomalies** - Quando mandas vir 100 euros de comida todos os dias então passa a ser normal, mas se for uma vez só em separado por ser esquisito
**Collective anomalies** -  Quando já temos um padrão base do que é suposto ser uma anomalia e é comparada a novos dados.

### Gradient descent.
Maneira de  encontrar um mínimo  de uma função
### (SMV) Support Vector Machine-Based 
- Associado a [[#Unsupervised learning]] 
- Aprende um região baseada nos dados de treinamento e a partir deles, nos dados de teste, a partir dessa região identifica que os que estão dentro dessa região são dados normais e os que estão fora, são anomalias
### Clustering
Abordagem à detecção de anomalias agrupando objetos similares

- **Density-Based Methods:** Estes métodos consideram um cluster uma região com elevada densidade de dados. 
- Tem uma boa precisão e podem juntar clusters

- **Hierarchical Based Methods:** Os clusters formados são gerados de uma maneira ramificada. Novos clusters são criados a partir do criado anterior

- **Partitioning Methods:** Método que parte um cluster grande em vários diferentes, tenta maximizar  a diferença entre clusters.

#### K-Means
- [[#Unsupervised learning]] 
- Algoritmo de detecção de anomalias com base na distância euclidiana. Aqui tu especificas o número de cluster que os teus dados vão ter e o algoritmo auto-organiza os dados de forma a caberem nos grupos especificados. 
- Partition method
#### (BSS) Blind Signal Separation
- [[#Unsupervised learning]] ??
- Separação de sinais que são captados juntos, assim conseguido ver cada um deles separadamente.  E.g. Num ficheiro de audio com muitas pessoas a conversar, separar em vários audios com cada audio corresponder a uma pessoa a falar apenas.

##### (PCA) Principal component Analysis
Maneira de sumarizar a informação de grandes tabelas. Tenta encontrar padrões em grandes massas de dados

##### (ICA) Independent Component Analysis

### Density Based
Usa densidade de forma a perceber as anomalias,  os pontos que estão perto de areas densas são dados normais, e os que estão em áreas não densas são anomalias.


#### Isolation forest 
- [[#Unsupervised learning]]
- Baseia-se no facto de anomalias serem dados que são poucos e diferentes e logo  são suscetíveis a um mecanismo chamados de isolamento.
- Funcionam  melhor quando os dados são balanceados, tendo o mesmo número de bons/maus casos
- O número de condições para isolar anomalias é mais baixo que para isolar dados normais
- Cria árvores de isolação e é dado um score de isolação com base quão longe se foi para isolar aquele dado
#### (LOF) Local Outlier Factor
- [[#Unsupervised learning]]
- Computa o desvio de densidade local para cada ponto, para com respeito com os vizinhos, anomalias são os pontos com um score muito mais baixo que os vizinhos


pergunta 10 
tipos de clustering e porque cada um é bom 
PCA vs ICA