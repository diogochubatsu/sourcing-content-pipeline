# Template: Ficha de Produto

## Meta
- **Replicabilidade:** Alta (1 produto = 1 artigo)
- **Fontes Bronze:** 1688 (minimo)
- **Volume possivel:** 200+ artigos

## Estrutura do Artigo

```markdown
# {product_name} no 1688: Preco, MOQ e Como Importar (2026)

## Resumo Rapido

| Campo | Valor |
|---|---|
| Preco 1688 | RMB {price_1688} (~USD {price_usd}) |
| MOQ | {moq} unidades |
| Fornecedor | {supplier_name} |
| Rating | {supplier_rating}/5 |
| Categoria | {category} |

## Preco no 1688

O preco medio deste produto no 1688 e de **RMB {price_1688}** por unidade, o que equivale a aproximadamente **USD {price_usd}** na taxa de cambio atual.

### Faixa de Precos
- **Minimo:** RMB {price_min} (fornecedores com MOQ alto)
- **Maximo:** RMB {price_max} (fornecedores com MOQ baixo)
- **Medio:** RMB {price_1688}

## Quanto Custa Importar?

| Custo | Valor | Percentual |
|---|---|---|
| Produto no 1688 | USD {product_cost} | {pct_product}% |
| Frete maritimo (estimado) | USD {sea_freight} | {pct_sea}% |
| Frete aereo (estimado) | USD {air_freight} | {pct_air}% |
| Tarifa de importacao | {tariff}% | {pct_tariff}% |
| Custo do agente (5-8%) | USD {agent_fee} | {pct_agent}% |
| **Total estimado** | **USD {total}** | **100%** |

## Onde Vender e Quanto Lucrar?

| Plataforma | Preco de Venda | Custo Total | Margem |
|---|---|---|---|
| Amazon US | USD {amazon_us_price} | USD {total} | {margin_amazon_us}% |
| Amazon BR | BRL {amazon_br_price} | BRL {total_brl} | {margin_amazon_br}% |
| Mercado Livre | BRL {ml_price} | BRL {total_brl} | {margin_ml}% |
| Shopify (proprio) | USD {shopify_price} | USD {total} | {margin_shopify}% |

## Fornecedores Similares no 1688

| Fornecedor | Preco | MOQ | Rating | Endereco |
|---|---|---|---|---|
| {supplier_1} | RMB {price_1} | {moq_1} | {rating_1}/5 | {address_1} |
| {supplier_2} | RMB {price_2} | {moq_2} | {rating_2}/5 | {address_2} |
| {supplier_3} | RMB {price_3} | {moq_3} | {rating_3}/5 | {address_3} |

## Dicas para Importar

1. **Negocie o preco** — fornecedores no 1688 aceitam desconto para pedidos grandes
2. **Peca amostra** — sempre teste antes de comprar em volume
3. **Verifique o MOQ real** — o MOQ exibido pode ser menor que o real
4. **Use agente de sourcing** — facilita pagamento e consolidacao
5. **Calcule o custo total** — preco do produto e so uma parte

## Links Uteis

- [Ver no 1688]({link_1688})
- [Comparar com Alibaba]({link_alibaba})
- [Ver no Amazon]({link_amazon})
- [Calculadora de Importacao]({link_calculator})
```

## Variaveis Obrigatorias

| Variavel | Fonte | Obrigatorio? |
|---|---|---|
| product_name | Bronze | Sim |
| price_1688 | Bronze | Sim |
| moq | Bronze | Sim |
| supplier_name | Bronze | Sim |
| supplier_rating | Bronze | Sim |
| category | Bronze | Sim |
| price_usd | Calculado | Sim |
| product_cost | Calculado | Sim |
| sea_freight | Tabela | Sim |
| air_freight | Tabela | Sim |
| tariff | Tabela | Sim |
| agent_fee | Fixo (5-8%) | Sim |
| total | Calculado | Sim |
| amazon_us_price | Bronze (Amazon) | Nao |
| ml_price | Bronze (ML) | Nao |
| link_1688 | Bronze | Sim |
