# EPIC X1 World Cup Database

Generated locally from open datasets on 2026-11-18. Scope: men's FIFA World Cups 1930–2026 inclusive. Each participating country and edition has its own folder under `cups/<year>/<country-slug>/`. Every team folder contains both `flag.svg` and `flag.png`; use the indexed `flagPath` (PNG) for the widest viewer compatibility. The PNG is rendered at 512 pixels wide, preserving the source aspect ratio, and the original SVG is retained.

## Files

- `players.json`: complete squad, in shirt-number order where numbers are available, with historical facts, match records where the underlying source provides them, and estimated game ratings.
- `skills.json`: compact ratings projection.
- `meta.json`: team/edition, host, coach, final phase, result, a `squad` roster mirror, and the tournament match schedule with opponents, scores, scorers and dates. `players.json` is a pretty-printed array with each player object separated as an individual block; `skills.json` is a compact JSON projection.
- `index.json`: edition and team manifest; each team entry includes a root-relative `flagPath` plus the available formats.
- `validation-report.md`: generated counts, nulls, warnings, and validation outcomes.
- `sources.json`: source URLs and licenses.

## Schema and nulls

Each player has `id`, `name`, `commonName`, `shirtNumber`, `position`, `positions`, `country`, `countrySlug`, `year`, `edition`, `club`, `age`, `history`, `attributes`, `overall`, `tier`, `isLegend`, `achievements`, `ratingType`, `overallAdjustment`, and `sources`. `null` means the ingested source does not provide a defensible value; it is not replaced by a guess. Historical source club fields are absent, so `club` is null for 1930–2022. Birth dates are used only when present to calculate age on tournament opening day. Shirt numbers absent in the historical dataset remain null.

Player appearance records in the Fjelstul dataset start in 1970, because earlier FIFA match reports do not contain equivalent substitution/appearance detail. Therefore `matchesPlayed` is null before 1970 (while goals and specific goal-match events are included where recorded); individual assists are null for 1930–2022. Cards before 1970 are null, not zero. Minutes before 1970 are null.

For 2026, player names, positions, squad numbers, DOB, club, and coaches come from FIFA's official squad-list PDF. Tournament results and 48-team completion are cross-checked against FIFA. Match-level player details are drawn from the cited open dataset and are not asserted to be official FIFA data.

## Rating methodology

Ratings are game estimates, not official FIFA or EA ratings. All values use integer 0–100 scales. The position-relevant weighted mean uses these weights (unlisted attributes have zero weight):

- GK: goalkeeping 0.50, agility 0.15, strength 0.10, physical 0.10, skill 0.05, passing 0.05, speed 0.05.
- DEF: defending 0.30, strength 0.20, physical 0.15, agility 0.10, speed 0.10, passing 0.10, skill 0.05.
- MID: passing 0.25, skill 0.20, agility 0.15, defending 0.10, strength 0.10, physical 0.10, speed 0.05, shooting 0.05.
- ATT: shooting 0.30, skill 0.25, speed 0.15, agility 0.15, physical 0.10, strength 0.025, passing 0.025.

The non-anchor historical core is `73 + min(10, round(matches×1.15)) + min(10, round(goals×1.35)) + min(4, round(assists×0.65)) + min(5, 2×individual_awards)` when match coverage is unavailable before 1970; otherwise it starts at 67. For 2026, the corresponding core starts at 67 and uses its published appearance, goal and assist totals; unresolved identity links use 73 and keep the associated stats null. The core is clamped to the documented rating range. Position-specific attribute offsets (scaled to 40% and centered on the weighted mean) produce the attribute profile; an individual-award reputation bonus of 1 (otherwise 0), minus the rounded profile residual, yields `overallAdjustment` capped ±3. `overall = clamp(round(weighted mean) + overallAdjustment, 40, 99)`. Profile adjustments are centered on the position-weighted mean; the residual era/reputation calibration is capped at ±3. Curated historical calibration anchors include Pelé 1970 97, Maradona 1986 96, Messi 2022 94, and other peak-cup all-time greats. Tier thresholds: LEGEND ≥90, EPIC 84–89, RARE 75–83, COMMON <75. `isLegend` is a separate curated iconic-player marker, not synonymous with the tier.

The EA Sports FC 24 file suggested for crosswalk was not part of the locally available source inputs; no access-restricted Kaggle values were fabricated or silently substituted. Consequently all ratings are marked `game-estimate`.

## Sources and licenses

Historical factual data (1930–2022) uses the Fjelstul World Cup Database CSVs, licensed CC BY-SA 4.0. 2026 official squad fields use FIFA's published PDF. The 2026 team results page is FIFA's public result source; detailed individual event/appearance fields are sourced from the cited 2026 community dataset, licensed CC0, and should be reviewed before critical use. Match data from openfootball is public domain. Standard flags use `lipis/flag-icons` (MIT); historical flags use their individual Wikimedia Commons source pages. Full URLs are in `sources.json` and per-player JSON.
