# Experimento: Aumento da margem de contribuição em e-commerce varejista
<br><br>
## 🌐 Contexto e Motivação 
 
Em um cenário de alta concorrência no varejo online, onde as pressões por preços baixos são intensas e por vezes até inconsequentes, a busca por uma operação cada vez mais lucrativa se torna um objetivo constante e fundamental para a sobrevivência e expansão do negócio. Para empresas enquadradas no Simples Nacional, que favorece operações focadas em lucratividade, é crucial desenvolver estratégias de precificação que proporcionem uma vantagem competitiva através da busca constante do aumento da rentabilidade. 

Esse contexto é fundamental para entender a importância do experimento e seu impacto potencial nos resultados da empresa.

<br><br>
## 📋 Descrição

Este repositório contém um experimento realizado em um e-commerce varejista do Simples Nacional, avaliando o impacto de um aumento da margem de contribuição (usada na precificação dos produtos). O objetivo é entender como a alteração dessa margem pode influenciar o resultado financeiro da empresa.

**Pontos Relevantes:**

- **Contexto:** O experimento foi conduzido em um e-commerce varejista com um amplo mix de produtos e vários canais de venda.
- **Proteção de Dados:** Alguns valores foram ocultados ou substituídos por valores sintéticos para preservar informações sensíveis.
- **Margem Atual:** Todos os produtos utilizavam uma margem de contribuição de X% até o início do experimento.
- **Controle de Variáveis:** Não foram aplicadas ofertas ou promoções durante o período do teste.
- **Pré-Requisitos:** Conhecimentos em precificação, tributação e contabilidade são necessários para completa compreensão dos resultados.

**Definição de Termos:**

- **Simples Nacional:** Regime tributário onde a alíquota é aplicada sobre o faturamento total, favorecendo operações focadas em lucratividade.
- **Faturamento:** Valor total vendido, incluindo valores de produtos, fretes e despesas adicionais.
- **Margem de Contribuição:** Percentual usado para cálculo do preço de venda do produto, diferente de markup.
- **Resultado:** Para esse experimento foi considerado o valor do faturamento menos o custo dos produtos e despesas variáveis.

<br><br>
## 🎯 Objetivo

Avaliar o impacto no resultado da empresa de um aumento da margem de contribuição de X% para X+5%, utilizando uma lista de 1.052 produtos distintos, com diferentes valores e canais de venda (todos os produtos são vendidos em todos os canais de venda, sem exclusividade).

<br><br>
## 🧩 Hipóteses

- **Hipótese Nula (H0):** O aumento da margem de contribuição de X% para X+5% **NÃO** tem impacto positivo significativo no resultado final da empresa.
- **Hipótese Alternativa (H1):** O aumento da margem de contribuição de X% para X+5% **TEM** impacto positivo significativo no resultado final da empresa.

Por impacto positivo entende-se um aumento no valor monetário do resultado da empresa.

**Nível de significância:** 0,05 (5%)

<br><br>
## 🧪 Design do Experimento

### a) Divisão dos Produtos

- **Grupo de Controle (A):** 50% dos produtos vão utilizar a margem de contribuição original de X%.
- **Grupo de Tratamento (B):** 50% dos produtos vão utilizar a margem de contribuição aumentada para X+5%.

A divisão foi realizada aleatoriamente com um script em Python, garantindo uma separação sem vieses. As listas de produtos foram salvas em Excel, sendo utilizadas na precificação e análise posterior dos resultados.

### b) Período de Análise

O experimento foi conduzido por 30 dias para ambos os grupos simultaneamente, com objetivo de minimizar o efeito das variações de oferta e demanda nas vendas.

<br><br>
## 📊 Métrica de Avaliação

A métrica utilizada foi o valor monetário no resultado final de ambos os grupos. Comparar os resultados entre o grupo de controle (X%) e o grupo de tratamento (X+5%) permitirá entender o impacto direto da alteração da margem de contribuição no resultado final da empresa.

<br><br>
## 🚀 Execução e Coleta dos Dados

- **Fonte de Dados:** A coleta dos dados de produtos e vendas foi realizada através da API do Bling ERP (Oauth 2.0) onde todas as informações da operação da empresa estão concentradas.

- **Processamento:** Para apuração do resultado, foram deduzidos os custos de venda de cada produto de acordo com seus respectivos canais de venda. Para cada canal de venda os custos são:
  - Custo de frete grátis em R$.
  - Taxas de venda em R$
  - Comissão de venda em %.
  - Custo de embalagem em %.
  - Impostos em %.
  
  Obs: A alíquota do Simples Nacional é comum para todos os canais de venda.

- **Desafios (ETL, Precificação e Apuração):** Para sucesso do experimento, foi necessário criar soluções para lidar com uma série de situações não suportadas nativamente pelo Bling ERP:

  - A API do Bling ERP disponibiliza os valores das vendas e os produtos vendidos através de caminhos diferentes.
 
  - A API do Bling ERP disponibiliza o custo dos produtos vendidos através de caminho diferente das vendas.

  - A API do Bling ERP só disponibiliza as informações dos produtos no formato em que foram vendidos, por exemplo, kits não tem a sua composição detalhada.

  -	A API do Bling ERP disponibiliza as composições de kits por um caminho diferente do cadastro dos produtos.

  - O Bling ERP não apura o valor de venda proporcional de cada produto (no caso de kits).

  -	O Bling ERP não apura o lucro de cada venda com precisão, pois não suporta o cadastro e vinculação de todos os custos possíveis para cada produto e canal de venda.

  -	O Bling ERP somente disponibiliza a precificação de produtos através de markup. Para uma correta precificação dos produtos com todas as variáveis envolvidas, foi criado um script em Python à parte.

