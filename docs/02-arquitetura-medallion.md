# 02 — Arquitetura Medalion de Conteudo

## Conceito

Inspirada na arquitetura medalion de dados (Bronze/Silver/Gold) usada em data engineering, adaptada para geracao de conteudo.

## Camada Bronze — Datalake

### O Que E
Tabela unificada com dados brutos de **multiplas fontes e idiomas**.

### Schema

```
| product_name | product_name_zh | product_name_ja | price_1688 | price_alibaba | price_amazon | price_ml | price_rakuten | moq | supplier_rating | supplier_address | category | source_url | scraped_at |
```

### Fontes

| Fonte | Idioma | Dados Capturados |
|---|---|---|
| 1688.com | Chines | Preco RMB, MOQ, rating fornecedor, tempo resposta |
| Alibaba.com | Ingles/Chines | Preco USD, MOQ, Gold Supplier, Trade Assurance |
| Rakuten/Rakumart | Japones | Preco JPY, fornecedor, avaliacao |
| Mercado Livre | Portugues/Espanhol | Preco BRL/USD, vendas, reputacao |
| Amazon | Ingles/PT/ES | Preco, BSR, reviews, ranking |
| Taobao/Tmall | Chines | Preco varejo |
| AliExpress | Ingles | Preco, fornecedor, avaliacao |
| Google Trends | Multilingue | Volume de busca, tendencias |

### Regras Bronze

1. **Dados brutos** — sem transformacao, sem interpretacao
2. **Timestamp obrigatorio** — toda linha tem `scraped_at`
3. **Fonte identificada** — toda linha tem `source_url`
4. **Deduplicacao por SKU** — mesmo produto de fontes diferentes = mesma linha
5. **Idioma preservado** — nomes em todos os idiomas capturados

## Camada Silver — Templates

### O Que E
Artigos publicaveis gerados a partir do Bronze + templates padronizados.

### Templates

| Template | Fontes Bronze Necessarias | Output |
|---|---|---|
| Ficha de Produto | 1688 (minimo) | Artigo com preco, MOQ, fornecedor |
| Comparacao 1688 vs Alibaba | 1688 + Alibaba | Artigo com gap de preco |
| Comparacao 1688 vs Amazon | 1688 + Amazon | Artigo com margem estimada |
| Comparacao Multi-Plataforma | 4+ fontes | Artigo global |
| Custo de Importacao | 1688 + tabelas de frete | Artigo com calculo completo |
| Ranking de Fornecedores | 1688 (multiplos fornecedores) | Artigo com top 10 |
| Lista por Categoria | 1688 (categoria) | Artigo com top 20 produtos |
| Calculadora | 1688 + Amazon + frete | Ferramenta interativa |

### Regras Silver

1. **Dados do Bronze** — todo numero vem da tabela Bronze, nao inventado
2. **Template fixo** — estrutura padronizada, variavel e so o produto/categoria
3. **Automatizavel** — pipeline gera artigo a partir de Bronze + template
4. **Revisavel** — humano pode revisar antes de publicar

## Camada Gold — Premium

### O Que E
Produtos de alto valor que geram receita e autoridade.

### Formatos

| Produto | Fonte | Preco |
|---|---|---|
| Relatorio Semanal de Tendencias | Bronze + Google Trends | $19-49/mes |
| Alerta de Margem Cross-Border | Bronze (calculado) | $9/mes |
| Analise de Mercado por Regiao | Bronze multilingue | $99-199/relatorio |
| Pesquisa Original | Bronze + trabalho manual | Gratuito (autoridade) |

### Regras Gold

1. **Exclusividade** — conteudo que ninguem mais tem
2. **Valor mensuravel** — economia ou lucro concreto para o leitor
3. **Atualizacao regular** — semanal ou mensal
4. **Formato premium** — PDF, dashboard, ou tool

## Fluxo Completo

```
┌─────────────────────────────────────────────────────┐
│                    BRONZE (Datalake)                │
│                                                     │
│  1688 ──┐                                          │
│  Alibaba ─┤                                         │
│  Rakuten ─┤                                         │
│  Amazon ──┼──→ TABELA UNIFICADA                     │
│  ML ─────┤     (produtos, precos,                   │
│  Taobao ─┤      fornecedores,                       │
│  Google ──┘      idiomas, fontes)                   │
│                                                     │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│                 SILVER (Templates)                  │
│                                                     │
│  Bronze + Template = Artigo publicavel              │
│                                                     │
│  "Ficha de Produto" + dados 1688 = Artigo           │
│  "Comparacao" + dados 1688 + Alibaba = Artigo       │
│  "Custo Importacao" + dados + frete = Artigo        │
│                                                     │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│                   Gold (Premium)                    │
│                                                     │
│  Relatorios semanais de tendencias                  │
│  Analises de mercado por idioma/regiao              │
│  Alertas de oportunidade cross-border               │
│  Artigos de pesquisa original                       │
│                                                     │
└─────────────────────────────────────────────────────┘
```
