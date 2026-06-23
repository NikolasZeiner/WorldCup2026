# 2026 FIFA World Cup Live Tracker 🏆⚽

**Tools:** Python | Power BI | ESPN API
**Data:** Live tournament data updated daily via ESPN API

## Overview

A fully automated live tracking dashboard for the 2026 FIFA World Cup.
Built a Python data pipeline that pulls real-time match data from the
ESPN API and feeds into a 2-page Power BI dashboard updated daily
throughout the tournament.

## Live Dashboard Preview

![Tournament Overview](https://github.com/NikolasZeiner/WorldCup2026/raw/main/Screenshot%202026-06-15%20155956.png)
![Team Deep Dive](https://github.com/NikolasZeiner/WorldCup2026/raw/main/Screenshot%202026-06-15%20160017.png)

## Key Features

- **Live match results** — scores, goals, assists updated daily
- **Goal scorers** — every goal with scorer, assist, and minute
- **Discipline tracking** — yellow and red cards by team
- **Group standings** — points table updated after every match
- **Team Deep Dive** — filter by nation for individual team stats
- **Match Day trends** — goals scored by match day chart
- **Possession vs Goals** — tactical analysis scatter plot
- **Shot efficiency** — shots vs shots on target by team

## Dashboard Pages

### Page 1 — Tournament Overview

- 5 KPI cards: Matches Played, Total Goals, Avg Goals/Match, Red Cards, Yellow Cards
- Nation slicer for filtering all visuals
- Goal Scorers table with scorer, assist, minute, and team
- Goals Scored by Nation bar chart
- Discipline by Nation stacked bar (yellow and red cards)
- Match Results table with GF/GA
- Goals by Match Day column chart
- Group Stage Standings table

### Page 2 — Team Deep Dive

- 6 KPI cards: Matches Played, Points, Goals Scored, Goals Conceded, Pass Completion %, Goals Per Game
- Nation tile slicer
- Shots vs Shots on Target clustered bar chart
- Possession % vs Goals scatter plot
- Top Scorers bar chart
- Results donut chart (Win/Draw/Loss)

## Data Pipeline

Built entirely in Python using the ESPN unofficial API:

- `site.api.espn.com/apis/site/v2/sports/soccer/fifa.world/scoreboard` — match results
- `site.api.espn.com/apis/site/v2/sports/soccer/fifa.world/summary` — detailed match stats

### Files Exported Daily (13 CSVs)

| File | Description |
| --- | --- |
| wc2026_all_matches.csv | All 72 tournament matches |
| wc2026_completed.csv | Completed matches with results |
| wc2026_goals_detail.csv | Individual goals with scorer and assist |
| wc2026_goals_summary.csv | Goals by team |
| wc2026_match_stats.csv | Possession, shots, passes per team |
| wc2026_discipline.csv | Cards with player names |
| wc2026_yellow_cards.csv | Yellow cards |
| wc2026_red_cards.csv | Red cards (VAR overturned removed) |
| wc2026_standings.csv | Group stage standings |
| wc2026_team_matches.csv | One row per team per match |
| wc2026_team_stats_avg.csv | Averaged team stats |
| wc2026_match_day_goals.csv | Goals by match day |
| wc2026_teams.csv | Teams that have played |

## How to Update

1. Open `WorldCup2026_Tracker.ipynb` in Google Colab
2. Run Script 1 — pulls all data and downloads 10 CSV files
3. Run Script 2 — downloads remaining 3 CSV files
4. Replace all CSVs in your local folder
5. Open `WorldCup2026.pbix` in Power BI → click **Refresh**

## Key Findings So Far

*(Updated through 44 completed matches)*

- **134 total goals** scored across 44 matches — averaging **3.05 goals per match**
- **Germany leads the tournament** with 9 goals scored, including a **7-1 win over Curacao** — the biggest margin of victory so far (6 goals)
- **Lionel Messi leads all individual scorers** with 5 goals
- **Group stage is tight at the top:** Germany, United States, France, Argentina, and Norway are all unbeaten through 2 matches with 6 points each — Germany holds the best goal differential (+7)
- **104 yellow cards and 8 red cards** issued so far
- **South Africa has picked up the most red cards** of any team (2), both coming in their match vs. Mexico

## Technical Highlights

- MST timezone conversion for accurate match dates
- VAR overturned red card filtering
- Special character standardization (Curaçao → Curacao, Türkiye → Turkey)
- Penalty goal extraction (ESPN logs as separate event type)
- 12 DAX measures for dynamic filtering by nation

## Skills Demonstrated

Python · pandas · REST API · Power BI · DAX ·
Data Pipeline · Sports Analytics · Live Data · ETL

## Live Portfolio

[View Portfolio](https://nikolaszeiner.github.io/NikolasZeiner/)
