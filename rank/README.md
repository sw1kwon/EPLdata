# rank

Each file contains season-specific standings, separated into:

## Data Coverage

- Seasons: 1992–93 (`9293`) to 2023–24 (`2324`)
- Match Type:
  - `All` (overall matches)
  - `Home` (home performance only)
  - `Away` (away performance only)

## Repository Structure

```
/rank/
├── rank_9293All.csv
├── rank_9293Home.csv
├── rank_9293Away.csv
├── ...
└── rank_2324All.csv
```

# season_dashboard.Rmd

## EPL Dashboard Overview

This dashboard, written in R using **RMarkdown + Flexdashboard + Plotly**, provides a visual summary of EPL standings for a given season and match type (All / Home / Away).

## How It Works

- CSV data is loaded directly from GitHub using the `params$season` and `params$type` values.
- If the dataset does not contain the `GD` (Goal Difference) column, it is automatically calculated as `GF - GA`.

## Dashboard Layout

The dashboard consists of two columns:

### Left Column: Full Standings Table

- Displays the full league table using `DT::datatable()`
- Supports pagination and horizontal scroll for better viewing

### Right Column: Visual Analytics

#### 1. **Top 5 Teams by Points**

- Bar chart showing the top 5 teams
- Each bar includes a tooltip with:
  - Win / Draw / Loss record
  - GF, GA, GD values
- Points are labeled outside the bar

#### 2. **Points vs Goal Difference**

- Scatter plot comparing `Points` vs `GD` for all teams
- Color gradient represents `Pos` (position):  
  - `darkorange` for higher rank (lower number)  
  - `skyblue` for lower rank (higher number)
- Interactive tooltips show team names and key stats

## Parameters Used

```yaml
params:
  season: "2223"
  type: "All"
```
