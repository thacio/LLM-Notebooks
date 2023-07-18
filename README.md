# Large Language Models Notebooks

Repositório com alguns notebooks de modelos de linguagem

| Notebook                        | Colab                                                                                                                       |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| benchmark-LM.ipynb              | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/thacio/LLM-Notebooks/blob/main/benchmark-LM.ipynb)             |
| Finetunning-LanguageModel.ipynb | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/thacio/LLM-Notebooks/blob/main/Finetunning-LanguageModel.ipynb) |


## Finetunning-LanguageModel.ipynb

Tutorial para fine-tune em dataset próprio, carregando de um dataframe do pandas obtido de um arquivo tsv. Suporta modelos decoder ou encoder-decoder.

## Benchmark-LM.ipynb

Notebook de benchmarks para modelos do tipo decoder, encoder-decoder e encoder com datasets em português.

Para os modelos decoder e encoder-decoder, é feito o fine-tune em diversos datasets ao mesmo tempo, com as métricas sendo calculadas individualmente para cada dataset. Assim, basta comentar ou descomentar o bloco com o dataset para considerá-lo ou não no benchmark.

Para os modelos encoder, só suporta um dataset por vez, então é necessário comentar as células dos datasets e deixar apenas uma descomentada.

Este notebook pode servir de base para finetunning em datasets próprios, é só seguir a estrutura da definição dos datasets.

### Benchmarks obtidos

#### Encoder-decoders e Decoders
Observação: Foram utilizadas as mesmas configurações para todos os modelos, com o fim de comparação do mesmo setup. Isso não implica dizer que algum dos modelos não possam obter melhores resultados com um melhor ajuste dos hiperparâmetros ou a mudança dos prompts.

|                                    |  Backbone + Embeddings = Total   Parameters | Assin2 STS Score Pearson &uarr; | Assin2 STS Score Mse &darr; | Assin2 Entail Acc &uarr; | Assin2 Entail F1 &uarr; | Cola Acc &uarr; | Cola Matthews Corr &uarr; | Mrpc Acc &uarr; | Rte Acc &uarr;  | Stsb Pearson &uarr; | Stsb Spearmanr &uarr; | Stsb Mse &darr; | Wnli Acc &uarr; | squad Acc &uarr; | squad F1 &uarr; |
|--------------------------------------|:-------------------------------------------:|:--------------------:|:----------------:|:-----------------:|:----------------:|:--------:|:------------------:|:--------:|:--------:|:------------:|:--------------:|:--------:|:--------:|:---------:|:--------:|
| ptt5-small-portuguese-vocab          |            44.1M + 16.4M = 60.5M            | 0.792753             | 0.547639         | 0.876225          | 0.87609          | 0.708533 | 0.184335           | 0.821078 | 0.67509  | 0.817776     | 0.813883       | 0.852606 | 0.478873 | 64.90066  | 75.90639 |
| ul2-pt-small sem prefixo             |            56.6M + 25.8M = 82.4M            | 0.81745              | 0.419042         | 0.88317           | 0.883074         | 0.688399 | 0.111816           | 0.806373 | 0.685921 | 0.852452     | 0.847828       | 0.641772 | 0.464789 | 65.38316  | 76.61703 |
| ul2-pt-small com prefixo   <\|NLU\|> |            56.6M + 25.8M = 82.4M            | 0.820127             | 0.439526         | 0.881944          | 0.881718         | 0.686481 | 0.15668            | 0.821078 | 0.689531 | 0.829919     | 0.830725       | 0.722225 | 0.464789 |     -     |     -    |
| ul2-pt-small com prefixo   <\|NLG\|> |            56.6M + 25.8M = 82.4M            | 0.813377             | 0.466839         | 0.883578          | 0.883539         | 0.691275 | 0.14724            | 0.806373 | 0.6787   | 0.837863     | 0.833992       | 0.683737 | 0.492958 |     -     |     -    |
| gpt2-small-portuguese                |            85.8M + 38.6M = 124.4M           | 0.783169             | 0.600997         | 0.872549          | 0.871974         | 0.69511  | 0.155226           | 0.813725 | 0.628159 | 0.8077       | 0.804051       | 0.790478 | 0.549296 | 51.12583  | 64.22844 |
| ptt5-base-portuguese-vocab           |           198.2M + 24.7M = 222.9M           | 0.823663             | 0.442637         | 0.895425          | 0.895156         | 0.725791 | 0.267567           | 0.852941 | 0.707581 | 0.851498     | 0.842867       | 0.649944 | 0.507042 | 71.3245   | 81.47399 |

<sup>1</sup> Dropout 0.1 para o SQUAD, sem dropout para o restante dos datasets.

&uarr; quanto maior, melhor a performance.

&darr; quanto menor, melhor a performance.

#### Encoders

|                            |  Backbone + Embeddings = Total   Parameters | Assin2 STS Score Pearson &uarr; | Assin2 STS Score Mse &darr; | Assin2 Entail Acc &uarr; | Assin2 Entail F1 &uarr; | Cola Acc &uarr; | Cola Matthews Corr &uarr; | Mrpc Acc &uarr; | Rte Acc &uarr;  | Stsb Pearson &uarr; | Stsb Spearmanr &uarr; | Stsb Mse &darr; | Wnli Acc &uarr; |
|--------------------------|:-------------------------------------------:|:--------------------:|:----------------:|:-----------------:|:----------------:|:--------:|:------------------:|:--------:|:--------:|:------------:|:--------------:|:--------:|:--------:|
| DeBERTina-base-32k-vocab |            85.5M + 24.6M = 110.0M           | 0.846492             | 0.39523          | 0.916667          | 0.916538         | 0.738255 | 0.351181           | 0.906863 | 0.765343 | 0.887879     | 0.885155       | 0.491599 | 0.56338  |
| BERTimbau-base           |            86.0M + 22.9M = 108.9M           | 0.842974             | 0.453757         | 0.89134           | 0.89093          | 0.736337 | 0.320599           | 0.872549 | 0.703971 | 0.881693     | 0.879315       | 0.510518 | 0.56338  |
| BERTimbau-large          |           303.9M + 30.5M = 334.4M           | 0.862311             | 0.359102         | 0.901961          | 0.901666         | 0.747843 | 0.350837           | 0.872549 | 0.754513 | 0.894086     | 0.892403       | 0.452587 | 0.56338  |
| mdeberta-base            |           85.5M + 192.8M = 278.2M           | 0.846274             | 0.386411         | 0.91299           | 0.91287          | 0.752637 | 0.373508           | 0.897059 | 0.761733 | 0.893377     | 0.890514       | 0.465971 | 0.56338  |

&uarr; quanto maior, melhor a performance.

&darr; quanto menor, melhor a performance.
