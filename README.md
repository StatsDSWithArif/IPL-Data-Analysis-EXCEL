# IPL Cricket Analytics — Case Study

A formula-driven Excel analysis of 13 seasons of Indian Premier League T20 cricket (2008–2020), covering 816 matches and 194,112 ball-by-ball deliveries, plus a business-problem write-up of the findings.

## Files in This Project

| File | What It Is |
|---|---|
| `IPL_Cricket_Analytics_Case_Study.xlsx` | The full analysis: 14 sheets of raw data, enriched data, aggregated tables, leaderboards, a 7-chart dashboard, and a documentation sheet indexing every function/chart/table used. |
| `IPL_Business_Problems_Solved.pdf` | A 7-problem business write-up (context → approach → findings → recommendation) built from the workbook's results. Written for a portfolio, interview, or resume walkthrough. |
| `README.md` | This file. |

## Dataset

- **Source:** Kaggle-style IPL ball-by-ball dataset (2008–2020), originally supplied as a lecture workbook.
- **Match-level records:** 816 matches, 17 fields each (teams, toss, venue, result, margin, etc.).
- **Ball-by-ball records:** 194,112 deliveries, 18 fields each (batsman, bowler, runs, extras, wicket details, etc.).
- **Deep-dive match:** Full 235-ball feed for the 2020 IPL Final (Mumbai Indians vs. Delhi Capitals).

## How the Workbook Is Organized

1. **Case Study Overview** — objective, dataset summary, and headline insights (live formulas, recalculate automatically).
2. **Dashboard** — 7 charts: wins by team, toss-decision split, season run trend, sixes vs. fours by season, top run scorers, top wicket takers, matches by venue.
3. **Team Performance** — matches, wins, losses, toss stats for all 15 franchises.
4. **Toss & Outcome Analysis** — whether winning the toss predicts the match winner.
5. **Season Trends** — runs, sixes, fours, and wickets by season.
6. **Venue Analysis** — matches hosted, winning margins, and bat-first/field-first splits for the top 10 venues.
7. **Batting Leaderboard / Bowling Leaderboard** — top 15 run scorers and wicket takers, ranked.
8. **Final Match Deep-Dive** — full scorecard reconstruction of the 2020 Final.
9. **Match Data (Enriched)** — the raw match log plus derived Season and Toss-Winner-Won-Match columns.
10. **IPL Match Data (Raw) / Ball by Ball Data (Raw) / MI vs DC Final (Raw)** — untouched source data.
11. **Functions, Charts & Tables Used** — a complete index of every technique applied, for quick reference.

## Methodology

Every number in the workbook is produced by a live Excel formula — nothing is hardcoded — so the analysis recalculates automatically if the source data changes. Key techniques:

- **Aggregation:** `SUMIFS`, `COUNTIFS`, `AVERAGEIFS`, `COUNTIF`, `SUMPRODUCT`
- **Lookup:** `INDEX` / `MATCH`, including an approximate-match (binary-search) lookup that links all 194,112 deliveries back to their season via a 13-row boundary table rather than a slow row-by-row exact-match scan
- **Logic:** `IF`, `IFS`, `IFERROR`
- **Statistical:** `RANK`, `MAX` / `MAXIFS`, `LARGE` / `SMALL`
- **Text:** `TEXT`, `TEXTJOIN`, `YEAR`, `ROUND`, `COUNTA`

Domain conventions applied for accuracy: balls faced excludes wide deliveries; bowling wickets exclude run-outs, retired-hurt, and obstructing-the-field dismissals; runs conceded strips out byes and leg-byes — all matching standard cricket scoring rules.

## Headline Findings

- **Most successful franchise:** Mumbai Indians — 120 wins, 59.1% win rate across 203 matches.
- **Toss impact:** Toss winners win only 51.2% of matches — barely better than a coin flip, despite 60.8% of captains choosing to field first.
- **Scoring trend:** League average runs/match rose from 309.3 (2008) to a peak of 331.7 (2018); wickets/match stayed stable throughout.
- **Top run scorer:** V Kohli — 5,878 runs; best combined average/strike rate among top scorers: DA Warner (42.7 / 141.5).
- **Top wicket taker:** SL Malinga — 170 wickets, also the best strike rate (16.6) among the top 6.
- **Most batter-friendly venue:** M. Chinnaswamy Stadium — average winning margin of 48 runs, well above the other top-10 venues.

Full detail, context, and recommendations for each of these are in `IPL_Business_Problems_Solved.pdf`.

## Suggested Use

- **Resume / portfolio:** Reference the "Functions, Charts & Tables Used" sheet directly as a skills index; the PDF doubles as a business-case writing sample.
- **Extending the analysis:** Add new seasons by appending rows to the raw data sheets and extending the season-boundary lookup table — all downstream formulas will recalculate without modification.
