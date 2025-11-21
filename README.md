# 🧪 Classificação de Materiais em Plano Inclinado: Uma Abordagem de Machine Learning

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Wrangling-150458.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-orange.svg)
![Physics](https://img.shields.io/badge/Physics-Classical_Mechanics-black.svg)

## 📌 Sobre o Projeto

Este projeto foi desenvolvido como parte da disciplina de **Física 1 (Ciências Moleculares)** da Universidade de São Paulo (USP), ministrada pelo Prof. Dr. Caetano Miranda. O objetivo foi unir a **Mecânica Clássica** com **Ciência de Dados** para analisar o movimento de rolamento de cilindros em um plano inclinado.

Utilizamos dados experimentais coletados por diferentes grupos para treinar um modelo de **Machine Learning (Regressão Logística)** capaz de classificar se um cilindro é feito de **Aço** ou **Alumínio** com base apenas no tempo de descida e nas características físicas do experimento.

## ⚙️ O Problema Físico

Analisamos o rolamento de corpos rígidos sem deslizamento. Teoricamente, a aceleração de um cilindro descendo uma rampa depende da gravidade ($g$), do ângulo de inclinação ($\theta$) e do momento de inércia ($I$), conforme a equação derivada da conservação de energia:

$$v = \sqrt{\frac{2gh}{1 + \frac{I}{mR^2}}}$$

Embora a teoria ideal sugira que a massa não influencia a velocidade de descida para cilindros maciços idênticos geometricamente, fatores experimentais (atrito, resistência do ar, erro humano) criam variações nos dados que podem ser detectadas por algoritmos estatísticos.

---


## 🗂️ Pipeline de Dados

O projeto seguiu um fluxo de trabalho (pipeline) rigoroso de Ciência de Dados:

### 1. Coleta e Estruturação
Os dados foram coletados experimentalmente por 6 grupos diferentes, medindo:
- Massa, Diâmetro e Altura dos cilindros.
- Tempo de descida ($\Delta t$) cronometrado por múltiplos observadores.
- Geometria da rampa (comprimento $\Delta S$ e ângulo $\theta$).

### 2. Data Wrangling (Limpeza e Transformação)
Utilizando **Pandas**, os dados brutos passaram por diversas transformações:
- **Tratamento de Nulos:** Identificação de *missing values* usando mapas de calor (Heatmaps).
- **Tidy Data:** Transformação do dataset de formato "largo" (colunas por aluno) para formato "longo" (uma observação por linha) usando `pd.melt`.
- **Engenharia de Atributos:** Cálculo das velocidades médias experimentais.

## 📊 Análise de Resultados

### 1. Exploração dos Dados
A análise inicial revelou que a distinção entre os materiais não é trivial apenas olhando para os tempos brutos, devido à variância experimental entre os grupos.

![Boxplot dos Grupos](images/boxplot_variancia_grupos.png)
*Figura 1: Variabilidade das medições de tempo entre os diferentes alunosde um mesmo grupo de coleta.*

### 2. Performance do Modelo (Regressão Logística)
O modelo foi avaliado utilizando dados de teste (30% do dataset). Abaixo, a Matriz de Confusão ilustra os acertos e erros por classe:

![Matriz de Confusão](images/matriz_confusao.png)

**Métricas Detalhadas:**

| Classe | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: |
| **Aço (0)** | 0.64 | 0.58 | 0.61 |
| **Alumínio (1)** | 0.62 | 0.67 | 0.64 |
| **Acurácia Total** | | | **62%** |

> *Nota: A performance moderada (62%) no Grupo 1 reflete a presença de ruído nas medições manuais. Em grupos com coleta mais rigorosa (ex: Grupo 6), o mesmo pipeline atingiu >90% de acurácia, demonstrando a importância da qualidade dos dados na física experimental.*


