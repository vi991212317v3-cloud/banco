# EPIC X1 — banco V2: atualização de Overall

## O que mudou

A V2 é uma cópia da V1. Foram alterados exclusivamente os campos numéricos `overall` em `players.json` e `skills.json`, usando Overall publicado em bases de ratings de jogos EA/FIFA quando houve correspondência conservadora de identidade. Nenhum outro campo existente foi editado. A V1 permanece intacta.

Foram processados **12.221 registros de jogadores**. Há correspondência de fonte de jogo para **3,338 (27.31%)**; **3,178 valores mudaram** e 160 já eram iguais. Em **8,883** registros, não encontrei uma correspondência segura nos conjuntos consultados; nesses casos, o valor da V1 foi mantido para não inventar rating nem deixar o campo vazio.

Na edição 2026, foram encontrados ratings para **806 de 1.248** jogadores. Distribuição de correspondências por Copa: `{1994: 1, 1998: 13, 2002: 71, 2006: 208, 2010: 451, 2014: 599, 2018: 570, 2022: 619, 2026: 806}`. Distribuição por base: `{'FIFA 2015': 1201, 'FIFA 2016': 62, 'FIFA 2019': 44, 'FIFA 2017': 49, 'FIFA 2021': 31, 'FIFA 2018': 470, 'FC27': 379, 'FC26': 651, 'FIFA 2020': 13, 'FIFA 2022': 438}`.

## Escopo e interpretação

A FIFA não publica um Overall numérico universal para cada atleta de cada Copa. As notas usadas nesta V2 são Overall de videogame FIFA/EA, não ratings oficiais de performance atribuídos pela FIFA ao torneio. Os ratings das bases FIFA15–22 vieram de dados SoFIFA; FC26 veio de um espelho público de dataset SoFIFA; FC27 veio de snapshot público declarado como extraído da EA Public Ratings API. A seleção prioriza a edição do jogo mais próxima do ano da Copa entre as bases disponíveis.

As correspondências exigiram nacionalidade compatível, nome com similaridade alta e idade plausível (ou nome exatamente igual em edição contemporânea quando a idade estava indisponível). Homônimos ambíguos foram omitidos.

O arquivo [`overall-sources.csv`](overall-sources.csv) registra cada fonte e correspondência. O arquivo [`sources-v2.md`](sources-v2.md) registra links e notas de proveniência.

## Limitação deliberada

Como foi pedido para não alterar nada além do Overall, campos derivados como `tier`, avaliações de atributos e rótulos textuais de tipo de rating foram preservados como na V1; eles não foram recalculados. Assim, esses campos podem não refletir o novo Overall.
