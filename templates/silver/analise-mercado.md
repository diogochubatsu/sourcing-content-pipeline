# Template: Analise de Mercado

## Meta
- **Replicabilidade:** Media (1 categoria/regiao = 1 artigo)
- **Fontes:** Google Trends, dados de vendas, reviews, precos
- **Volume possivel:** 50+ artigos
- **Vida util:** 3-6 meses

## Estrutura do Artigo

```markdown
# {category}: Analise de Mercado {year} — Tendencias, Precos e Oportunidades

## Resumo Executivo

**Tendencia geral:** {trend_direction}
**Oportunidade principal:** {main_opportunity}
**Mercado-alvo:** {target_market}

## Tendencias de Busca

### Google Trends

| Termo | Volume | Tendencia | Oportunidade |
|---|---|---|---|
| {term_1} | {volume_1} | {trend_1} | {opp_1} |
| {term_2} | {volume_2} | {trend_2} | {opp_2} |
| {term_3} | {volume_3} | {trend_3} | {opp_3} |

### O Que Esta Em Alta

{trending_analysis}

### O Que Esta Caindo

{declining_analysis}

## Precos por Regiao

| Regiao | Preco Medio | Tendencia | Fonte |
|---|---|---|---|
| China (1688) | RMB {avg_cn} | {trend_cn} | Scraping |
| EUA (Amazon) | USD {avg_us} | {trend_us} | Scraping |
| Brasil (ML) | BRL {avg_br} | {trend_br} | Scraping |
| Japao (Rakuten) | JPY {avg_jp} | {trend_jp} | Scraping |
| Europa (AliExpress) | EUR {avg_eu} | {trend_eu} | Scraping |

## Top Produtos da Categoria

### Mais Vendidos

| # | Produto | Vendas Est. | Preco | Margem |
|---|---|---|---|---|
| 1 | {product_1} | {sales_1} | {price_1} | {margin_1}% |
| 2 | {product_2} | {sales_2} | {price_2} | {margin_2}% |
| ... | ... | ... | ... | ... |

### Maior Margem

| # | Produto | Preco 1688 | Preco Varejo | Margem |
|---|---|---|---|---|
| 1 | {product_high_1} | {cost_1} | {retail_1} | {margin_high_1}% |
| 2 | {product_high_2} | {cost_2} | {retail_2} | {margin_high_2}% |
| ... | ... | ... | ... | ... |

## Analise de Reviews

### Sentimento Geral

| Aspecto | Positivo | Neutro | Negativo |
|---|---|---|---|
| Qualidade | {pos_quality}% | {neu_quality}% | {neg_quality}% |
| Preco | {pos_price}% | {neu_price}% | {neg_price}% |
| Durabilidade | {pos_durability}% | {neu_durability}% | {neg_durability}% |

### Top Reclamacoes

1. {complaint_1} ({frequency_1})
2. {complaint_2} ({frequency_2})
3. {complaint_3} ({frequency_3})

### Top Elogios

1. {praise_1} ({frequency_1})
2. {praise_2} ({frequency_2})
3. {praise_3} ({frequency_3})

## Oportunidades de Importacao

### Produto 1: {opportunity_1}
- **Por que agora:** {reason}
- **Preco estimado:** {price}
- **Margem potencial:** {margin}
- **Risco:** {risk_level}

### Produto 2: {opportunity_2}
- **Por que agora:** {reason}
- **Preco estimado:** {price}
- **Margem potencial:** {margin}
- **Risco:** {risk_level}

### Produto 3: {opportunity_3}
- **Por que agora:** {reason}
- **Preco estimado:** {price}
- **Margem potencial:** {margin}
- **Risco:** {risk_level}

## Previsoes para o Proximo Trimestre

{predictions}

## Como Comecar

1. **Pesquise o produto** — use nossos dados de preco
2. **Peca amostra** — teste antes de comprar em volume
3. **Calcule a margem** — use nossa calculadora
4. **Escolha o fornecedor** — verifique ratings e MOQ
5. **Comece pequeno** — teste com 50-100 unidades

## Fontes dos Dados

- Precos: Scraping de {total_sources} fontes
- Reviews: {total_reviews} reviews analisados
- Tendencias: Google Trends (ultimos 12 meses)
- Vendas: Estimativas baseadas em BSR e dados publicos

---
*Analise atualizada em {date}. Dados coletados de {total_sources} fontes em {total_languages} idiomas.*
```

## Variaveis Obrigatorias

| Variavel | Fonte | Obrigatorio? |
|---|---|---|
| category | Fixo | Sim |
| year | Atual | Sim |
| trend_direction | Google Trends | Sim |
| main_opportunity | Analise | Sim |
| prices (multi-regiao) | Bronze | Sim |
| trending_analysis | Google Trends | Sim |
| products (top vendidos) | Bronze | Sim |
| reviews (sentimento) | Reviews | Sim |
| opportunities (3) | Analise | Sim |
