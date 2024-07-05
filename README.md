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

## Dataset

Utilizei o dataset: ```dataset-1000-com-preco-variavel-e-renovacao-estoque```. Esse dataset possui a ID do produto, preço, quantidade em estoque e data. 

Seguindo a sugestão do SageMaker Canvas, escolhi para substituir os valores faltantes de preço pela média e de estoque por 0.

![subs_valor](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/1b47497b-048f-432e-81fe-387a0eb9f360)

## Modelo

Selecionei como target a quantidade em estoque. Para o modelo o Time Series com predição para os próximos 3 dias.

![model_config](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/cd3cce54-2569-4a6d-8788-cd77b6c565b0)

Então executou-se o treino do modelo. 

![treino](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/92093796-b948-4e4e-8f85-b527d7e8073b)

## Analisar

Terminado o treino foram retornadas as métricas

![metrica](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/c7e710ad-3485-4092-a81e-857038049767)

### Weighted Quantile Loss (wQL)

Segundo o [guia do desenvolvedor](https://docs.aws.amazon.com/pt_br/forecast/latest/dg/metrics.html) do Amazon Forecast, a métrica Weighted Quantile Loss (wQL) mede a precisão de um modelo em um quantil especificado. É particularmente útil quando há custos diferentes de subprevisão e superprevisão.

- P10 (0.1): espera-se que o valor verdadeiro seja menor do que o valor previsto 10% do tempo.

- P50 (0.5): espera-se que o valor verdadeiro seja menor do que o valor previsto 50% do tempo. Isso também é conhecido como previsão mediana.

- P90 (0.9): espera-se que o valor verdadeiro seja menor do que o valor previsto 90% do tempo.

O preço possui quase 49% de influência na previsão. O SageMaker Canvas marcou a coluna preço como faltando valores futuros.

![missing_future_values](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/a15e646a-349c-4be4-8ae7-814ee8673110)

Isso indica que, caso os valores futuros de preço sejam fornecidos o modelo pode ter uma melhor performance. 

## Prever

São retornadas as curvas (de cima para baixo) P90, P50 e P10. 

![single_prediction_1](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/f967a04f-6a0c-4405-8dbe-8a353b07122f)

![single_prediction_2](https://github.com/tsdes-santiago/projetoDIOawsSagemakerCanvasEstoque/assets/139132478/384e733c-9f67-42eb-8fbc-ad91ed0fe484)

A curva P50, que está mais próxima da média, parece ser mais recomendata para previsão. Porém esse dataset é bem pequeno. Tendo apenas valores para 3 datas. Um dataset maior levaria a uma melhor performance do modelo.
