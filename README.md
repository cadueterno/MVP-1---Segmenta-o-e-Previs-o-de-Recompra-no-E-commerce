# MVP-1---Segmenta-o-e-Previs-o-de-Recompra-no-E-commerce
Segmentação e Previsão de Recompra no E-commerce


# MVP de Machine Learning - Segmentação e Previsão de Recompra no E-commerce

## **Objetivo**
Este projeto tem como objetivo desenvolver um **MVP (Produto Mínimo Viável)** utilizando **Machine Learning**, abordando as etapas fundamentais do ciclo de ciência de dados:  
- Exploração e preparação de dados  
- Criação de features relevantes (engenharia de atributos)  
- Treinamento e avaliação de modelos de aprendizado de máquina  
- Comparação de algoritmos  
- Otimização de hiperparâmetros  
- Documentação e apresentação dos resultados  

O foco principal foi realizar a **segmentação de clientes** através de **clusterização** (KMeans) e criar um modelo supervisionado para **previsão de recompra em até 90 dias**, utilizando os dados transacionais de um e-commerce.

---

## **Dataset Utilizado**
O dataset utilizado foi o **Online Retail II**, disponível no repositório [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii).

**Descrição do dataset:**
- Dados transacionais de uma loja online do Reino Unido entre **2009 e 2011**.
- Informações incluem:
  - `InvoiceNo`: número da nota fiscal  
  - `StockCode`: código do produto  
  - `Description`: descrição do produto  
  - `Quantity`: quantidade de produtos comprados  
  - `InvoiceDate`: data e hora da transação  
  - `UnitPrice`: preço unitário  
  - `CustomerID`: identificador único do cliente  
  - `Country`: país do cliente  

Este dataset é ideal para problemas de:
- Segmentação de clientes (Clusterização)  
- Previsão de churn ou recompra (Classificação)  
- Análise de comportamento de consumo

---

## **Tecnologias Utilizadas**
As principais bibliotecas e ferramentas utilizadas foram:

| Tecnologia | Finalidade |
|------------|------------|
| **Python 3.10+** | Linguagem principal |
| **Google Colab** | Ambiente de execução |
| **Pandas** | Manipulação e limpeza dos dados |
| **NumPy** | Operações numéricas |
| **Scikit-learn** | Modelagem, métricas e pipelines |
| **Matplotlib / Seaborn** | Visualização dos dados |
| **Ucimlrepo** | Coleta automatizada do dataset do UCI |
| **Joblib** | Salvamento de modelos |

---

## **Etapas Desenvolvidas**
O projeto seguiu as melhores práticas de ciência de dados, com as seguintes etapas:

### **1. Carga e preparação dos dados**
- Leitura automática do dataset via `ucimlrepo`.  
- Limpeza:
  - Remoção de transações de cancelamento.  
  - Exclusão de registros com `CustomerID` ausente.  
  - Filtragem de quantidades negativas e preços iguais a zero.

### **2. Engenharia de Atributos (RFM)**
Criação das métricas **RFM (Recency, Frequency, Monetary)** para caracterizar clientes:
- **Recency:** dias desde a última compra.  
- **Frequency:** número de compras realizadas.  
- **Monetary:** total gasto pelo cliente.

### **3. Clusterização de Clientes**
- Algoritmo: **KMeans**.  
- Determinação do número ideal de clusters via **Silhouette Score**.  
- Interpretação dos clusters para estratégias de marketing e fidelização.

### **4. Criação da Tarefa Supervisionada**
- Construção de um target binário:
  - `1` → cliente realizou **nova compra em até 90 dias** após a última.  
  - `0` → cliente **não realizou recompra** no período.

- Divisão dos dados em **treino (70%)** e **teste (30%)**, garantindo separação temporal para evitar vazamento de dados.

### **5. Modelagem Supervisionada**
- **Baseline:** Logistic Regression.  
- **Modelo principal:** Random Forest Classifier.  
- **Otimização:** `RandomizedSearchCV` para ajuste de hiperparâmetros.  
- **Métricas utilizadas:**
  - Accuracy  
  - Precision  
  - Recall  
  - F1-score  
  - ROC AUC

### **6. Avaliação**
- Comparação entre modelos com matriz de confusão e curva ROC.  
- Verificação de **overfitting** analisando diferenças entre treino e teste.  
- Random Forest apresentou melhor equilíbrio entre precisão e recall.

---

## **Conclusões**
- A **clusterização RFM** permitiu identificar **grupos distintos de clientes**, possibilitando estratégias direcionadas de marketing.  
- O modelo supervisionado **Random Forest** obteve boa performance na **previsão de recompra**, sendo uma ferramenta viável para campanhas de retenção.  
- Possíveis melhorias futuras:
  - Incluir dados adicionais, como informações demográficas ou campanhas promocionais.  
  - Testar modelos mais avançados, como **XGBoost** ou **LightGBM**.  
  - Implementar validação cruzada com estratégia temporal para forecasting.  
  - Desenvolver uma API para integração do modelo em sistemas de recomendação em tempo real.

---

## **Autor**
**Carlos Eduardo Silva dos Santos**  
Projeto desenvolvido como entrega final da disciplina **Privacidade e Segurança Cibernética**, ministrada pelo Prof. Dr. André Serrano.
