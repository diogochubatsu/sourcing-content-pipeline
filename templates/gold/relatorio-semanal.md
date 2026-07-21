# Template: Relatorio Semanal de Tendencias

## Meta
- **Replicabilidade:** Semanal (1 por semana)
- **Fontes:** Bronze + Google Trends + analise manual
- **Preco:** $19-49/mes (assinatura)

## Estrutura do Relatorio

```markdown
# Relatorio Semanal: {category} — Semana de {date}

## Resumo Executivo

**Destaques da semana:**
- {highlight_1}
- {highlight_2}
- {highlight_3}

**Tendencia geral:** {trend_direction} ({trend_percent}% {trend_vs_last_week})

## Top 5 Oportunidades da Semana

### 1. {product_1}
- **Preco 1688:** RMB {price_1688} (~USD {price_usd})
- **Preco Amazon:** USD {amazon_price}
- **Margem estimada:** {margin}%
- **Por que agora:** {reason}
- **Link:** [{link_text}]({link})

### 2. {product_2}
...

### 3. {product_3}
...

### 4. {product_4}
...

### 5. {product_5}
...

## Alertas de Preco

### Produtos com queda de preco (>20%)

| Produto | Preco Antes | Preco Agora | Queda | Fonte |
|---|---|---|---|---|
| {product_a} | RMB {old_price} | RMB {new_price} | {drop}% | 1688 |
| {product_b} | RMB {old_price} | RMB {new_price} | {drop}% | Alibaba |

### Produtos com aumento de preco (>20%)

| Produto | Preco Antes | Preco Agora | Aumento | Fonte |
|---|---|---|---|---|
| {product_c} | RMB {old_price} | RMB {new_price} | {rise}% | 1688 |

## Tendencias de Busca (Google Trends)

| Termo | Volume | Tendencia | Oportunidade |
|---|---|---|---|
| {term_1} | {volume_1} | {trend_1} | {opp_1} |
| {term_2} | {volume_2} | {trend_2} | {opp_2} |
| {term_3} | {volume_3} | {trend_3} | {opp_3} |

## Dados por Regiao

| Regiao | Preco Medio | Tendencia | Nota |
|---|---|---|---|
| China (1688) | RMB {avg_cn} | {trend_cn} | — |
| EUA (Amazon) | USD {avg_us} | {trend_us} | — |
| Brasil (ML) | BRL {avg_br} | {trend_br} | — |
| Japao (Rakuten) | JPY {avg_jp} | {trend_jp} | — |

## Metricas do Bronze esta Semana

| Metrica | Valor |
|---|---|
| Produtos atualizados | {products_updated} |
| Fontes consultadas | {sources} |
| Idiomas cobertos | {languages} |
| Dados novos | {new_data_points} |

## Proxima Semana

- {outlook_1}
- {outlook_2}
- {outlook_3}

---
*Relatorio gerado automaticamente a partir do Bronze. Dados atualizados em {scraped_at}.*
*Assinantes premium recebem alertas em tempo real via email.*
```

## Variaveis Obrigatorias

| Variavel | Fonte | Obrigatorio? |
|---|---|---|
| category | Fixo | Sim |
| date | Atual | Sim |
| highlights (3) | Analise | Sim |
| trend_direction | Calculado | Sim |
| products (5) | Bronze (top margem) | Sim |
| price_drops | Bronze (comparacao temporal) | Sim |
| google_trends | API | Sim |
| regional_data | Bronze (multi-fonte) | Sim |
