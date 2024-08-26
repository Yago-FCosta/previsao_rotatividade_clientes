# Previsão Rotatividade Clientes

## Descrição do Projeto
Neste projeto será criado um modelo que vai predizer a rotatividades de clientes de uma empresa de telecomunicações.

## Ferramentas e Bibliotecas Utilizadas
- Python: Linguagem principal utilizada para a análise.
- Pandas e Numpy: Biblioteca para manipulação e análise de dados.
- Sklearn: Biblioteca para construção de modelo de machine learning.
- Matplotlib.pyplot e Seaborn: Biblioteca para construção de gráficos
- google.colab: integração do colab a conta do google

## Tabela
Temos quatro conjuntos de dados para trabalhar neste projeto:

**DF Contract**
Este data frame contém as informações dos contratos, como início, final, pagamento, e cargas mensais e totais.
- customerID
- BeginDate
- EndDate
- Type
- PaperlessBilling
- PaymentMethod
- MonthlyCharges
- TotalCharges

**DF Internet**
Este data frame contém informações sobre os serviços de internet, como o tipo e demais opções para os clientes, como backup, proteção, suport, segurança, e streaming
- customerID
- InternetService
- OnlineSecurity
- OnlineBackup
- DeviceProtection
- TechSupport
- StreamingTV
- StreamingMovies

**DF Personal**
Esse é um conjunto de dados que tem informações pessoais dos clientes, como gênero, se possuem parceiros e dependentes, e se são SeniorCitizen.
- customerID
- gender	
- SeniorCitizen
- Partner	Dependents

**DF Phone**
Este é o conjunto que permite visualizar quais clientes possuem multiplas linhas.
- customerID
- MultipleLines

## Metodologia
**Pré Processamento**
- Importar as bibliotecas necessárias
- Carregar e visualizar os dados
- Dados ausentes
- Dados duplicados
- Agrupando dados em um único conjunto
- Adicionando a coluna que calcula o tempo de contrato até o encerramento
- Categorizando as colunas de charges e tempo de contrato
  
**Análises**
- Análises das colunas em relação ao encerrameto do contrato
- Análise das colunas em relação a data de de encerramento
- Análise Monthy Charges
- Matrix Correlação com contratos encerrados

**Preparação para aplicação de Modelos Machine Learning**
- Seleção de features e target
- Divisão entre conjuntos de treino e teste
- Padronização e escalabilidade de features

**Predição**
- Modelo Árvore de Decisão
- Modelo de Floresta Aleatória
- Modelo de Regressão Logística
- Avaliação dos modelos

## Resultados
Após tratar e limpar os dados fiz análises entre eles.
- Analisando os dados com base na coluna encerrado
  - Contratos month-to-month possuem maior índice de churn em relação aos demais;
  - O meio de pagamento eletronic checks possui mais churn que os demais;
  - Fiber optic é a internet que mais tem índice de churn;
  - Vemos um comportamento inversamente proporcional entre os contratos ativos e os encerrados quando separamos as cargas mensais e totais por faixas. Enquanto mensal, o número de churn sobe conforme a carga média mensal também sobe, e os contratos ativos diminuem.
  - O invesro ocorre pro totalcharges
- Analisando por data de EndDate:
  - O número de churn por data de encerramento é praticamente o mesmo;
  - O número de churn por contratos do tipo mensal levando em conta as datas de encerramento são os mesmos;
  - Para o pagamento de eletronic check, todas as datas de encerramento possuem mais ou menos os menos número de churn;
  - Fiber optic possui também prarticamente os mesmos números de churn;
  - Por faixas de cargas (mensais ou totais) não existem diferenças entre as datas de saídas;
  - Existe uma certa padronização entre o tempo de duração dos contratos e as datas de saídas.

- Além destas variáveis também analisei de forma mais específica o histograma de MonthlyCharges. Ele apresentoum comportamento anormal, onde podemos ver 3 "picos" ao longo do mesmo. Para ter uma melhor visualização do comportamento, fiz algumas comparações com yempo de contratos, as faixas de tempo de contrato e EndDate.
  - Percebi que o primeiro pico da esquerda para direita é aquele que possui o menor tempo de contrato, e o que a última data de churn é que tem maior influencia;
  - No segundo pico, também é preenchido por quem possui menos tempo de contato e que as datas de encerraento estão mais pareados;
  - Já o último pico é determinado pelas datas de encerramento mais longas, ou seja, a média de charge mensal aumenta conforme o tempo de contrato aumenta, sendo diretamente proporcionais nesse caso.

- E para finalizar montei uma correlação das variáveis numéricas com o churn, transformei todas as variáveis bidimensionais em 0 (não) e 1 (sim).
  - Pelo que recebemos ao final, foi que MonthlyCharges (0.193356), PaperlessBilling (0.191825) e SeniorCitizen (0.150889) são as que possuem mais correlação positiva e TechSupport (-0.164674), OnlineSecurity (-0.171226) e TotalCharges (-0.199484) as maiores correlações negativas.

- Fizemos todos os treinos e testes dos modelos Árvore de Decisão, Floresta Aleatória e Regressão Logpística. Todos apresentaram resultados satisfatórios quanto acurácia e AUC-ROC, ambas as métricas tiveram resultado acima de 0,81. Mas se formos analisar qual o melhor modelo, acredito que vamos usar o modelo de Floresta Aleatória, pois foi aquele que apresentou os melhores resultados dos teste em relação às métricas analisadas e comparando com os demais modelos.

## Aprendizados
- Análise de dados: interpretação e extração de insights valiosos a partir de grandes volumes de dados.
- Preparação do conjunto para aplicações em Machine Learning: separação do conjunto original em teste e treino, além da seleção das features e target do modelo.
- Funções: construção e aplicação de funções para simplificar o código.
- Regras de negócios: aplicação de regras de negócio para resolução de problemas.
- Aplicação de modelos de Machine Learning: aplicação, seleção de hiperparâmetros, teste e avalição do modelo.
- Documentação de projetos: elaboração de documentação clara e detalhada para garantir que o projeto seja compreensível e replicável.
- Utilização de bibliotecas e ferramentas: aplicação prática de diversas bibliotecas e ferramentas do ecossistema Python.
- Tomada de decisões baseadas em dados: uso de insights derivados da análise de dados para orientar decisões estratégicas.
