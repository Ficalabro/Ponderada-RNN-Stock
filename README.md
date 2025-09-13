# 📊 Predição de Série Temporal com RNN - Kaggle Stock Market Dataset

Este projeto implementa uma **Rede Neural Recorrente (RNN)** para prever preços de fechamento de ações com base em dados históricos do Kaggle.

---

## 📂 Dataset

O dataset utilizado é o [Stock Market Dataset - Kaggle](https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset), que contém duas pastas: `stocks` e `etfs`.  

No notebook, foi utilizado o arquivo de uma ação específica (ex: `AAPL.csv`), que contém dados históricos de preço.

### 📋 Colunas

| Coluna      | Descrição |
|-------------|-----------|
| **Date**    | Data da negociação |
| **Open**    | Preço de abertura |
| **High**    | Preço máximo |
| **Low**     | Preço mínimo |
| **Close**   | Preço de fechamento |
| **Adj Close** | Preço ajustado (considerando dividendos e splits) |
| **Volume**  | Quantidade de ações negociadas |

Neste projeto, o alvo de predição foi a coluna **Close**.

---

## 🎯 Métrica de Avaliação

A métrica escolhida foi **RMSE (Root Mean Squared Error)**, pois:
- É adequada para problemas de regressão.
- Penaliza erros maiores de forma mais forte.
- É expressa na mesma escala do preço (US$), facilitando interpretação.

---

## 🧹 Pré-Processamento

- Conversão da coluna `Date` para datetime e ordenação crescente.
- Normalização do preço de fechamento com `MinMaxScaler`.
- Criação de janelas de **30 dias** para previsão do dia seguinte.
- Divisão em treino (80%) e teste (20%).

---

## 🧠 Modelo

O modelo utilizado foi uma **SimpleRNN** com:
- **128 unidades** e ativação `tanh`
- Camada de saída densa (`Dense(1)`)
- Função de perda: **MSE**
- Otimizador: **Adam**

Treinamento por **50 épocas** com `batch_size=32`.

---

## 📈 Resultados

- **RMSE Teste:** calculado ao final da execução e exibido no notebook.

O notebook gera um gráfico comparando valores reais e previstos **apenas para o conjunto de teste**, usando datas no eixo X e preço em dólares no eixo Y:

- Linha azul: valores reais  
- Linha laranja tracejada: valores previstos pelo modelo

Este gráfico permite avaliar a capacidade do modelo de seguir a tendência de preços no período de teste.

---
