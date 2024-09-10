# Atividade 2 – Classificação de Texto

**Aluno**: Lucas Menezes Costa  
**Matrícula**: 202000066884
**Modelo**: https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment-latest
**Dataset**: https://www.kaggle.com/datasets/kazanova/sentiment140

## 1. Introdução

Esta atividade tem como objetivo treinar um modelo de classificação de texto usando um dataset de sentimentos extraído do Twitter. Utilizei o modelo pré-treinado `cardiffnlp/twitter-roberta-base-sentiment-latest` da Hugging Face e o dataset Sentiment140. O desafio foi ajustar o modelo pré-treinado, originalmente configurado para 3 classes, para realizar uma tarefa de classificação binária (2 classes).

## 2. Preparação do Ambiente

Para iniciar a atividade, configurei o ambiente no Google Colab, incluindo a montagem do Google Drive para acessar os arquivos necessários e a importação das bibliotecas essenciais, como `transformers`, `datasets`, `pandas`, entre outras.

## 3. Exploração e Pré-processamento do Dataset

### 3.1 Importação e Visualização do Dataset

O dataset Sentiment140 foi carregado e visualizado para entender sua estrutura. Ele contém informações como o texto do tweet, o usuário que postou, e o rótulo de sentimento (0 para negativo, 4 para positivo). Abaixo estão os atributos principais:

- **labels**: O rótulo de sentimento (0 = negativo, 4 = positivo).
- **text**: O texto do tweet.

Foram apresentados os primeiros registros do dataset e gráficos que mostram a distribuição dos rótulos e um boxplot para a distribuição dos tamanhos dos textos por classe.

### 3.2 Conversão dos Rótulos

O modelo pré-treinado foi originalmente configurado para 3 rótulos, enquanto o dataset possui rótulos binários (0 e 4). Portanto, os rótulos 4 foram convertidos para 1 para que o modelo pudesse ser treinado para uma tarefa de classificação binária.

### 3.3 Divisão do Dataset

O dataset foi dividido em conjuntos de treino, validação e teste. Para facilitar o processamento, selecionei 1% dos dados de cada conjunto para demonstração, mantendo a proporção original das classes.

## 4. Preparação do Dataset para o Modelo

### 4.1 Criação dos Datasets

Os dados foram convertidos para objetos `Dataset` do Hugging Face, que facilitam o manuseio e o treinamento do modelo.

### 4.2 Tokenização

O texto foi tokenizado utilizando o `AutoTokenizer` da Hugging Face, preparando os dados para serem processados pelo modelo pré-treinado.

### 4.3 Extração dos Hidden States

Os hidden states foram extraídos usando o modelo pré-treinado, onde a última camada oculta foi capturada para cada entrada do dataset.

## 5. Visualização dos Embeddings

Para visualizar a separação entre as classes após a tokenização e extração dos embeddings, utilizei o UMAP para reduzir os embeddings para duas dimensões. O gráfico resultante mostrou como as classes estavam distribuídas no espaço vetorial, facilitando a análise visual da separabilidade entre as classes.

## 6. Treinamento de um Classificador Simples

### 6.1 Regressão Logística

Um classificador de regressão logística foi treinado usando os embeddings gerados. A acurácia e o F1-score foram calculados, proporcionando uma linha de base para a performance do modelo.

### 6.2 Comparação com DummyClassifier

Para avaliar o desempenho do modelo de regressão logística, comparei seus resultados com os de um `DummyClassifier`, que serve como uma linha de base trivial.

### 6.3 Matriz de Confusão da Regressão Logística

## 7. Treinamento do Modelo Pré-treinado

### 7.1 Configuração e Treinamento

O modelo `cardiffnlp/twitter-roberta-base-sentiment-latest` foi ajustado para uma tarefa de classificação binária. A última camada de classificação foi redefinida para ter duas saídas. O treinamento foi realizado utilizando o `Trainer` da Hugging Face.

### 7.2 Avaliação e Resultados

Após o treinamento, o modelo foi avaliado usando o conjunto de validação. A matriz de confusão foi gerada, mostrando a precisão do modelo na classificação correta dos tweets.

## 8. Conclusão

A atividade demonstrou a eficácia do uso de modelos pré-treinados para tarefas de classificação de texto, mesmo quando o número de classes precisa ser ajustado. O processo de conversão dos rótulos e o treinamento da última camada do modelo foram cruciais para alcançar bons resultados. A visualização dos embeddings mostrou que as classes estavam bem separadas, e o modelo treinado apresentou bons resultados em termos de acurácia e F1-score.

## 9. Código e Repositório

Todo o código utilizado nesta atividade está disponível no repositório privado no GitHub, e também em um notebook do Colab:
[GitHub](https://github.com/lucasmenezesdev/PLN_2024_Classifica_Texto_Costa_Lucas)
[Google Colab](https://colab.research.google.com/drive/1vY_35BYbp34Y48LCqOMkRRK-Vi-nfFjW?usp=sharing)
