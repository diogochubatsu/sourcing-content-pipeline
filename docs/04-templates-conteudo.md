# 04 — Templates de Conteudo

## Visao Geral

Templates sao as "receitas" que transformam dados Bronze em artigos Silver. Cada template define estrutura, campos obrigatorios e formato de saida.

## Template 1: Ficha de Produto

**Replicabilidade:** Alta (1 produto = 1 artigo)
**Fontes Bronze:** 1688 (minimo)
**Volume possivel:** 200+ artigos

### Estrutura

```markdown
# {product_name} no 1688: Preco, MOQ e Como Importar (2026)

## Resumo Rapido
| Campo | Valor |
|---|---|
| Preco 1688 | RMB {price} (~USD {price_usd}) |
| MOQ | {moq} unidades |
| Fornecedor | {supplier_name} |
| Rating | {rating}/5 |
| Categoria | {category} |

## Preco no 1688
{price_analysis}

## Quanto Custa Importar?
| Custo | Valor |
|---|---|
| Produto | USD {product_cost} |
| Frete estimado | USD {shipping} |
| Tarifa | {tariff}% |
| Agente | {agent_fee}% |
| **Total** | **USD {total}** |

## Onde Vender?
| Plataforma | Preco | Margem |
|---|---|---|
| Amazon US | USD {amazon_price} | {amazon_margin}% |
| Mercado Livre | BRL {ml_price} | {ml_margin}% |

## Fornecedores Similares
{similar_suppliers_table}
```

## Template 2: Comparacao 1688 vs Alibaba

**Replicabilidade:** Media (1 categoria = 1 artigo)
**Fontes Bronze:** 1688 + Alibaba
**Volume possivel:** 50-100 artigos

### Estrutura

```markdown
# {category}: 1688 vs Alibaba — Precos Reais de {month} 2026

## Resumo
O 1688 e em media {gap_percent}% mais barato que o Alibaba para {category}.

## Comparacao por Produto

| Produto | 1688 | Alibaba | Gap |
|---|---|---|---|
{comparison_rows}

## Analise do Gap

### Por que o 1688 e mais barato?
{price_reasons}

### Custos Ocultos do 1688
{hidden_costs}

### Quando o Alibaba e Melhor?
{alibaba_wins}

## Recomendacao
{recommendation}
```

## Template 3: Comparacao 1688 vs Amazon

**Replicabilidade:** Alta (1 produto = 1 artigo)
**Fontes Bronze:** 1688 + Amazon
**Volume possivel:** 100+ artigos

### Estrutura

```markdown
# {product_name}: 1688 vs Amazon — Quanto Voce Economiza?

## O Produto
{product_description}

## Precos

| Fonte | Preco | Moeda |
|---|---|---|
| 1688 | {price_1688} | CNY |
| Amazon US | {price_amazon} | USD |
| Amazon BR | {price_amazon_br} | BRL |

## Calculo de Margem

| Custo | Valor |
|---|---|
| Produto no 1688 | USD {cost_1688} |
| Frete + Tarifa | USD {shipping_tariff} |
| Agente | USD {agent_fee} |
| **Custo Total** | **USD {total_cost}** |
| **Preco de Venda** | **USD {sale_price}** |
| **Margem** | **{margin}%** |

## Links Diretos
- [1688]({link_1688})
- [Amazon]({link_amazon})
```

## Template 4: Ranking de Fornecedores

**Replicabilidade:** Media (1 categoria = 1 artigo)
**Fontes Bronze:** 1688 (multiplos fornecedores)
**Volume possivel:** 50-100 artigos

### Estrutura

```markdown
# Top 10 Fornecedores de {category} no 1688 (2026)

## Como Avaliamos
- Preco medio
- MOQ
- Rating do fornecedor
- Tempo de resposta
- Tempo no mercado

## Ranking

### 1. {supplier_1_name}
- Preco medio: RMB {price}
- MOQ: {moq}
- Rating: {rating}/5
- Endereco: {address}
- [Ver loja]({link})

### 2. {supplier_2_name}
...

## Dicas para Escolher
{tips}
```

## Template 5: Custo de Importacao

**Replicabilidade:** Media (1 categoria = 1 artigo)
**Fontes Bronze:** 1688 + tabelas de frete
**Volume possivel:** 20-50 artigos

### Estrutura

```markdown
# Quanto Custa Importar {category} da China? Custos Reais 2026

## Preco Medio no 1688
{average_price}

## Cadeia de Custos

| Etapa | Custo | Percentual |
|---|---|---|
| Produto | {product_cost} | {pct}% |
| Frete maritimo | {sea_freight} | {pct}% |
| Frete aereo | {air_freight} | {pct}% |
| Tarifa de importacao | {tariff} | {pct}% |
| Agente de sourcing | {agent} | {pct}% |
| Impostos (ICMS, II, IPI) | {taxes} | {pct}% |
| **Total estimado** | **{total}** | **100%** |

## Exemplo Real
{real_example}

## Como Economizar
{tips}
```

## Template 6: Calculadora

**Replicabilidade:** Baixa (1 por categoria)
**Fontes Bronze:** 1688 + Amazon + tabelas
**Volume possivel:** 10-20 ferramentas

### Formato

```html
<!-- Ferramenta interativa -->
<h2>Calculadora de Importacao: {category}</h2>

<label>Preco no 1688 (RMB):</label>
<input type="number" id="price_1688">

<label>Quantidade:</label>
<input type="number" id="quantity">

<label>Peso unitario (kg):</label>
<input type="number" id="weight">

<button onclick="calculate()">Calcular</button>

<div id="result">
  <!-- Resultado gerado por JS -->
</div>
```

## Escalabilidade dos Templates

| Template | Produtos/Categorias | Artigos Possiveis |
|---|---|---|
| Ficha de Produto | 200 produtos | 200-400 |
| Comparacao 1688 vs Alibaba | 10 categorias | 20-40 |
| Comparacao 1688 vs Amazon | 100 produtos | 100-200 |
| Ranking de Fornecedores | 10 categorias | 10-20 |
| Custo de Importacao | 10 categorias | 10-20 |
| Calculadora | 10 categorias | 10-20 |
| **Total** | | **350-700** |
