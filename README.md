Template
==============================

Template do CookieCutter

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>


# PROJETO EM REVISÃO: 
  - EM REVISÃO PARA AUMENTAR A LEGIBILIDADE / INTERPRETABILIDADE DO CÓDIGO
  - O CODIGO SERÁ MELHOR SEPARADO EM SUBTÓPICOS PARA EVITAR APLICAÇÃO DE TRANSFORMAÇÕES ANTES DA AMOSTRAGEM: LEAKAGE.

# Detecção de Fraudes em sistemas de pagamento online


# Projeto
- Detecção de fraudes - Classificação

# Repositório
- Notebook.ipynb - Notebook com EDA, limpeza, amostragem, balanceamento, pré-processamento, seleção de modelos, seleção de features, tunagem e métricas de modelos

# 1 Introdução e Data Source

Dados de transações de pagamentos, debitos, saques, depósitos e transferencias foram disponibilizados em um dataset no Kaggle. O dataset compõe dados de tipo de pagamento, saldo antes e após da transação da conta de origem e destino e rótulos de operações comuns (rótulo = 0) e fraudulentas (rótulo = 1)

https://www.kaggle.com/datasets/rupakroy/online-payments-fraud-detection-dataset

Os dados são naturalmente desbalanceados, o número de transações fraudulentas registrados corresponde à apenas 1.29% das transações. (8.213 transações fraudulentas e 6.354.407 transações comuns).

# 2 Objetivos

O objetivo desse projeto é criar um modelo que seja capaz de identificar corretamente transações fraudulentas para que, dessa forma, as instituições financeiras possam  impedir que a transação seja realizada e bloqueá-los como medida de segurança.

Obter um modelo com alta revocação e alta precisão para classificação de transações fraudulentas, portanto, é fundamental.

# Em andamento: Construção arquitetura (Kafka - streaming de dados) para consumo do modelo simulando uma transação real.

# 3 Metodologia

- Análise Exploratória: Uma analise exploratória dos dados foi conduzida no próprio notebook para traçar o perfil das transações fraudulentas.
- Pré-Processamento: OneHotEncoding no tipo de transação, Normalização em dados numéricos
- Amostragem: Realizado uma amostragem com dados de 20% fraudes e 80% transações comuns
- Taxa de balanceamento e seleção de modelo: Conduzido experimentos com diversos modelos para definir a melhor taxa de balanceamento para identificar as transações fraudulentas e selecionar o modelo a partir da performance dos modelos testados.
- Seleção de features: com o modelo selecionado, analizou-se a correlação da variável entre si e com a variável alvo e foi conduzido experimentos com o modelo para definir o melhor conjunto de features
- Tunning
- Avaliação do modelo: Avaliado performance sobre dados de testes e sobre todo o conjunto de dados para verificar se o modelo é capaz de aprender todos os exemplos mesmo após a amostragem e o rebalanceamento de classes

# Resultados
  
  O modelo RandomForest eleito como preditor e apresenta as seguinte performance nos dados de teste:
  
  Revocação classe 1 - Fraudes: 99,07%  
  Revocação classe 0 - Transações comuns: 98,13%  
  Acurácia:  98,50%  
  AUC:  0,9860  

O modelo apresenta as seguinte performance sobre a totalidade dos dados:
  
  Revocação classe 1 - Fraudes: 99,71%  
  Revocação classe 0 - Transações comuns: 98,77%  
  Acurácia:  98,97%  
  AUC:  0,9925  


# Stack
Numpy, Pandas, Scikit-Learn, Matplotlib
