# Desenvolvendo um processo de ciência de dados no Orange Data Mining

Para minha graduação desenvolvi um projeto de ciência de dados com os seguintes objetivos:

- Exploração dos dados
- Escolha dos algoritmos de aprendizado para a modelagem (pelo menos 3 algoritmos)
- Preparação dos dados de acordo com as características dos algoritmos de aprendizado Escolhidos
- Execução dos experimentos de aprendizado e coleta das métricas

O conjunto de dados escolhidos compreende um dataset de diabetes, que é originário do 
National of Diabetes and Digestive and Kidney, disponível em: https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset e considerado o  padrão gold de dados.  O objetivo dos dados é prever diagnosticamente se o paciente tem diabetes, com base em medidas de diagnósticos incluídas no conjunto de dados. Todos os pacientes são mulheres com idade superior a 21 anos. 

Alguns conceitos foram levantados durante a exploração de dados: 
• Resultados: 500 com resultado de “não diabetes” e 268 com resultado de “diabetes” 
• Idade: 
o Média: 33,2 anos 
o Moda: 22 anos 
o Encontrado o valor máximo de 81 anos, podendo ser considerado um único outlier como apresentado pelo box plot

• Quantidade de vezes grávida: 
o Média: 3,8  
o Moda: 1 
o Máximo: 17 porém não consideraria outlier visto que é um valor muito próximo de demais  

• BMI (Body Mass Index):  
• O equivalente ao IMC aqui no Brasil, quanto maior o valor, maior a relação com sobrepeso e obesidade. 
• Média: 31 – considerado obesidade 
• Moda: 32 – considerado de obesidade 
• Máximo: 67.1

# Modelos utilizados e conclusões:

1. KNN 
 
A utilização do modelo K-Nearest Neighbors (KNN) foi uma escolha para a classificação de 
diabetes em mulheres devido à sua simplicidade e à falta de suposições sobre a distribuição 
dos dados. Ele classifica novos casos com base na proximidade aos K vizinhos mais próximos 
no conjunto de treinamento, o que é intuitivo e eficaz para detectar padrões não lineares.  
Também, optei devido a sua pré prepação de dados realizada através do sistema Orange. 

Conclusão: Considerando os dados não normalizados o modelo apresentou a consistência entre os 
valores de acurácia (0.7089 e 0.6942) está mostrando um desempenho relativamente estável 
em diferentes conjuntos de validação ou diferentes execuções. A acurácia média (em torno 
de 0.70) indica que o modelo tem um desempenho razoável, mas há espaço para melhorias. 
 
Considerados os dados normalizados a acurácia média dos valores fornecidos é bastante alta, 
especialmente o valor de 0.7876, que sugere que o modelo KNN(1) está alcançando um bom 
desempenho geral na maioria dos casos. 

 
2. Logistc Regression 
 
A regressão logística foi escolhida devido a eficácia para a classificação de diabetes devido à 
sua simplicidade e capacidade de fornecer probabilidades interpretáveis sobre a presença da 
doença. Ela assume uma relação linear entre as características e a probabilidade de uma 
classe, o que facilita a modelagem e a interpretação dos. A regressão logística também 
permite uma avaliação clara do desempenho por meio de métricas como acurácia – AUC. 

Conclusão: 
O modelo de Regressão Logística tem um desempenho robusto, com acurácia média alta e 
consistente na versão original, variando de 76.6% a 81.8%. A versão mais recente (Logistic 
Regression (1)) mostra uma acurácia máxima melhor (84.0%), mas com uma média um pouco 
menor e uma métrica de erro mais alta (0.4965). Apesar de a melhoria na acurácia máxima 
seja notável, a métrica de erro sugere que ainda há espaço para ajustes. No geral, ambos os 
modelos têm um desempenho competitivo, mas a versão (1) pode indicar que a acurácia foi 
aprimorada em alguns aspectos, enquanto o erro precisa ser melhorado. 
 
3. Tree 
 
As árvores de decisão são adequadas para a classificação de diabetes por sua capacidade de 
modelar relações complexas e não lineares de maneira visual e intuitiva, facilitando a 
interpretação dos critérios de decisão. Elas lidam bem com dados categóricos e contínuos, 
não exigem normalização dos dados e são robustas a outliers como os apresentados acima.  

Conclusão: 

Considerando os dados não normalizados o modelo de árvore de decisão apresenta uma 
acurácia média que varia entre 63% e 70% em diferentes execuções ou validações, com algum 
nível de consistência em torno de 70% em algumas validações. No entanto, o valor baixo de 
0.3486 em uma métrica de erro sugere que o modelo pode ter problemas de desempenho 
em aspectos específicos. Em comparação com outros modelos, a árvores de decisão não está 
performando tão bem. 
 
Considerando os dados normalizados a comparação entre os dois conjuntos de scores para o 
modelo de árvore de decisão mostra uma melhoria significativa na versão mais recente (Tree 
(1)). A acurácia aumentou de uma faixa de 63%-70% para 74.9%-78.8%, indicando um 
desempenho muito melhor e mais consistente. A métrica de erro também mostrou uma variação, mas a versão mais recente do modelo demonstra um avanço em termos de 
desempenho geral. 

# Para refletir

Optei por normalizar os dados visto que a logistic regression apresentou um número alto de 
falso negativo, levando em consideração o contexto dos dados, um falso negativo é muito 
mais prejudicial neste caso, imagine o seguinte cenário: paciente recebe o resultado de não 
ter diabetes, já considerando os dados vistos anteriormente que possui agravantes como 
sobrepeso e alto valor de insulina, quando olhamos para os casos que apresentaram falsos 
negativos, temos uma média de insulina de 77, considerando valores coletados em jejum o 
normal previsto é entre 5 a 29,0 µIU/mL. Sabendo as complicações da diabetes a médio e 
longo prazo um erro de 40,5% de pacientes apresentaria até mesmo a morte desses 
pacientes. 
