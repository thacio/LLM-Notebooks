# Large Language Models Notebooks

Repositório com alguns notebooks de modelos de linguagem

## Finetunning-LanguageModel

Tutorial para fine-tune em dataset próprio, carregando de um dataframe do pandas obtido de um arquivo tsv. Suporta modelos decoder ou encoder-decoder.

## Benchmark-LM

Notebook de benchmarks para modelos do tipo decoder e encoder-decoder com datasets em português.

É feito o fine-tune em diversos datasets ao mesmo tempo, com as métricas sendo calculadas individualmente para cada dataset. Assim, basta comentar ou descomentar o bloco com o dataset para considerá-lo ou não no benchmark.

Este notebook pode servir de base para finetunning em datasets próprios, é só seguir a estrutura da definição dos datasets.

### Benchmarks obtidos

Observação: Foram utilizadas as mesmas configurações para todos os modelos, com o fim de comparação do mesmo setup. Isso não implica dizer que algum dos modelos não possam obter melhores resultados com um melhor ajuste dos hiperparâmetros ou a mudança dos prompts.

|                             | Assin2 Score Pearson | Assin2 Score Mse | Assin2 Entail Acc | Assin2 Entail F1 | Cola Acc | Cola Matthews Corr | Mrpc Acc |  Rte Acc | Stsb Pearson | Stsb Spearmanr | Stsb Mse | Wnli Acc | squad Acc | squad F1 |
|-----------------------------|:--------------------:|:----------------:|:-----------------:|:----------------:|:--------:|:------------------:|:--------:|:--------:|:------------:|:--------------:|:--------:|:--------:|:---------:|:--------:|
| gpt2-small-portuguese       | 0.783169             | 0.600997         | 0.872549          | 0.871974         | 0.69511  | 0.155226           | 0.813725 | 0.628159 | 0.8077       | 0.804051       | 0.790478 | 0.549296 | 51.12583  | 64.22844 |
| ptt5-small-portuguese-vocab | 0.792753             | 0.547639         | 0.876225          | 0.87609          | 0.708533 | 0.184335           | 0.821078 | 0.67509  | 0.817776     | 0.813883       | 0.852606 | 0.478873 | 64.90066  | 75.90639 |
| ptt5-base-portuguese-vocab  | 0.823663             | 0.442637         | 0.895425          | 0.895156         | 0.725791 | 0.267567           | 0.852941 | 0.707581 | 0.851498     | 0.842867       | 0.649944 | 0.507042 | 71.3245   | 81.47399 |
| ult5-pt-small sem prefixo<sup>1</sup>    | 0.81745              | 0.419042         | 0.88317           | 0.883074         | 0.688399 | 0.111816           | 0.806373 | 0.685921 | 0.852452     | 0.847828       | 0.641772 | 0.464789 | 65.38316  | 76.61703 |
| ult5-pt-small NLU            | 0.820127             | 0.439526         | 0.881944          | 0.881718         | 0.686481 | 0.15668            | 0.821078 | 0.689531 | 0.829919     | 0.830725       | 0.722225 | 0.464789 |     -     |     -    |
| ult5-pt-small NLG            | 0.813377             | 0.466839         | 0.883578          | 0.883539         | 0.691275 | 0.14724            | 0.806373 | 0.6787   | 0.837863     | 0.833992       | 0.683737 | 0.492958 |     -     |     -    |

<sup>1</sup> Dropout 0.1 para o SQUAD, sem dropout para o restante dos datasets.
