# Validation report

- Editions covered: 23
- Distinct country/territory labels across editions: 95 (includes historical names and aliases)
- Nation-edition folders: 537
- Player records: 12221
- Flag SVG source files: 537/537
- Working PNG flag images: 537/537 (512 px wide; aspect ratio preserved)
- Unique player IDs: 12221
- JSON/schema validation errors: 0

## Per-edition coverage

| Year | Nations | Players |
|---:|---:|---:|
| 1930 | 13 | 245 |
| 1934 | 16 | 342 |
| 1938 | 15 | 320 |
| 1950 | 13 | 281 |
| 1954 | 16 | 350 |
| 1958 | 16 | 352 |
| 1962 | 16 | 352 |
| 1966 | 16 | 352 |
| 1970 | 16 | 349 |
| 1974 | 16 | 352 |
| 1978 | 16 | 352 |
| 1982 | 24 | 526 |
| 1986 | 24 | 528 |
| 1990 | 24 | 528 |
| 1994 | 24 | 528 |
| 1998 | 32 | 705 |
| 2002 | 32 | 736 |
| 2006 | 32 | 736 |
| 2010 | 32 | 736 |
| 2014 | 32 | 736 |
| 2018 | 32 | 736 |
| 2022 | 32 | 831 |
| 2026 | 48 | 1248 |

## Null / coverage notes

- Null counts by field: `{"club": 10973, "history.matchesPlayed": 2621, "history.assists": 11000, "history.yellowCards": 2621, "history.redCards": 2621, "age": 77, "history.goals": 27}`.
- Historical club fields are absent in the source; `club` remains null for 1930–2022 rather than being guessed.
- Before 1970, the historical source lacks equivalent individual appearance logs. Unknown matches/minutes/assists/cards remain null; goal events are included when recorded.
- Early-era shirt numbers absent from the source remain null. Stable roster-order suffixes are used only to keep IDs unique.
- 2026 official squad fields come from FIFA; event/appearance detail is from a community dataset and is identified as such.
- A small number of 2026 community-player rows could not be confidently identity-matched to FIFA’s roster; their statistics are null instead of being attached to a possibly wrong player.
- FC24 ratings data was not locally available, so all ratings are explicitly labeled `game-estimate` and use the documented deterministic formula.

## Gaps by category

- Historical club unavailable in source: 10973
- Pre-1970 match-level player detail unavailable: 2594
- Age could not be calculated: 77
- 2026 player-stat identity unresolved: 27

All 537 folders have a validated `flag.png` and retained `flag.svg`; the manifest points to `flag.png` by default.

## Validation errors

- None. All generated JSON files parse; player/skills array lengths agree; IDs are unique; tiers match overall thresholds.

## Sources

- https://github.com/jfjelstul/worldcup (historical dataset; CC BY-SA 4.0).
- https://fdp.fifa.org/assetspublic/ce281/pdf/SquadLists-English.pdf (official 2026 roster data).
- https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026/articles/final-tournament-standings (official 2026 final standings).
- https://github.com/openfootball/worldcup.json (public-domain match dataset).
- https://github.com/mominullptr/FIFA-World-Cup-2026-Dataset (community detailed 2026 events; CC0-1.0).
- https://github.com/lipis/flag-icons and per-file Wikimedia Commons links in `sources.json`.
