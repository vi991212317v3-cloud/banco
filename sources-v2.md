# Fontes externas consultadas para V2

- EA SPORTS FC ratings: https://www.ea.com/en/games/ea-sports-fc/ratings
  A página oficial publica tabela de ratings de uma edição específica do jogo (FC27) e explica que a tabela reflete apenas cartas Gold/Silver/Bronze do Ultimate Team no lançamento; não inclui Icons/Heroes/campanhas nem atualizações live. Não é um Overall oficial da FIFA para uma Copa inteira.
- SoFIFA: https://sofifa.com/players
  Arquivo de edições de videogame listadas na página inclui FIFA07 até FC26; o banco permite consultas por edição e os campos incluem Overall. As notas são de videogame, não nota de performance da FIFA no torneio.
- Kaggle FIFA 22 complete player dataset: https://www.kaggle.com/datasets/stefanoleone992/fifa-22-complete-player-dataset
  A ficha descreve os arquivos de Career Mode FIFA15–FIFA22; 19k+ jogadores e atributos de jogo; os dados foram raspados de SoFIFA; licença declarada CC0.
- Repositório multi-edition FIFA15–22 usado: https://github.com/wimmerth/fifa-data-visualization
  Arquivo combinado local `fifa_players_15_22_clean.csv`, colunas `sofifa_id`, `short_name`, `long_name`, `overall`, `year`, `age`, `dob`, `nationality_name`; anos encontrados 2015–2022.
- Kaggle FIFA Players Dataset: https://www.kaggle.com/datasets/luisfucros/fifa-players
  A página declara arquivos de jogadores FIFA15–22 e dados SoFIFA; menciona nacionalidade, data de nascimento e Overall; licença declarada MIT.
- FC26 public dataset mirror: https://github.com/ismailoksuz/EAFC26-DataHub
  README diz que `data/players.csv` foi obtido de https://www.kaggle.com/datasets/rovnez/fc-26-fifa-26-player-data, com mais de 18k records, rating overall e estatísticas; dataset espelha SoFIFA.
- FC27 public ratings snapshot: https://github.com/LakshmiKanth11/EA_FC_ANALYSIS
  README declara 19,789 jogadores retirados da EA public ratings API, snapshot 2026-09-12, com `overall_rating`, nacionalidade, posição e dados biográficos. O arquivo de ratings públicos inclui o escopo do FC27.
- FIFA official World Cup 2026 team statistics article: https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026/articles/numbers-squads-stats
  Publica fatos estatísticos de equipes/plantéis, idade e representação de clubes, mas não Overall numérico de videogame.

Conclusão metodológica: o Overall não é uma métrica universal/publicada pela FIFA para todos os jogadores de cada edição da Copa. A V2 só pode substituir o Overall por valor quando há correspondência segura a uma nota de videogame publicada; nenhuma nota é calculada a partir de estatísticas do torneio e apresentada como oficial.
