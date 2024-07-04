<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png"></a>
    <span>Bootcamp Nexa - Machine Learning para Iniciantes na AWS</span>
</h1>

# :computer: Desafio: Previsão de Estoque Inteligente na AWS com Sagemaker Canvas

Bem-vindo ao desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas. Neste Lab DIO, você aprenderá a usar o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). Siga os passos abaixo para completar o desafio!

## 🚀 Passo a Passo

### 1. Selecionar Dataset

-   Navegue até a pasta `datasets` deste repositório. Esta pasta contém os datasets que você poderá escolher para treinar e testar seu modelo de ML. Sinta-se à vontade para gerar/enriquecer seus próprios datasets, quanto mais você se engajar, mais relevante esse projeto será em seu portfólio.
-   Escolha o dataset que você usará para treinar seu modelo de previsão de estoque.
-   Faça o upload do dataset no SageMaker Canvas.

### 2. Construir/Treinar

-   No SageMaker Canvas, importe o dataset que você selecionou.
-   Configure as variáveis de entrada e saída de acordo com os dados.
-   Inicie o treinamento do modelo. Isso pode levar algum tempo, dependendo do tamanho do dataset.

### 3. Analisar

-   Após o treinamento, examine as métricas de performance do modelo.
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 4. Prever

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

# :bulb: Solução do desafio

## Problemas para executar o SageMaker

Para executar o SageMaker é necessário criar um Domínio, porém a Amazon não havia adicionado nenhuma cota para criação de domínio na minha conta.

![Resource_limit](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/5100972a-c569-4d87-8506-c60f906b48e4)

Foi necessário solicitar o aumento da cota e aguardar a resposta da Amazon:

![SolicitandoDomain](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/e2a733ce-941f-4075-acc3-da0baeca107f)



