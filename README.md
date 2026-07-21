# Sourcing Content Pipeline

Sistema de captura de trafego de sourcing da China/Japao com arquitetura medalion de dados.

## Visao Geral

Este projeto implementa um pipeline de dados que captura precos, fornecedores e informacoes de mercado de multiplas fontes (1688, Alibaba, Rakuten, Mercado Livre, Amazon) em multiplos idiomas, e gera conteudo automaticamente para sites de nicho de importacao.

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

### Bronze (Datalake)
Dados brutos de multiplas fontes e idiomas:
- **1688.com** (chines) — Precos, MOQ, fornecedores
- **Alibaba.com** (ingles/chines) — Precos, MOQ, fornecedores
- **Rakuten/Rakumart** (japones) — Precos, fornecedores
- **Mercado Livre** (portugues/espanhol) — Precos, vendedores
- **Amazon** (ingles/PT/ES) — Precos, BSR, reviews
- **Google Trends** (multilingue) — Volume de busca

### Silver (Templates)
Artigos gerados automaticamente a partir do Bronze:
- Fichas de Produto (preco + MOQ + fornecedor)
- Comparacoes (1688 vs Alibaba vs Amazon vs ML)
- Calculos de Custo de Importacao
- Rankings de Fornecedores

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
│   └── 08-concorrencia.md
├── templates/
│   ├── bronze/
│   │   └── schema.csv
│   ├── silver/
│   │   ├── ficha-produto.md
│   │   └── comparacao.md
│   └── gold/
│       └── relatorio-semanal.md
└── data/
    └── sample-bronze.csv
```

## Status

Em fase de planejamento e documentacao.

## Licenca

Proprietario — Uso interno.
