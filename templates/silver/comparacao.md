# Template: Comparacao 1688 vs Alibaba

## Meta
- **Replicabilidade:** Media (1 categoria = 1 artigo)
- **Fontes Bronze:** 1688 + Alibaba
- **Volume possivel:** 50-100 artigos

## Estrutura do Artigo

```markdown
# {category}: 1688 vs Alibaba — Precos Reais de {month} 2026

## Resumo

O 1688 e em media **{gap_percent}% mais barato** que o Alibaba para {category}.

| Metrica | 1688 | Alibaba | Gap |
|---|---|---|---|
| Preco medio | RMB {avg_1688} | USD {avg_alibaba} | {gap_percent}% |
| MOQ medio | {moq_1688} | {moq_alibaba} | — |
| Fornecedores verificados | {verified_1688} | {verified_alibaba} | — |

## Comparacao por Produto

| Produto | 1688 (RMB) | Alibaba (USD) | Gap | Mesmo Fabrica? |
|---|---|---|---|---|
| {product_1} | {price_1_1688} | {price_1_alibaba} | {gap_1}% | {same_1} |
| {product_2} | {price_2_1688} | {price_2_alibaba} | {gap_2}% | {same_2} |
| {product_3} | {price_3_1688} | {price_3_alibaba} | {gap_3}% | {same_3} |
| ... | ... | ... | ... | ... |
| **Media** | **{avg_1688}** | **{avg_alibaba}** | **{gap_percent}%** | — |

## Analise do Gap

### Por que o 1688 e mais barato?

1. **Precos em RMB, nao USD** — fornecedores convertem com margem de 5-10%
2. **Custos de exportacao embutidos no Alibaba** — listagem em ingles, documentacao, suporte
3. **MOQs diferentes** — 1688 aceita pedidos menores
4. **Mesmo fabrico, plataformas diferentes** — fabricas vendem direto no 1688 e por trading companies no Alibaba

### Custos Ocultos do 1688

| Custo | Valor | Impacto |
|---|---|---|
| Agente de sourcing | 5-10% do pedido | Reduz gap em 5-10% |
| Pagamento em RMB | 1-3% spread cambial | Reduz gap em 1-3% |
| Consolidacao | $30-80 por envio | Fixo, dilui com volume |
| Inspecao | $100-200 | Fixo, dilui com volume |
| **Gap real (liquido)** | **{real_gap}%** | **Ainda significativo** |

### Quando o Alibaba e Melhor?

| Cenario | Plataforma Recomendada |
|---|---|
| Primeiro pedido, teste pequeno | Alibaba |
| Pedido > 500 unidades | 1688 |
| Produto precisa de CE/FCC/UL | Alibaba |
| Customizacao complexa | Alibaba |
| Ja tem agente de confianca | 1688 |

## Como Verificar se e o Mesmo Fabrica

1. **Busca reversa de imagem** — fotos identicas = mesmo fabrica
2. **Nome do fornecedor** — mesmo nome chines, variacao em ingles no Alibaba
3. **Endereco** — quando listado, geralmente idêntico
4. **SKU** — fabricas usam mesmo SKU internamente

## Recomendacao

Para **{category}**, o 1688 vale a pena quando:
- Pedido > {min_order} unidades
- Ja tem agente de sourcing
- Produto e simples (sem certificacao)
- Margem > {min_margin}%

Para **{category}**, o Alibaba e melhor quando:
- Primeiro pedido
- Precisa de certificacao
- Customizacao complexa
- Volume < {max_alibaba_order} unidades

## Fontes dos Dados

- Precos 1688: Scraping em {date_1688}
- Precos Alibaba: Scraping em {date_alibaba}
- Taxa de cambio: {exchange_rate}
- Dados de {total_products} produtos comparados
```

## Variaveis Obrigatorias

| Variavel | Fonte | Obrigatorio? |
|---|---|---|
| category | Bronze | Sim |
| gap_percent | Calculado | Sim |
| products (lista) | Bronze | Sim |
| avg_1688 | Calculado | Sim |
| avg_alibaba | Calculado | Sim |
| real_gap | Calculado | Sim |
| min_order | Fixo | Sim |
| min_margin | Fixo | Sim |
| exchange_rate | API | Sim |
| total_products | Contagem | Sim |
