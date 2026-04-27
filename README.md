# Simple Credit Analysis

Projeto de analise de credito com dados publicos do LendingClub. O objetivo e explorar o dataset, treinar modelos simples de classificacao e avaliar a capacidade de identificar emprestimos que nao foram pagos integralmente.

## Visao geral

O arquivo principal e o notebook `credit_notebook.ipynb`. Ele usa dados de emprestimos de 2007 a 2010 e trabalha com a variavel alvo `not.fully.paid`:

- `0`: emprestimo pago integralmente
- `1`: emprestimo nao pago integralmente

O problema e desbalanceado: a maioria dos registros pertence a classe 0. Por isso, a analise nao deve depender apenas da acuracia. O recall da classe 1 e uma metrica importante para entender se o modelo consegue identificar possiveis inadimplentes.

## Estrutura

```text
simple-credit-analysis/
|-- README.md
|-- pyproject.toml
|-- requirements.txt
|-- uv.lock
|-- credit_notebook.ipynb
`-- loan_data.csv
```

## Instalacao

Pre-requisitos:

- Python 3.14 ou superior
- `uv` ou `pip`

Com `uv`:

```bash
uv sync
```

Com `pip`:

```bash
pip install -r requirements.txt
```

## Execucao

Inicie o Jupyter:

```bash
jupyter notebook
```

ou:

```bash
jupyter lab
```

Depois, abra `credit_notebook.ipynb` e execute as celulas em ordem.

## Conteudo do notebook

O notebook esta organizado em:

1. Contexto do problema
2. Descricao do dataset
3. Carregamento e exploracao inicial
4. Analise exploratoria
5. Preparacao dos dados
6. Treinamento e avaliacao dos modelos
7. Conclusao e proximos passos

Os modelos avaliados sao:

- `DecisionTreeClassifier`
- `RandomForestClassifier`

## Resultados de referencia

| Modelo | Acuracia | Precision classe 1 | Recall classe 1 | F1-score classe 1 |
| --- | ---: | ---: | ---: | ---: |
| Decision Tree | 72% | 19% | 24% | 21% |
| Random Forest | 85% | 52% | 3% | 5% |

O Random Forest apresenta acuracia maior, mas recall muito baixo para a classe 1. Isso indica que o modelo tende a favorecer a classe majoritaria e deixa de identificar boa parte dos emprestimos nao pagos integralmente.

## Variaveis

| Variavel | Descricao |
| --- | --- |
| `credit.policy` | Indica se o cliente atende a politica de credito |
| `purpose` | Finalidade do emprestimo |
| `int.rate` | Taxa de juros |
| `installment` | Parcela mensal |
| `log.annual.inc` | Logaritmo da renda anual |
| `dti` | Razao divida/renda |
| `fico` | Score FICO |
| `days.with.cr.line` | Dias com linha de credito |
| `revol.bal` | Saldo rotativo |
| `revol.util` | Utilizacao do credito rotativo |
| `inq.last.6mths` | Consultas de credito nos ultimos 6 meses |
| `delinq.2yrs` | Inadimplencias nos ultimos 2 anos |
| `pub.rec` | Registros publicos depreciativos |
| `not.fully.paid` | Variavel alvo |

## Possiveis melhorias

- Tratar o desbalanceamento com `class_weight`, undersampling ou SMOTE.
- Criar variaveis derivadas, como razao entre parcela e renda.
- Ajustar hiperparametros com validacao cruzada estratificada.
- Usar metricas como ROC-AUC, Precision-Recall AUC e recall da classe 1.
- Comparar com modelos adicionais, como regressao logistica balanceada ou gradient boosting.

## Observacao

Este projeto tem finalidade educacional e nao deve ser usado como ferramenta real de decisao de credito sem validacao adicional.
