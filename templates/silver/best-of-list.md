# Template: Best Of List (Reviews/Analises)

## Meta
- **Replicabilidade:** Media (1 categoria = 1 artigo)
- **Fontes:** Reviews de Amazon, Reddit, YouTube, blogs
- **Volume possivel:** 100+ artigos
- **Vida util:** 6-12 meses

## Estrutura do Artigo

```markdown
# Os {number} Melhores {category} para Importar da China em {year}

## Resumo Rapido

| Posicao | Produto | Preco Medio | Melhor Para |
|---|---|---|---|
| 1 | {product_1} | {price_1} | {best_for_1} |
| 2 | {product_2} | {price_2} | {best_for_2} |
| ... | ... | ... | ... |

## Como Escolhemos

Analisamos:
- {total_reviews} reviews de compradores reais
- Precos em {total_platforms} plataformas
- Avaliacoes de {total_sources} fontes
- Dados de vendas e tendencias

## Ranking Completo

### 1. {product_1} — {tagline}

**Melhor para:** {best_for}
**Preco medio:** {price}
**Onde comprar:** {where_to_buy}

**Por que e o melhor:**
{reasoning}

**O que dizem os reviews:**
> "{review_quote_1}" — {reviewer_1}
> "{review_quote_2}" — {reviewer_2}

**Pontos fortes:**
- {pro_1}
- {pro_2}
- {pro_3}

**Pontos fracos:**
- {con_1}
- {con_2}

**Onde encontrar mais barato:**
| Plataforma | Preco | Link |
|---|---|---|
| 1688 | {price_1688} | {link_1688} |
| Amazon | {price_amazon} | {link_amazon} |
| AliExpress | {price_aliexpress} | {link_aliexpress} |

---

### 2. {product_2} — {tagline}

{repeat_structure}

---

{repeat_for_all_products}

## Comparativo Visual

| Produto | Qualidade | Preco | Facilidade de Importacao | Nota Geral |
|---|---|---|---|---|
| {product_1} | {quality_1}/5 | {price_1} | {ease_1}/5 | {overall_1}/5 |
| {product_2} | {quality_2}/5 | {price_2} | {ease_2}/5 | {overall_2}/5 |
| ... | ... | ... | ... | ... |

## Dicas para Importar {category}

1. **{tip_1}**
2. **{tip_2}**
3. **{tip_3}**
4. **{tip_4}**
5. **{tip_5}**

## Perguntas Frequentes

### {faq_1}
{answer_1}

### {faq_2}
{answer_2}

### {faq_3}
{answer_3}

## Conclusao

{conclusion}

---
*Atualizado em {date}. Baseado em {total_reviews} reviews e {total_sources} fontes.*
```

## Variaveis Obrigatorias

| Variavel | Fonte | Obrigatorio? |
|---|---|---|
| category | Fixo | Sim |
| number | Fixo (10, 15, 20) | Sim |
| year | Atual | Sim |
| products (lista) | Curadoria | Sim |
| reviews (por produto) | Amazon, Reddit | Sim |
| prices (por produto) | Multi-fonte | Sim |
| tips (lista) | Editorial | Sim |
| faqs (lista) | Editorial | Sim |

## Fontes de Reviews

| Fonte | Tipo | Confiabilidade |
|---|---|---|
| Amazon Reviews | Reviews verificados | Alta |
| Reddit | Discussoes comunitarias | Media-Alta |
| YouTube | Reviews em video | Media |
| Blogs de nicho | Analises especializadas | Variavel |
| AliExpress Reviews | Reviews de compradores | Media |
