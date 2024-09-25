# Objetivo do Arquivo

Este arquivo foi criado para registrar todas as informações essenciais para o processo de precificação de produtos e posterior apuração dos resultados, utilizando a API do Bling ERP. Ele inclui parâmetros detalhados sobre os custos e cobranças aplicáveis em cada canal de venda para cada grupo de produtos.

## Descrição das Abas

- **LOJAS**: Contém o nome e o código das lojas no Bling ERP, para as quais os produtos serão precificados. O código será utilizado para requisitar e atualizar os preços dos produtos via API em cada canal de venda. As lojas registradas aqui serão replicadas automaticamente nas demais abas do arquivo.

- **GRUPO**: Lista os grupos de produtos cadastrados no Bling ERP. Como cada canal de venda pode aplicar diferentes custos de venda para cada grupo, esses dados serão replicados automaticamente nas abas pertinentes.

- **MARGEM GRUPO A**: Define a margem de contribuição padrão (X%) usada no experimento.

- **MARGEM GRUPO B**: Define a margem de contribuição ajustada (X+5%), incluindo o adicional percentual para o experimento.

- **COMISSÃO**: Indica a comissão de venda, expressa em %, que cada canal de venda cobra para cada grupo de produtos.

- **BARREIRA FRETE GRÁTIS**: Limite do preço de venda em R$ que determina se o produto irá oferecer frete grátis ao cliente. Produtos abaixo desse valor terão custos de taxas, enquanto produtos acima estarão sujeitos aos custos de frete grátis, conforme o peso do pedido.

- **TAXA ATÉ FRETE GRÁTIS**: Define o valor cobrado em R$ por alguns canais para pedidos que não atingem o preço de venda limite para oferecer frete grátis ao cliente final.

- **VALOR FRETE GRÁTIS**: Registra o custo de frete grátis para produtos que ultrapassam o limite mencionado. Cada canal de venda tem custos diferentes, baseados nas faixas de peso do pedido.

- **TAXA PEDIDO**: Valor em R$ cobrado por pedido, independente do valor da compra, aplicável em determinados canais de venda.

- **EMBALAGEM**: Especifica o custo de embalagem em %, para cada canal de venda, que pode variar conforme a estratégia da empresa para cada canal de venda.

- **IMPOSTO NA ENTRADA**: Percentual de impostos que geram direito a crédito (aplicável para empresas do Lucro Real). Esses valores são comuns para toda a empresa e não variam conforme o canal de venda. Para empresas do Simples Nacional essa aba pode ser ignorada.

- **IMPOSTO NA SAÍDA**: Percentual de impostos aplicados sobre o valor final da venda, comum a todos os canais. Para empresas do Simples Nacional, é utilizada uma alíquota única.

Este arquivo visa otimizar o processo de precificação e apuração do resultado, garantindo que todos os custos e parâmetros de venda estejam corretamente alocados para cada canal de venda. O arquivo também elaborado nessa estrutura para que seja de fácil manipulação e alteração, nos casos de atualização dos custos envolvidos.

## Exemplo de Cálculo para produto do GRUPO1 no CANAL_A com peso de 200g

### Preço de venda: R$ 100

#### Custos do Canal de Venda A:
- **Comissão (ABA 'COMISSÃO')**: 10% (canal de venda A cobra 10% de comissão sobre o valor de venda do produto)
  - Custo: R$ 100 * 10% = **R$ 10**

- **Valor limite para oferecer o Frete Grátis (ABA 'BARREIRA FRETE GRÁTIS ')**: R$ 79 (Como o preço de venda é R$ 100, haverá o custo do frete grátis e não da taxa)
  
- **Taxa Até Frete Grátis (ABA 'TAXA ATÉ FRETE GRÁTIS')**: R$ 5,50 (mas não será cobrada pois o preço de venda do produto ultrapassou o limite para frete grátis)

- **Valor do Frete Grátis (ABA 'VALOR FRETE GRÁTIS')**: R$ 18,95 (cobrado de acordo com o peso pois o preço de venda ultrapassou a barreira limite para frete grátis)
- Custo:  **R$ 18,95**
  
- **Taxa de Pedido (ABA 'TAXA PEDIDO')**: R$ 0 (esse canal de venda não tem custo por pedido)
  
- **Embalagem (ABA 'EMBALAGEM')**: 1,58% (custo de embalagem definido pela empresa)
  - Custo: R$ 100 * 1,58% = **R$ 1,58**
  
- **Imposto na Entrada (ABA 'IMPOSTO NA ENTRADA')**: 0% (Como empresa do Simples Nacional, não tem direito a crédito dos impostos)
  
- **Imposto na Saída (ABA 'IMPOSTO NA SAÍDA')**: 10% (Alíquota única aplicada sobre o valor final da operação)
  - Custo: R$ 100 * 10% = **R$ 10**

#### Total de Custos:
- **Comissão**: R$ 10
- **Taxa Até Frete Grátis**: R$ 0
- **Taxa de Pedido**: R$ 0
- **Embalagem**: R$ 1,58
- **Imposto na Entrada**:  -R$ 0
- **Imposto na Saída**: R$ 10

**Total de custos = R$ 10 + R$ 0 + R$ 0 + R$ 1,58 + R$ 0 + R$ 10 = R$ 21,58**

