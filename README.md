# LLM-Notebooks

Repositório com alguns notebooks de modelos de linguagem

## Benchmark-LM

Notebook de benchmarks para modelos do tipo decoder e encoder-decoder com datasets em português.

É feito o fine-tune em diversos datasets ao mesmo tempo, com as métricas sendo calculadas individualmente para cada dataset. Assim, basta comentar ou descomentar o bloco com o dataset para considerá-lo ou não no benchmark.

Este notebook pode servir de base para finetunning em datasets próprios, é só seguir a estrutura da definição dos datasets.

## Finetunning-LanguageModel

Tutorial para fine-tune em dataset próprio, carregando de um dataframe do pandas obtido de um arquivo tsv. Suporta modelos decoder (gpt2) ou encoder-decoder (t5).
