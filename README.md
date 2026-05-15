# 🐋 Projeto Whale Watcher: Motor Big Data para High-Frequency Trading (HFT)

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Polars](https://img.shields.io/badge/Polars-Fast_Data_Processing-orange?logo=polars&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-Statistical_Analysis-8CACEA?logo=scipy&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Machine_Learning-Scikit_Learn-yellow?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Concluído-success)

## 📌 O Problema de Negócio
No mercado financeiro e de criptomoedas, investidores institucionais (conhecidos como "Baleias") têm o poder de impactar drasticamente o livro de ofertas (*Order Book*). Quando uma grande ordem de venda é executada a mercado, ela consome a liquidez e causa uma queda abrupta no preço do ativo, fenómeno conhecido como *Slippage*.

Este projeto atua como um **Motor de Deteção e Previsão**, ingerindo o histórico massivo de transações da Binance (nível milissegundo) para responder a duas perguntas centrais:
1. Existe uma correlação matemática real entre o volume vendido pelas baleias e a queda de preço no mesmo minuto?
2. Se detetarmos uma ordem de $5 Milhões, quanto o preço vai cair?

## 🚀 Arquitetura e Tecnologias Aplicadas

O pipeline foi desenhado para lidar com **Big Data**, substituindo abordagens tradicionais que esgotariam a Memória RAM, aplicando as seguintes técnicas:

* **Avaliação Lazy (*Lazy Evaluation*):** Ingestão de ficheiros CSV massivos através de planos de execução do **Polars**, processando milhões de linhas sem sobrecarregar a máquina.
* **Compressão Parquet:** Conversão do histórico bruto em ficheiros `.parquet` colunares, reduzindo drasticamente o tamanho em disco e acelerando a leitura analítica.
* **Análise Exploratória e Detecção de Outliers (EDA):** Auditoria da amostra através de estatística descritiva rigorosa (Média, Mediana, Amplitude e Desvio Padrão).
* **Auditoria de Forma e Distribuição:** Utilização de Histograma e Boxplot (`Seaborn`/`Matplotlib`) em conjunto com métricas de Assimetria (*Skewness*) e Curtose (*Kurtosis*) para validar matematicamente distribuições de cauda longa.
* **Estatística Não-Paramétrica:** Uso da **Correlação de Spearman** (`SciPy`) para provar o impacto direcional de ordens massivas, superando as limitações da correlação de Pearson em amostras com forte presença de *outliers*.
* **Machine Learning Preditivo:** Treino de um modelo de **Regressão Linear** (`Scikit-Learn`) avaliado via $R^2$ e MSE, para prever a variação financeira com base no volume despejado a mercado.

## 📈 Resultados e Impacto Estratégico

* **Isolamento de Outliers:** A análise de quartis provou matematicamente que a distribuição de volume não é normal. O motor analítico isolou com sucesso o comportamento institucional (Baleias/Outliers) do ruído de retalho (Sardinhas).
* **Validação de Impacto:** O modelo confirmou a correlação negativa e a dependência estatística entre o aumento súbito de volume de venda e o *slippage* de preço do par **BTC/USDT**.
* **Previsão em Tempo Real:** O modelo de Machine Learning treinado é capaz de emitir um alerta estimando o impacto em dólares de forma precisa no exato minuto em que a ordem é submetida, servindo como uma ferramenta quantitativa poderosa para mesas de operações e gestão de risco.

---
## 👨‍💻 Autor
**Matheus Santos Felipe** *Engenharia e Ciência de Dados*
