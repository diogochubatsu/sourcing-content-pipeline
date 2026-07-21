# 03 — Pipeline de Dados

## Visao Geral

O pipeline transforma dados brutos de multiplas fontes em conteudo publicavel.

## Fase 1: Ingestao (Bronze)

### Agentes de Scraping

| Agente | Fonte | Frequencia | Dados |
|---|---|---|---|
| Agente 1688 | 1688.com | 6-12h | Preco, MOQ, fornecedor, rating |
| Agente Alibaba | Alibaba.com | 12h | Preco, MOQ, Gold Supplier |
| Agente Rakumart | Rakuten/Rakumart | 24h | Preco, fornecedor, avaliacao |
| Agente ML+Amazon | ML + Amazon | 6h | Preco, BSR, vendas |

### Formato de Saida

```json
{
  "product_name": "Capinha iPhone 16",
  "product_name_zh": "iPhone 16手机壳",
  "product_name_ja": "iPhone 16ケース",
  "prices": {
    "1688": {"price": 0.45, "currency": "CNY", "moq": 10},
    "alibaba": {"price": 0.08, "currency": "USD", "moq": 100},
    "amazon_us": {"price": 12.99, "currency": "USD", "bsr": 1542},
    "ml_brl": {"price": 45.90, "currency": "BRL", "sales": 2300}
  },
  "suppliers": [
    {"name": "Shenzhen TechCo", "rating": 4.8, "address": "Shenzhen, Guangdong"}
  ],
  "category": "Acessorios de Celular",
  "source_urls": ["https://1688.com/...", "https://alibaba.com/..."],
  "scraped_at": "2026-07-21T10:00:00Z"
}
```

### Armazenamento

- **Formato:** JSON Lines (`.jsonl`) ou CSV
- **Local:** Data lake local ou S3
- **Retencao:** 90 dias (dados antigos sao resumidos)
- **Deduplicacao:** Por `product_name` + `category`

## Fase 2: Processamento (Silver)

### Pipeline de Geração

```
DADOS BRONZE
    ↓
SELECAO DE TEMPLATE
    ↓
PREENCHIMENTO AUTOMATICO
    ↓
GERACAO DE CONTEUDO (LLM)
    ↓
REVISAO (opcional)
    ↓
PUBLICACAO
```

### Exemplo: Ficha de Produto

```python
# Entrada: dados Bronze de um produto
bronze_data = {
    "product_name": "Capinha iPhone 16",
    "price_1688": 0.45,
    "moq": 10,
    "supplier": "Shenzhen TechCo",
    "supplier_rating": 4.8
}

# Template Silver
template = """
# {product_name} no 1688: Preco, MOQ e Como Importar (2026)

## Preco no 1688
- **Preco unitario:** RMB {price} (~USD {price_usd})
- **MOQ:** {moq} unidades
- **Fornecedor:** {supplier} (Rating: {rating}/5)

## Quanto Custa Importar?
- Frete estimado: ~USD {frete}
- Tarifa: ~{tarifa}%
- Custo do agente: ~{agent_fee}%
- **Custo total estimado:** USD {total}

## Onde Vender?
- Amazon US: USD {amazon_price}
- Mercado Livre: BRL {ml_price}
- **Margem estimada:** {margin}%

## Fornecedores Similares
{similar_suppliers}
"""

# Saida: artigo Silver pronto para publicar
```

### Exemplo: Comparacao 1688 vs Alibaba

```python
# Entrada: dados Bronze de 2 fontes
comparison_data = {
    "product": "Capinha iPhone 16",
    "price_1688": 0.45,
    "price_alibaba": 0.08,
    "gap_percent": 33,
    "same_factory": True
}

# Template gera artigo com:
# - Tabela comparativa
# - Analise do gap
# - Recomendacao por caso de uso
```

## Fase 3: Premium (Gold)

### Relatorio Semanal

```
ENTRADA: Bronze da semana inteira
    ↓
AGREGACAO: Top 50 produtos por margem
    ↓
ANALISE: Tendencias, mudancas de preco
    ↓
OUTPUT: PDF/HTML com:
  - Top 10 oportunidades da semana
  - Alertas de preco
  - Tendencias por categoria
  - Dados para download
```

### Alerta de Margem

```
ENTRADA: Bronze (calculo de margem)
    ↓
FILTRAR: margem > 50%
    ↓
OUTPUT: Email/dashboard com:
  - Produto
  - Preco 1688 vs Amazon/ML
  - Margem calculada
  - Link direto
```

## Frequencia de Atualizacao

| Camada | Frequencia | Metodo |
|---|---|---|
| Bronze | 6-24h | Scraping automatico |
| Silver | Semanal | Pipeline de geracao |
| Gold | Semanal/Mensal | Analise + publicacao |

## Stack Tecnico

| Componente | Ferramenta | Custo |
|---|---|---|
| Scraping | Agentes customizados | Variavel |
| Armazenamento | Local / S3 | $5-20/mes |
| Processamento | Python scripts | $0 |
| Geracao de conteudo | Claude/GPT API | ~$50/mes |
| Publicacao | Next.js + Vercel | ~$20/mes |
| Analytics | Plausible | ~$20/mes |