Obs: Os scripts em Python (1-ETL, 2-Precificação e 3-Apuração) que lidam com todos esses desafios, não serão apresentados neste experimento pois são considerados uma vantagem competitiva da empresa.

<br><br>
## 📈 Análise dos Resultados

O Resultado final apurado para as vendas de cada grupo foram os seguintes:

- **Grupo A (margem de X%):** Lucro Total = R$ 987,00. Lucro Médio por Produto = R$ 1,88. Desvio Padrão = R$ 1,08.
- **Grupo B (margem de X+5%):** Lucro Total = R$ 1.183,00. Lucro Médio por Produto = R$ 2,25. Desvio Padrão = R$ 1,27.

Para avaliar se os resultados são estatisticamente significantes foi utilizado o Teste T.

**Teste T:**
- **Estatística t:** -5.138
- **Valor p:** 3.322e-07

O valor-p é menor que o nível de significância (0.05), o que indica que há uma diferença significativa no resultado entre os dois grupos.

**Conclusão** : Rejeitamos a hipótese nula (H0). Há evidências suficientes para concluir que o resultado do Grupo de tratamento (margem de contribuição X+5%) é significante maior que o resultado do Grupo de controle (margem de contribuição X%).

**Conclusões dicionais sobre os Resultados** :

#### Variabilidade dos Resultados

O desvio padrão do resultado por produto no Grupo B (**R$ 1,27**) foi ligeiramente superior ao do Grupo A (**R$ 1,08**). Isso indica uma variação um pouco maior nos resultados individuais dos produtos que receberam a nova margem (Grupo B), o que pode ser comum quando se altera uma variável como a margem de precificação. No entanto, apesar dessa maior dispersão, o aumento observado na média de resultado do Grupo B foi substancial o suficiente para que a diferença se mostrasse estatisticamente significante, superando o efeito da variabilidade.

#### Impacto Prático: Intervalo de Confiança para a Diferença

Para além da significância estatística, é importante quantificar a magnitude provável do efeito da nova margem no mundo real. Para isso, podemos estimar um intervalo de confiança de 95% para a verdadeira diferença no resultado médio por produto entre os grupos (µʙ - µᴀ):

1.  **Diferença observada nas médias (X̄ʙ - X̄ᴀ):**
    R$ 2,25 - R$ 1,88 = **R$ 0,37**

2.  **Erro Padrão da Diferença (SE_diff):**
    Este valor é derivado da estatística t e dos dados amostrais. Usando a sua estatística t:
    SE_diff = |Diferença Observada / Estatística t|
    SE_diff = R$ 0,37 / 5.138 ≈ **R$ 0,072**

3.  **Cálculo do Intervalo de Confiança de 95%:**
    Para amostras grandes (como N ≈ 526 por grupo), podemos usar o multiplicador z de aproximadamente 1.96.
    Intervalo = Diferença Observada ± (Multiplicador z * SE_diff)
    Intervalo = R$ 0,37 ± (1.96 * R$ 0,072)
    Intervalo = R$ 0,37 ± R$ 0,14112

4.  **Intervalo de Confiança de 95% para (µʙ - µᴀ):**
    **[R$ 0,22888; R$ 0,51112]**

Arredondando para fins práticos (duas ou três casas decimais):
**IC 95%: [R$ 0,23; R$ 0,51]** ou **[R$ 0,229; R$ 0,511]**

**Interpretação do Intervalo de Confiança:**
Com 95% de confiança, podemos afirmar que o aumento da margem de contribuição de X% para X+5% leva a um aumento no resultado médio *por produto* que está entre **R$ 0,23 e R$ 0,51**, em comparação com a margem X%.

Crucialmente, este intervalo:
*   **Não inclui o valor zero:** Isso significa que é muito improvável que não haja diferença entre os grupos.
*   **Está inteiramente do lado positivo:** Isso indica que o efeito é um aumento no resultado.

Esses achados reforçam a conclusão de que o efeito da mudança na margem de contribuição não só é estatisticamente significativo, mas também representa um ganho prático e positivo para o resultado da empresa.

<br><br>
## ✅ Considerações Finais

Após confirmar que o aumento na margem de contribuição gerou um aumento significativo no resultado, a empresa passou a adotar essa nova margem para precificação padrão. Nos meses subsequentes foi observado que o resultado da empresa não recuou (empresas com um mix de produtos limitado ou com demanda altamente sensível ao preço, provavelmente não alcançarão resultados similares).

Posteriormente, um novo teste foi realizado com mais um aumento na margem de contribuição, onde novamente houve melhora no resultado da empresa. Esse fato levou a uma nova abordagem na precificação dos produtos, onde o objetivo foi trabalhar com margens de contribuição flutuantes, onde a margem era automaticamente ajustada (para cima ou para baixo) conforme o resultado gerado semanalmente.
