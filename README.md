# Simple Credit Analysis

Análise de Crédito usando Machine Learning para prever se mutuários pagarão seus empréstimos.

## 📋 Sobre o Projeto

Este projeto explora dados públicos do LendingClub.com para criar um modelo de classificação que ajuda a prever se um mutuário pagará o empréstimo integralmente ou não. O LendingClub conecta pessoas que precisam de dinheiro (mutuários) com investidores, e o objetivo é auxiliar investidores a tomarem decisões mais informadas.

**Dataset**: Dados de empréstimos de 2007-2010 do LendingClub

**Objetivo**: Classificar se o mutuário pagou o empréstimo na íntegra (`not.fully.paid`)

## 🚀 Instalação

### Pré-requisitos

- Python 3.14 ou superior
- Gerenciador de pacotes `uv` (recomendado) ou `pip`

### Configuração do Ambiente

```bash
# Clone o repositório
git clone <repository-url>
cd simple-credit-analysis

# Instale as dependências usando uv
uv sync

# Ou usando pip
pip install -r requirements.txt
```

### Dependências

- jupyter>=1.1.1
- matplotlib>=3.10.9
- numpy>=2.4.4
- pandas>=3.0.2
- scikit-learn>=1.8.0
- seaborn>=0.13.2

## 📁 Estrutura do Projeto

```
simple-credit-analysis/
├── README.md                 # Este arquivo
├── pyproject.toml           # Configuração do projeto e dependências
├── uv.lock                  # Lock file das dependências
├── credit_notebook.ipynb    # Notebook principal com análise e modelos
└── loan_data.csv            # Dataset de empréstimos
```

## 💻 Como Usar

### Executar o Notebook

```bash
# Inicie o Jupyter Notebook
jupyter notebook

# Ou JupyterLab
jupyter lab
```

Abra o arquivo `credit_notebook.ipynb` e execute as células sequencialmente.

## 📊 Conteúdo do Notebook

O notebook está organizado nas seguintes seções:

### 1. Introdução
- Contexto do LendingClub e objetivo do projeto
- Descrição dos dados (2007-2010)

### 2. Carregamento e Exploração dos Dados
- Importação de bibliotecas
- Carregamento do dataset `loan_data.csv`
- Análise inicial: tipos de dados, valores não nulos, estatísticas descritivas

### 3. Análise Exploratória (EDA)
- Distribuição do score FICO por política de crédito
- Distribuição do score FICO por status de pagamento
- Contagem de empréstimos por propósito e status de pagamento
- Relação entre score FICO e taxa de juros
- Análise de regressão linear entre FICO e taxa de juros

### 4. Preparação dos Dados
- One-hot encoding da variável categórica `purpose`
- Separação entre features (X) e target (y)
- Divisão treino/teste (70%/30%)

### 5. Modelos de Machine Learning

#### Decision Tree Classifier
- Treinamento com `random_state=101`
- Avaliação: precision, recall, f1-score
- Matriz de confusão

#### Random Forest Classifier
- Treinamento com `n_estimators=600` e `random_state=101`
- Avaliação: precision, recall, f1-score
- Matriz de confusão

### 6. Próximos Passos
O notebook inclui uma seção detalhada com sugestões para melhorar a performance dos modelos:
- Tratamento do desbalanceamento de classes (SMOTE, undersampling, class weights)
- Feature engineering (novas variáveis, transformações, interações)
- Normalização e padronização dos dados
- Seleção e redução de features
- Ajuste de hiperparâmetros (GridSearchCV, RandomizedSearchCV)
- Experimentação com outros algoritmos (XGBoost, LightGBM, Logistic Regression)
- Métricas de avaliação mais adequadas (ROC-AUC, Precision-Recall AUC)
- Análise de erros

## 📈 Resultados Principais

### Decision Tree
- Acurácia: 72%
- Precision (classe 1): 19%
- Recall (classe 1): 24%
- F1-score (classe 1): 21%

### Random Forest
- Acurácia: 85%
- Precision (classe 1): 52%
- Recall (classe 1): 3%
- F1-score (classe 1): 5%

**Observação**: A acurácia elevada do Random Forest é enganosa devido ao desbalanceamento das classes (~84% classe 0 vs ~16% classe 1). O modelo tem dificuldade em identificar corretamente mutuários que não pagarão o empréstimo.

## 🔧 Variáveis do Dataset

- `credit.policy`: Política de crédito do LendingClub (1=cumpre, 0=não cumpre)
- `purpose`: Propósito do empréstimo (categórica)
- `int.rate`: Taxa de juros
- `installment`: Parcela mensal
- `log.annual.inc`: Log da renda anual
- `dti`: Debt-to-income ratio
- `fico`: Score FICO de crédito
- `days.with.cr.line`: Dias com linha de crédito
- `revol.bal`: Saldo rotativo
- `revol.util`: Taxa de utilização do crédito rotativo
- `inq.last.6mths`: Consultas nos últimos 6 meses
- `delinq.2yrs`: Inadimplências nos últimos 2 anos
- `pub.rec`: Registros públicos
- `not.fully.paid`: Target (1=não pagou integralmente, 0=pagou)

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:
- Reportar bugs
- Sugerir novas features
- Enviar pull requests

## 📝 Licença

Este projeto é fornecido para fins educacionais.

## 👤 Autor

Desenvolvido como projeto de análise de crédito e machine learning.

---

**Nota**: Este é um projeto educacional para demonstrar técnicas de análise de dados e machine learning aplicadas ao domínio de crédito financeiro.
