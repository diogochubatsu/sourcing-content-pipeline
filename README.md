# Sourcing Content Pipeline

Sistema de captura de trafego de sourcing da China/Japao com arquitetura medalion de dados.

## Visao Geral

Este projeto implementa um pipeline de dados **hibrido** que combina:
1. **Scraping de produtos** — precos, MOQ, fornecedores de 1688, Alibaba, Amazon, ML
2. **Conteudo de reviews/analises** — curadoria, comparativos, "best of", analises de mercado

O Bronze agrega dados de **multiplas fontes e idiomas**. O Silver gera conteudo automaticamente. O Gold entrega produtos premium.

## Arquitetura Medalion

```
         GOLD (5-10%)
        ┌─────────┐
        │ Relatorios │  ← Diferencial competitivo
        │ Insights   │  ← Gera backlinks
        └─────────┘
       SILVER (30-40%)
      ┌─────────────┐
      │  Comparacoes  │  ← Valor real
      │  Analises     │  ← Gera engajamento
      └─────────────┘
    BRONZE (50-60%)
   ┌─────────────────┐
   │  Dados de         │  ← Volume
   │  Multiplas Fontes │  ← Indexacao
   │  Multi-idioma     │  ← Autoridade
   └─────────────────┘
```

### Bronze (Datalake) — Hibrido
Dados brutos de **duas categorias de fontes**:

**Fontes de Produtos (scraping):**
- **1688.com** (chines) — Precos, MOQ, fornecedores
- **Alibaba.com** (ingles/chines) — Precos, MOQ, fornecedores
- **Rakuten/Rakumart** (japones) — Precos, fornecedores
- **Mercado Livre** (portugues/espanhol) — Precos, vendedores
- **Amazon** (ingles/PT/ES) — Precos, BSR, reviews

**Fontes de Reviews/Analises (curadoria):**
- **Amazon Reviews** — Opinoes de compradores
- **Reddit** — Discussoes de comunidades (r/FulfillmentByAmazon, r/1688)
- **YouTube** — Reviews em video
- **Blogs de nicho** — Analises especializadas
- **Google Trends** — Volume de busca e tendencias

### Silver (Templates) — Hibrido
Artigos gerados a partir do Bronze, em **duas categorias**:

**Conteudo de Dados (scraping):**
- Fichas de Produto (preco + MOQ + fornecedor)
- Comparacoes de preco (1688 vs Alibaba vs Amazon)
- Calculos de Custo de Importacao

**Conteudo de Reviews/Analises (curadoria):**
- "Best of" lists (Top 10 produtos por categoria)
- Comparativos editorial (qualidade vs preco)
- Analises de tendencias
- Guias de compra baseados em reviews

### Gold (Premium)
Produtos de alto valor:
- Relatorios semanais de tendencias
- Alertas de margem cross-border
- Analises de mercado multilingues
- Artigos de pesquisa original

## Sites Destino

| Site | Nicho | Idioma Principal |
|------|-------|------------------|
| 1688master.com | 1688 especifico | Ingles |
| alibabaexperts.com | Alibaba especifico | Ingles |
| importelectronics.com | Eletronicos | Ingles |
| yiwuagents.com | Yiwu Market | Ingles |

## Estrutura do Repositorio

```
sourcing-content-pipeline/
├── README.md
├── docs/
│   ├── 01-visao-geral.md
│   ├── 02-arquitetura-medallion.md
│   ├── 03-pipeline-dados.md
│   ├── 04-templates-conteudo.md
│   ├── 05-fontes-dados.md
│   ├── 06-monetizacao.md
│   ├── 07-cronograma.md
│   ├── 08-concorrencia.md
│   └── 09-comparacao-abordagens.md   ← NOVO
├── templates/
│   ├── bronze/
│   │   └── schema.csv
│   ├── silver/
│   │   ├── ficha-produto.md
│   │   ├── comparacao.md
│   │   ├── best-of-list.md           ← NOVO
│   │   └── analise-mercado.md        ← NOVO
│   └── gold/
│       └── relatorio-semanal.md
└── data/
    └── sample-bronze.csv
```

## Status

Em fase de planejamento e documentacao.

## Licenca

Proprietario — Uso interno.
