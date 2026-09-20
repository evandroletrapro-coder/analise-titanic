# Análise de Sobrevivência no Titanic

**Projeto Final — Curso de Análise de Dados**

Investigação de características associadas à sobrevivência dos passageiros do Titanic utilizando análise exploratória, visualização de dados e modelagem preditiva.

---

## 1. Objetivo

Este projeto tem como objetivo analisar os dados dos passageiros do Titanic para identificar características associadas à sobrevivência durante o naufrágio.

A pergunta central da análise é:

> **Quais características dos passageiros estavam associadas à sobrevivência e quais padrões podem ser identificados a partir dos dados disponíveis?**

A análise considera principalmente variáveis como sexo, idade, classe do passageiro, tarifa e composição familiar.

---

## 2. Base de dados

**Dataset:** Titanic

A base utilizada contém **891 registros de passageiros e 12 variáveis**.

Principais variáveis analisadas:

| Variável | Descrição |
|---|---|
| `Survived` | Indicador de sobrevivência |
| `Pclass` | Classe do passageiro |
| `Sex` | Sexo |
| `Age` | Idade |
| `SibSp` | Número de irmãos/cônjuges a bordo |
| `Parch` | Número de pais/filhos a bordo |
| `Fare` | Tarifa paga |
| `Cabin` | Número da cabine |
| `Embarked` | Porto de embarque |

---

## 3. Problema de análise

O projeto busca identificar padrões relacionados à sobrevivência dos passageiros.

Foram levantadas hipóteses relacionadas a:

- diferença nas taxas de sobrevivência entre homens e mulheres;
- diferença entre crianças e adultos;
- influência da classe do passageiro;
- relação entre tarifa e sobrevivência;
- possível influência da composição familiar.

O objetivo não é estabelecer causalidade, mas identificar **associações e padrões presentes na base de dados**.

---

## 4. Metodologia

O projeto foi desenvolvido seguindo as seguintes etapas:

```text
Exploração dos dados
        ↓
Avaliação da qualidade dos dados
        ↓
Tratamento dos valores ausentes
        ↓
Engenharia de variáveis
        ↓
Análise exploratória
        ↓
Visualização dos dados
        ↓
Análise estatística
        ↓
Modelagem preditiva
        ↓
Avaliação do modelo
        ↓
Interpretação dos resultados
```

### 4.1 Tratamento dos dados

Foram realizados:

- identificação de valores ausentes;
- preenchimento de `Age` utilizando a mediana;
- preenchimento de `Embarked` utilizando a moda;
- criação da variável `Child`, considerando passageiros com até 12 anos;
- criação da variável `FamilySize`;
- criação da variável `IsAlone`;
- análise da disponibilidade da informação de `Cabin`.

---

## 5. Análise exploratória

Foram realizadas análises de:

- taxa geral de sobrevivência;
- sobrevivência por sexo;
- sobrevivência por classe;
- sobrevivência entre crianças e adultos;
- distribuição das idades;
- distribuição das tarifas;
- identificação de possíveis outliers;
- correlação entre variáveis numéricas;
- relação entre sexo e classe;
- composição familiar.

### 5.1 Principais resultados

A taxa geral de sobrevivência foi de aproximadamente **38,38%**.

| Grupo | Taxa de sobrevivência |
|---|---:|
| Mulheres | 74,20% |
| Homens | 18,89% |

Por classe:

| Classe | Taxa de sobrevivência |
|---|---:|
| 1ª classe | 62,96% |
| 2ª classe | 47,28% |
| 3ª classe | 24,24% |

Entre passageiros com até 12 anos, a taxa observada foi de aproximadamente **57,97%**, enquanto entre os demais passageiros foi de aproximadamente **36,74%**.

Esses resultados representam associações observadas na amostra e não devem ser interpretados isoladamente como relações causais.

---

## 6. Análise da variável Fare

A variável `Fare` apresenta forte assimetria à direita e presença de possíveis valores extremos.

Foram utilizados histograma, boxplot e estatísticas descritivas.

A média da tarifa foi de aproximadamente **32,20**, enquanto a mediana foi de **14,45**.

Esse comportamento demonstra a importância de considerar a distribuição dos dados e medidas estatísticas mais robustas quando existem valores extremos.

---

## 7. Modelagem preditiva

Como etapa complementar à análise exploratória, foi utilizada **Regressão Logística** para classificação binária da variável `Survived`.

A base foi dividida em conjuntos de treinamento e teste para avaliar o desempenho do modelo em dados que não participaram diretamente do treinamento.

As principais métricas utilizadas foram:

- Acurácia;
- Precisão;
- Recall;
- F1-score;
- Matriz de confusão.

### 7.1 Resultados da avaliação inicial

| Métrica | Resultado |
|---|---:|
| Acurácia | 80,45% |
| Precisão | 75,76% |
| Recall | 72,46% |
| F1-score | 74,07% |

Matriz de confusão:

| | Predito: não sobreviveu | Predito: sobreviveu |
|---|---:|---:|
| **Real: não sobreviveu** | 94 | 16 |
| **Real: sobreviveu** | 19 | 50 |

> **Nota:** antes da versão final do projeto, o notebook será revisado para que o tratamento dos dados seja integrado ao processo de modelagem, reduzindo o risco de *data leakage*.

---

## 8. Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

## 9. Estrutura do projeto

```text
Projeto_Final_Analise_Titanic/
│
├── README.md
├── requirements.txt
│
├── data/
│   └── titanic.csv
│
├── notebooks/
│   └── analise_titanic.ipynb
│
└── reports/
    └── graficos/
```

### Descrição das pastas

**`data/`**  
Contém a base de dados utilizada no projeto.

**`notebooks/`**  
Contém o notebook com código, análises, visualizações e modelagem.

**`reports/`**  
Destinado aos gráficos e demais materiais produzidos como resultado do projeto.

**`requirements.txt`**  
Lista as principais bibliotecas necessárias para reproduzir a análise.

---

## 10. Limitações

- Existem valores ausentes em algumas variáveis.
- `Cabin` possui grande quantidade de informações ausentes.
- A base representa os registros disponíveis no dataset.
- Associações não devem ser interpretadas automaticamente como causalidade.
- O desempenho do modelo depende das variáveis utilizadas e da divisão entre treinamento e teste.

---

## 11. Possíveis aplicações

Embora o Titanic seja um dataset histórico, o projeto simula uma situação de análise em que dados de indivíduos são utilizados para identificar padrões associados a determinado resultado.

As técnicas utilizadas podem ser aplicadas em contextos como:

- análise de clientes;
- avaliação de risco;
- segmentação;
- previsão de eventos;
- identificação de padrões;
- apoio à tomada de decisões baseada em dados.

---

## 12. Aprendizados

O projeto permitiu consolidar conhecimentos relacionados a:

- exploração e compreensão de bases de dados;
- tratamento de valores ausentes;
- criação de variáveis;
- análise estatística descritiva;
- visualização de dados;
- interpretação de correlações;
- preparação de dados para modelos;
- classificação supervisionada;
- avaliação de modelos;
- comunicação de resultados.

O principal aprendizado foi perceber que análise de dados não consiste apenas em executar código, mas em **transformar dados em informações capazes de responder a um problema definido**.

---

## 13. Autor

**Evandro**

Projeto desenvolvido como parte do curso de Análise de Dados.
