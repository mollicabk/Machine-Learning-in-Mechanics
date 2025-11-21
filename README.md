# 🧪 Classificação de Materiais em Plano Inclinado: Uma Abordagem de Machine Learning

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Wrangling-150458.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-orange.svg)
![Physics](https://img.shields.io/badge/Physics-Classical_Mechanics-black.svg)

## 📌 Sobre o Projeto

Este projeto foi desenvolvido como parte da disciplina de **Física 1 (Ciências Moleculares)** da Universidade de São Paulo (USP). O objetivo foi unir a **Mecânica Clássica** com **Ciência de Dados** para analisar o movimento de rolamento de cilindros em um plano inclinado.

Utilizamos dados experimentais coletados por diferentes grupos para treinar um modelo de **Machine Learning (Regressão Logística)** capaz de classificar se um cilindro é feito de **Aço** ou **Alumínio** com base apenas no tempo de descida e nas características físicas do experimento.

## ⚙️ O Problema Físico

Analisamos o rolamento de corpos rígidos sem deslizamento. Teoricamente, a aceleração de um cilindro descendo uma rampa depende da gravidade ($g$), do ângulo de inclinação ($\theta$) e do momento de inércia ($I$), conforme a equação derivada da conservação de energia:

$$v = \sqrt{\frac{2gh}{1 + \frac{I}{mR^2}}}$$

Embora a teoria ideal sugira que a massa não influencia a velocidade de descida para cilindros maciços idênticos geometricamente, fatores experimentais (atrito, resistência do ar, erro humano) criam variações nos dados que podem ser detectadas por algoritmos estatísticos.

## 🗂️ Coleta e Processamento de Dados (Data Wrangling)

Os dados foram coletados manualmente utilizando cronômetros, balanças e paquímetros, e posteriormente processados utilizando **Python** e **Pandas**.

### Etapas do Pipeline:
1.  **Coleta:** Medição de massa, diâmetro, altura, ângulo da rampa e tempo de descida ($\Delta t$).
2.  **Limpeza:** Tratamento de valores nulos (`NaNs`) provenientes de diferentes grupos de medição.
3.  **Transformação:** Utilização da função `pd.melt` para transformar o dataset de formato *wide* para *long*, facilitando a visualização e modelagem (Tidy Data).
4.  **Engenharia de Atributos:** Cálculo de velocidades médias baseadas no deslocamento ($\Delta S$).

*Snippet de código da transformação:*
```python
# Transformando colunas de alunos em linhas para análise
df_melted = df.melt(
    id_vars=["Medida", "Grupo", "Material"],
    value_vars=["Aluno 1", "Aluno 2", "Aluno 3"],
    var_name="Aluno",
    value_name="Tempo"
)
