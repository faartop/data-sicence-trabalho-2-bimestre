# README – Predição de Desempenho Acadêmico

Este projeto tem como objetivo desenvolver um pipeline completo de machine learning para prever o desempenho acadêmico de estudantes com base em variáveis comportamentais, socioeconômicas e contextuais. Ao longo do processo, foram aplicadas técnicas de pré-processamento, modelagem, tuning de hiperparâmetros e avaliação visual e estatística dos resultados.

---

## 1. Estrutura Geral do Projeto

O projeto segue o fluxo abaixo:

1. Tratamento de valores ausentes  
2. Codificação de variáveis categóricas  
3. Separação entre variáveis numéricas e categóricas  
4. Pré-processamento com ColumnTransformer  
5. Treinamento de modelos (Linear Regression e Random Forest)  
6. Otimização do Random Forest com GridSearchCV  
7. Análises de importância de variáveis  
8. Geração de gráficos de avaliação  
9. Criação de um pipeline final integrado para produção

---

## 2. Pré-processamento dos Dados

### Tratamento de nulos
As colunas:  
- Parental_Education_Level  
- Teacher_Quality  
- Distance_from_Home  

tiveram seus valores nulos preenchidos com a moda.

### Codificação de variáveis categóricas
Foi aplicado LabelEncoder individual para cada coluna do tipo object.  
Posteriormente, para o pipeline final, utilizou-se OneHotEncoder.

### Padronização
Variáveis numéricas foram padronizadas via StandardScaler.

### Divisão das features
As variáveis foram divididas em:
- categóricas
- numéricas
- variável-alvo: Exam_Score

---

## 3. Modelos Treinados

### Regressão Linear
Treinada com dados pré-processados.  
Métricas obtidas:  
- R² ≈ 0.746  
- MAE ≈ 0.656  
- RMSE ≈ 1.894

### Random Forest (padrão)
Métricas:  
- R² ≈ 0.672  
- MAE ≈ 1.073  
- RMSE ≈ 2.154

### Random Forest (GridSearchCV)

Busca pelos hiperparâmetros:

- n_estimators  
- max_depth  
- min_samples_split  
- min_samples_leaf

Melhor configuração encontrada:

```
{
  "n_estimators": 500,
  "max_depth": null,
  "min_samples_split": 2,
  "min_samples_leaf": 4
}
```

Resultados no teste:
- R² ≈ 0.687  
- MAE ≈ 1.05  
- RMSE ≈ 2.10

---

## 4. Importância das Variáveis

Tanto para Random Forest quanto para Regressão Linear, as variáveis mais relevantes foram:

1. Attendance  
2. Hours_Studied  
3. Previous_Scores  
4. Tutoring_Sessions

Categorias relacionadas a acesso a recursos, envolvimento dos pais e condições familiares também apresentaram impacto relevante.

---

## 5. Avaliação Visual

Foram gerados:

### Predito vs Real
Comparando:
- Regressão Linear
- Random Forest

### Distribuição dos Resíduos
Para ambos os modelos.

As análises mostraram que a Regressão Linear apresentou resíduos mais concentrados e previsões mais próximas da linha ideal.

---

## 6. Pipeline Final Integrado

Foi criado um Pipeline contendo:

- Pré-processamento (padronização + one-hot encoding)  
- Modelo RandomForestRegressor final

O modelo foi treinado com todos os dados disponíveis.

Métricas finais:
- R² ≈ 0.953  
- RMSE ≈ 0.816

Observação: valores muito altos indicam possível overfitting ou vazamento de dados.

---

## 7. Como Executar (Exemplo)

Execute o notebook `machine_learning.ipynb` por completo, seja etapa a etapa ou em sua totalidade de uma vez.

---

## 8. Requisitos

- Python 3.8+  
- Scikit-learn  
- Pandas  
- NumPy  
- Matplotlib
