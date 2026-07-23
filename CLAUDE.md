# CLAUDE.md — Instrucoes para o Proximo Agente

## Sobre Este Projeto

Sistema de captura de trafego de sourcing da China/Japao com arquitetura medalion de dados (Bronze/Silver/Gold).

## Contexto da Sessao Anterior

Esta sessao discutiu e documentou:

1. **Plano original:** 4 sites de nicho para capturar trafego de sourcing
2. **Arquitetura medalion:** Bronze (datalake) → Silver (templates) → Gold (premium)
3. **Abordagem hibrida:** Scraping de produtos + Reviews/Analises
4. **Templates de conteudo:** Ficha de Produto, Comparacao, Best Of List, Analise de Mercado
5. **Fontes multilingues:** 1688, Alibaba, Rakuten, Amazon, ML em PT/ES/JA/PL

## O Que Ja Foi Feito

- [x] Documentacao completa no repositorio
- [x] Schema Bronze (hibrido com reviews)
- [x] Templates Silver (4 tipos)
- [x] Template Gold (relatorio semanal)
- [x] Analise de concorrencia
- [x] Estrategia de monetizacao
- [x] Cronograma de implementacao

## O Que Falta Fazer

- [ ] Implementar pipeline de scraping (Bronze)
- [ ] Criar site Next.js (primeiro site)
- [ ] Automatizar geracao de conteudo (Silver)
- [ ] Configurar analytics e email capture
- [ ] Testar com 20-50 artigos reais

## Estrutura do Repositorio

```
sourcing-content-pipeline/
├── README.md                    # Visao geral
├── CLAUDE.md                    # Este arquivo
├── docs/
│   ├── 01-visao-geral.md        # Problema e solucao
│   ├── 02-arquitetura-medallion.md  # Bronze/Silver/Gold
│   ├── 03-pipeline-dados.md     # Fluxo tecnico
│   ├── 04-templates-conteudo.md # Templates Silver
│   ├── 05-fontes-dados.md       # Fontes multilingues
│   ├── 06-monetizacao.md        # Estrategias de receita
│   ├── 07-cronograma.md         # Fases
│   ├── 08-concorrencia.md       # Analise de mercado
│   └── 09-comparacao-abordagens.md  # Scraping vs Reviews
├── templates/
│   ├── bronze/
│   │   ├── schema.csv           # Schema de dados
│   │   └── schema-hibrido.csv   # Schema com reviews
│   ├── silver/
│   │   ├── ficha-produto.md     # Template produto
│   │   ├── comparacao.md        # Template comparacao
│   │   ├── best-of-list.md      # Template reviews
│   │   └── analise-mercado.md   # Template analise
│   └── gold/
│       └── relatorio-semanal.md # Template premium
└── data/
    └── sample-bronze.csv        # Dados de exemplo
```

## Arquitetura

### Bronze (Datalake) — Hibrido

**Fontes de Produtos (scraping):**
- 1688.com (chines) — Precos, MOQ, fornecedores
- Alibaba.com (ingles/chines) — Precos, MOQ
- Rakuten/Rakumart (japones) — Precos
- Mercado Livre (portugues/espanhol) — Precos
- Amazon (ingles/PT/ES) — Precos, BSR

**Fontes de Reviews (curadoria):**
- Amazon Reviews — Opinoes de compradores
- Reddit — Discussoes comunitarias
- YouTube — Reviews em video
- Google Trends — Tendencias

### Silver (Templates)

**Conteudo de Dados:**
- Ficha de Produto (preco + MOQ + fornecedor)
- Comparacao (1688 vs Alibaba vs Amazon)

**Conteudo de Reviews:**
- Best Of List (Top 10 por categoria)
- Analise de Mercado (tendencias + dados)

### Gold (Premium)
- Relatorios semanais
- Alertas de margem
- Analises multilingues

## Tecnologias

- **Framework:** Next.js + Vercel
- **Analytics:** Plausible
- **Email:** Beehiiv
- **DNS:** Cloudflare
- **Scraping:** Agentes customizados
- **LLM:** Claude/GPT API para geracao

## Regras

1. **Dados reais** — Todo numero vem de scraping, nao inventado
2. **Multi-idioma** — Conteudo em PT, ES, JA, PL quando possivel
3. **Qualidade > Quantidade** — Melhor 10 artigos bons que 100 ruins
4. **Automatizar** — Pipeline deve gerar conteudo sem intervencao manual
5. **Medir** — Toda decisao baseada em dados reais

## Contato

- **Autor:** diogochubatsu
- **Repositorio:** https://github.com/diogochubatsu/sourcing-content-pipeline
