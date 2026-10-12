# Porsche Sales Intelligence Dashboard

Dashboard executiva em HTML de arquivo único, construída a partir de uma planilha com 100 vendas de Porsche (dados sanitizados). Projeto da Aceleração AI Reports com Excel, GPT Agents e Claude Code na DIO.

**Dashboard publicada:** https://rodrigo8k.github.io/porsche-agentes-ia/
**Código-fonte:** https://github.com/Rodrigo8k/porsche-agentes-ia

![Dashboard completa](screenshot-dashboard.png)

## Perguntas de negócio escolhidas

1. **Como a receita evolui por ano do modelo?** (linha) — mostra em quais anos-modelo a receita se concentra (pico em 2024), apoiando decisões de estoque e marketing.
2. **Qual a relação entre ano do modelo e preço de venda?** (dispersão) — revela dispersão de preço dentro de cada ano e o peso dos modelos de alto valor (GT3, Turbo S, Dakar).
3. **Como as vendas se distribuem por estado e método de pagamento?** (barras por estado, barras agrupadas e rosca) — mostra concentração regional (TX lidera em receita) e a preferência por Wire Transfer.

Complementam as perguntas: KPIs de topo (vendas, receita, ticket médio, modelo líder, top estado, pagamento predominante), receita por modelo (Top 10) e tabela de pagamento por modelo (Top 5).

## Filtros

Modelo, ano do modelo, estado, cidade e método de pagamento. O filtro de cidade se ajusta ao estado selecionado. Há botões para exportar CSV, exportar PNG (receita por ano) e resetar filtros.

**Exemplo:** Modelo = `Taycan 4S` e Ano = `2025` → 3 vendas, US$ 393.300,00 de receita, ticket médio US$ 131.100,00.

![Filtro aplicado](screenshot-filtro.png)

## Tratamento da base

- Mantidas somente as colunas sanitizadas: `PorscheModelSanitized`, `ModelYearSanitized`, `SalesPriceSanitized`, `PayMethodSanitized`, `CitySanitized`, `StateSanitized`.
- Preço e ano convertidos para número; valores colados como valores, sem fórmulas.
- Conferência: os 100 registros embutidos no HTML batem com a planilha (receita total US$ 12.827.800,50) e nenhuma dessas colunas contém `INVALID`.
- **Dados sensíveis:** a planilha original tem nome de cliente e vendedor, por isso ela **não** está no repositório. Só as seis colunas acima vão embutidas no HTML (array `rawData`).

## Abordagem

Dois caminhos, comparados:

- **ChatGPT com Canvas** para a primeira versão da dashboard.
- **Agente com skill** para refinamentos, mais ajustes em linguagem natural: gráficos de tendência e dispersão, KPIs adicionais, exportação CSV/PNG, reset de filtros, filtro de cidade dependente do estado, logotipo e fonte dos dados.

### Prompt

> Cole aqui o prompt usado e descreva o que mudou até a versão final.

## Como publicar (GitHub Pages)

1. Repositório público, com `index.html` na raiz.
2. *Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save*.
3. Aguarde 1–2 minutos e acesse o endereço acima.

## Tecnologias

HTML5, CSS3 (variáveis CSS), JavaScript vanilla e Chart.js 4.4.7 (CDN). Veja [AGENTS.md](AGENTS.md) para orientações de manutenção.
