# 🎼 Projeto de Machine Learning: Previsão de Popularidade no Spotify

![GitHub repo size](https://img.shields.io/github/repo-size/GabrieldPeder/MachineLearning?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/GabrieldPeder/MachineLearning?style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/GabrieldPeder/MachineLearning?style=for-the-badge)

Um projeto de [GabrieldPeder](https://github.com/GabrieldPeder)

## 📜 Sobre o Projeto

Este repositório contém um projeto completo de Machine Learning cujo objetivo é prever se uma música alcançará alta popularidade no Spotify. Utilizando um dataset com diversas características sonoras e metadados, o modelo foi treinado para classificar músicas como "Populares" ou "Não Populares".

O projeto aborda um ciclo completo de Data Science, desde a análise exploratória dos dados até a otimização de hiperparâmetros, tratamento de dados desbalanceados e a serialização do modelo final.

## 🎯 Índice

* [Fonte dos Dados](#-fonte-dos-dados)
* [Metodologia Aplicada](#-metodologia-aplicada)
* [Resultados do Modelo Final](#-resultados-do-modelo-final)
* [Tecnologias Utilizadas](#-tecnologias-utilizadas)
* [Como Executar o Projeto](#-como-executar-o-projeto)
* [Conclusão e Próximos Passos](#-conclusão-e-próximos-passos)
* [Autor](#-autor)

## 📦 Fonte dos Dados

Os dados foram obtidos de um dataset público contendo informações de milhares de músicas do Spotify, extraídas via API da plataforma. As principais features incluem:

* **Características Sonoras:** `danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`.
* **Metadados:** Nome da música, artista, duração, gênero, entre outros.
* **Variável Alvo:** `popularity`, uma pontuação de 0 a 100, que foi transformada em uma classificação binária para este projeto.

## ⚙️ Metodologia Aplicada

O projeto foi estruturado nas seguintes etapas:

1.  **Análise Exploratória de Dados (EDA):** Investigação inicial para entender a distribuição dos dados, correlações entre as features e identificar os artistas e gêneros mais populares.

2.  **Pré-Processamento:** Limpeza de dados nulos e duplicados. A variável `popularity` foi convertida em uma classe binária (`is_popular`), onde músicas com popularidade `> 70` foram consideradas "Populares" (1) e as demais "Não Populares" (0).

3.  **Tratamento de Dados Desbalanceados:** Foi identificado um forte desbalanceamento de classes. Para corrigir isso, duas técnicas de reamostragem foram comparadas:
    * **Oversampling com SMOTE:** Criação de dados sintéticos para a classe minoritária.
    * **Undersampling Aleatório:** Redução de amostras da classe majoritária.
    O SMOTE apresentou um melhor balanço de performance e foi escolhido para o modelo final.

4.  **Modelagem e Otimização:** Um modelo `RandomForestClassifier` foi selecionado. A ferramenta `GridSearchCV` foi utilizada para realizar uma busca exaustiva pelos melhores hiperparâmetros, otimizando o modelo para a métrica `F1-score`.

5.  **Avaliação Final:** O pipeline final, contendo o SMOTE, o `StandardScaler` e o modelo otimizado, foi avaliado no conjunto de teste (dados nunca vistos antes) para validar sua performance real.

## 📊 Resultados do Modelo Final

O modelo final, treinado com a técnica de oversampling (SMOTE) e com os hiperparâmetros otimizados, alcançou o seguinte desempenho no conjunto de teste:

| Classe        | Precision | Recall | F1-Score | Support |
|---------------|:---------:|:------:|:--------:|:-------:|
| Não Popular   |   0.98    |  0.89  |   0.93   |  5732   |
| Popular       |   0.31    |  0.72  |   0.43   |   453   |
| **Accuracy** |           |        | **0.88** |  **6185** |
| **Macro Avg** |   0.65    |  0.80  |   0.68   |  6185   |
| **Weighted Avg**|   0.93    |  0.88  |   0.89   |  6185   |

*O modelo demonstrou uma excelente capacidade de identificar corretamente as músicas populares (Recall de 72%), o que era o principal objetivo após o tratamento de desbalanceamento.*

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * Pandas & NumPy para manipulação de dados
    * Matplotlib & Seaborn para visualização
    * Scikit-learn para pré-processamento, modelagem e avaliação
    * Imbalanced-learn para técnicas de reamostragem
* **Ambiente:** Jupyter Notebook executado no VS Code

## 🚀 Como Executar o Projeto

Para executar este projeto localmente, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/GabrieldPeder/MachineLearning.git](https://github.com/GabrieldPeder/MachineLearning.git)
    cd MachineLearning
    ```

2.  **Crie um ambiente virtual (recomendado):**
    ```bash
    python -m venv .venv
    # Ative o ambiente
    # No Windows:
    .venv\Scripts\activate
    # No macOS/Linux:
    source .venv/bin/activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Execute o Notebook:**
    Abra o arquivo `.ipynb` no VS Code ou Jupyter e execute as células.

O modelo final treinado está salvo no arquivo `spotify_popularity_model.joblib` e pode ser carregado para fazer novas previsões.

## 🏁 Conclusão e Próximos Passos

O projeto demonstrou com sucesso a viabilidade de prever a popularidade de músicas utilizando dados de suas características. O tratamento do desbalanceamento de classes com SMOTE foi crucial para que o modelo aprendesse a identificar a classe minoritária (músicas populares) de forma eficaz.

**Melhorias Futuras:**
* Testar modelos mais avançados, como Gradient Boosting (XGBoost, LightGBM).
* Realizar engenharia de features mais complexa, utilizando dados textuais como nomes de artistas e títulos.
* Fazer o deploy do modelo como uma API web para realizar previsões em tempo real.

## 👤 Autor

**Gabriel de Peder**
