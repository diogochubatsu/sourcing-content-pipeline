# 05 — Fontes de Dados Multilingues

## Visao Geral

O Bronze agrega dados de **multiplas fontes em multiplos idiomas**, criando um datalake que nenhum concorrente replicado.

## Fontes por Idioma

### Chines (ZH)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| 1688.com | 1688.com | Precos atacado, MOQ, fornecedores | **Critica** |
| Alibaba.com | alibaba.com | Precos export, MOQ, Gold Supplier | **Alta** |
| Taobao | taobao.com | Precos varejo | Media |
| Tmall | tmall.com | Precos premium | Media |
| Pinduoduo | pinduoduo.com | Precos promocao | Media |

**Por que importa:** 1688 e a fonte mais barata para maioria dos produtos. Dados em chines dao acesso direto ao mercado doméstico.

### Ingles (EN)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| Amazon US | amazon.com | Precos, BSR, reviews | **Critica** |
| Amazon UK | amazon.co.uk | Precos, BSR | **Alta** |
| AliExpress | aliexpress.com | Precos, fornecedores | **Alta** |
| eBay | ebay.com | Precos, vendas | Media |

**Por que importa:** Amazon e a referencia de preco para varejo. AliExpress e a plataforma de compra para consumidores finais.

### Japones (JA)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| Rakuten | rakuten.co.jp | Precos, fornecedores | **Alta** |
| Rakumart | rakumart.com | Precos atacado | **Alta** |
| Amazon JP | amazon.co.jp | Precos, BSR | Media |
| Yahoo Shopping JP | shopping.yahoo.co.jp | Precos | Media |

**Por que importa:** Japao tem mercado forte para eletronicos e produtos premium. Poucos sites de sourcing cobrem Rakuten.

### Portugues (PT)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| Mercado Livre BR | mercadolivre.com.br | Precos, vendas, reputacao | **Critica** |
| Amazon BR | amazon.com.br | Precos, BSR | **Alta** |
| Shopee BR | shopee.com.br | Precos | Media |

**Por que importa:** Mercado Livre e a referencia de preco para o Brasil. Dados em portugues dao acesso ao publico LATAM.

### Espanhol (ES)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| Mercado Livre MX | mercadolibre.com.mx | Precos, vendas | **Alta** |
| Mercado Livre AR | mercadolibre.com.ar | Precos, vendas | **Alta** |
| Amazon ES | amazon.es | Precos, BSR | Media |

**Por que importa:** Mercado Libre cobre toda America Latina em espanhol. Mercado inexplorado por sites de sourcing em ingles.

### Polones (PL)

| Fonte | URL | Tipo de Dado | Importancia |
|---|---|---|---|
| Allegro | allegro.pl | Precos, vendas | **Alta** |
| Amazon PL | amazon.pl | Precos, BSR | Media |

**Por que importa:** Polonia e hub de e-commerce na Europa Oriental. Pouquissimo conteudo sobre sourcing da China em polones.

## Tabela Unificada (Bronze)

### Schema

```csv
product_name,product_name_zh,product_name_ja,product_name_es,price_1688_cny,price_alibaba_usd,price_amazon_usd,price_amazon_br_brl,price_ml_brl,price_rakuten_jpy,price_allegro_pln,moq,supplier_name,supplier_rating,supplier_address,category,source_urls,scraped_at
```

### Exemplo de Linha

```csv
"Capinha iPhone 16","iPhone 16手机壳","iPhone 16ケース","Funda iPhone 16",0.45,0.08,12.99,45.90,39.90,1200,29.90,10,"Shenzhen TechCo",4.8,"Shenzhen, Guangdong","Acessorios de Celular","https://1688.com/...,https://alibaba.com/...,https://amazon.com/...",2026-07-21T10:00:00Z
```

## Cobertura Atual vs Ideal

| Idioma | Fonte Principal | Status | Prioridade |
|---|---|---|---|
| Chines | 1688 + Alibaba | **Ativo** | — |
| Ingles | Amazon + AliExpress | **Ativo** | — |
| Japones | Rakuten | **Pendente** | Alta |
| Portugues | Mercado Livre | **Pendente** | Alta |
| Espanhol | Mercado Libre | **Pendente** | Media |
| Polones | Allegro | **Pendente** | Media |

## Oportunidade de Mercado

| Idioma | Concorrentes | Oportunidade |
|---|---|---|
| Ingles | Muitos | Difícil se diferenciar |
| Portugues | Poucos | **Enorme** — mercado BR enorme |
| Espanhol | Quase nenhum | **Enorme** — LATAM inexplorado |
| Japones | Nenhum em sourcing | **Unico** — niche premium |
| Polones | Nenhum | **Unico** — Europa Oriental |
