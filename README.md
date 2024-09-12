# Experimento: Aumento da Margem de Contribuição em E-commerce Varejista


## 📋 Descrição

Este repositório contém um experimento realizado em um e-commerce varejista do Simples Nacional para avaliar o impacto de um aumento na margem de contribuição. O objetivo é entender como a alteração dessa margem pode influenciar o resultado financeiro da empresa.

**Pontos Relevantes:**

- **Contexto:** O experimento foi conduzido em um e-commerce varejista com um amplo mix de produtos e vários canais de venda.
- **Proteção de Dados:** Alguns valores foram ocultados ou substituídos por valores sintéticos para preservar informações sensíveis.
- **Margem Atual:** Todos os produtos utilizavam uma margem de contribuição de X% até o início do experimento.
- **Controle de Variáveis:** Não foram aplicadas ofertas ou promoções durante o período do teste.
- **Pré-Requisitos:** Conhecimentos em precificação, tributação e contabilidade são necessários para acompanhamento do experimento e completa compreensão dos resultados.

**Definição de Termos:**

- **Simples Nacional:** Regime tributário onde a alíquota é aplicada sobre o faturamento total, favorecendo operações focadas em lucratividade.
- **Faturamento:** Valor total vendido, incluindo valores de produtos, fretes e despesas adicionais.
- **Margem de Contribuição:** Percentual usado para cálculo do preço de venda do produto, diferente de markup.
- **Resultado:** Para esse experimento foi considerado o valor do faturamento menos o custo dos produtos e despesas variáveis.


## 🎯 Objetivo

Avaliar o impacto no resultado da empresa de um aumento da margem de contribuição de X% para X+5%, utilizando uma lista de 1.052 produtos distintos, com diferentes valores e canais de venda.


## 🧩 Hipóteses

- **Hipótese Nula (H0):** O aumento da margem de contribuição de X% para X+5% **NÃO** tem impacto positivo significativo no resultado final da empresa.
- **Hipótese Alternativa (H1):** O aumento da margem de contribuição de X% para X+5% **TEM** impacto positivo significativo no resultado final da empresa.

Por impacto positivo entende-se um aumento no valor monetário do resultado da empresa.

**Nível de significância:** 0,05 (5%)


## 🧪 Design do Experimento

### a) Divisão dos Produtos

- **Grupo de Controle (A):** 50% dos produtos mantêm a margem de contribuição original de X%.
- **Grupo de Tratamento (B):** 50% dos produtos terão a margem de contribuição aumentada para X+5%.

A divisão foi realizada aleatoriamente com um script Python, garantindo uma separação sem vieses. As listas de produtos foram salvas em Excel, sendo utilizadas na precificação e análise posterior dos resultados.

### b) Período de Análise

O experimento foi conduzido por 30 dias, comparando os efeitos entre os grupos e minimizando as variações de oferta e demanda.


## 📊 Métrica de Avaliação

A métrica utilizada foi o valor monetário no resultado final de ambos os grupos. Comparar os resultados entre o grupo de controle (X%) e o grupo de tratamento (X+5%) permitirá entender o impacto direto da alteração da margem de contribuição no resultado final da empresa.


## 🚀 Execução e Coleta dos Dados

- **Fonte de Dados:** A coleta dos dados de produtos e vendas foi realizada através da API do Bling ERP (Oauth 2.0) onde todas as informações da operação da empresa estão concentradas.

- **Processamento:** Para apuração do resultado foi deduzido os custos de venda de cada produto de seus respectivos canais de venda. Para cada canal de venda os custos são:
  - Custos de frete grátis.
  - Comissão de venda em %.
  - Taxa de venda em $.
  - Custo de embalagem em %. 

- **Desafios (ETL):** Para calcular o resultado de cada produto foi utilizado um script em Python para lidar com uma série de situações não suportadas nativamente pelo Bling ERP:

  - A API do Bling ERP disponibiliza os valores das vendas e os produtos vendidos através de caminhos diferentes.

  - A API do Bling ERP só disponibiliza as informações dos produtos no formato em que foram vendidos, por exemplo, kits não tem a sua composição detalhada.

  -	A API do Bling ERP disponibiliza as composições de kits por um caminho diferente das informações de venda.

  - O Bling ERP não apura o valor de venda proporcional de cada produto(no caso de kits) para cada canal de venda.

  -	O Bling ERP não apura o lucro de cada venda com precisão, pois não suporta o cadastro e vínculação de todos os custos possíveis para produto e canal de venda.

obs: O script em Python que lida com todos esses desafios não será apresentado nesse experimento, por ser considerado uma vantagem competitiva da empresa.


## 📈 Análise dos Resultados

O Resultado final para cada grupo foram os seguintes:

- **Grupo A (margem de X%):** R$ 987
- **Grupo B (margem de X+5%):** R$ 1.183

Para avaliar se os resultados são estatisticamente significantes foi utilizado o Teste T.
**Teste T:**
- **Estatística t:** -5.138
- **Valor p:** 3.322e-07

O valor-p é menor que o nível de significância (0.05), o que indica que há uma diferença significativa no resultado entre os dois grupos.

**Conclusão** : Rejeitamos a hipótese nula (H0). Há evidências suficientes para concluir que o resultado do Grupo de tratamento (margem de contribuição X+5%) é significante maior que o resultado do Grupo de controle (margem de contribuição X%).



## ✅ Considerações Finais

Após confirmar que o aumento na margem de contribuição gerou um aumento significativo no resultado, a empresa passou a adotar essa nova margem de contribuição para precificação padrão. Nos meses subsequentes foi observado que o resultado da empresa não recuou (empresas com um mix de produtos limitado ou com demanda altamente sensível ao preço, provavelmente não alcançarão resultados similares).

Um novo teste foi realizado com mais um aumento na margem de contribuição, onde novamente houve melhora no resultado da empresa. Esse fato levou a uma nova abordagem na precificação dos produtos, onde o objetivo foi trabalhar com margens de contribuição flutuantes, onde a margem era automaticamente ajustada (para cima ou para baixo) conforme o resultado gerado semanalmente.
