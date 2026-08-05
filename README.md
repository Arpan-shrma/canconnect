# Toronto Gentrification Explorer

**[Landing Page →](https://arpan-shrma.github.io/canconnect/)**

An interactive spatial forecasting dashboard that tracks gentrification risk across
Toronto's 25 wards from 2023 through 2028, built to turn a static risk forecast into
something planners, researchers, or curious residents can actually explore — down to
the level of individual city blocks.

## What it does

The city is broken into roughly 500 spatial grid cells, each carrying a forecasted
gentrification risk score for every year in the horizon. The dashboard sits on top of
that data and lets you move between six different lenses on it:

- **Spatial Analysis** — a Leaflet map of every grid cell colored by risk level, with a
  year slider (and animation) so you can watch risk shift across the city over time,
  filterable down to a single ward.
- **Year-wise Changes** — rather than just showing risk levels, this tracks the *change*
  between each consecutive year (2023→2024, 2024→2025, …), classifying every grid cell
  into one of five categories from major decrease to major increase, mapped and ranked
  by magnitude.
- **Ward Analysis** — ranks all 25 wards by high-risk share, average risk score, or
  count of very-high-risk areas, alongside a velocity view showing which wards are
  changing fastest across the full six-year window.
- **Temporal Trends** — city-wide and ward-level trend lines with optional loess
  smoothing and change-point highlighting, with a multi-ward comparison for the five
  highest-risk areas.
- **Data Explorer** — the full underlying dataset (current risk or year-over-year
  changes), filterable by year, ward, and risk level, exportable as CSV.
- **Confidence tracking** — every prediction carries a model confidence score, so
  low-certainty forecasts aren't presented with the same weight as high-certainty ones.

## Why year-wise change tracking

Most risk dashboards show a snapshot: here's the risk level today. This one is built
around the idea that the *rate and direction of change* is usually more actionable than
the raw number — a ward with moderate risk that's climbing fast may need attention
sooner than one with high risk that's been flat for years. The year-wise change engine
computes that delta for every grid cell across every consecutive year pair and
classifies it by both direction and magnitude (small/medium/large), so patterns of
acceleration or improvement are visible at the grid level, not just city-wide.

## How it's built

- **Spatial layer**: grid cells and ward boundaries stored as `sf` geometries, joined
  to forecast data on a consistent grid ID
- **Ward assignment**: joined from a real ward-lookup table where available, with a
  coordinate-based fallback so the app still runs if that file is missing
- **Change detection**: `tidyr::pivot_wider` reshapes each consecutive year pair, then
  computes and categorizes the score delta per cell
- **Aggregation**: grid-level data rolls up into yearly city-wide stats and yearly
  ward-level stats — high-risk share, average score, confidence, very-high-risk counts
- **Interface**: a `shinydashboard` with six tabs, all wired to reactive filters so
  every map, chart, and table on a page updates together as you change year, ward, or
  metric

## Tech stack

R · Shiny · shinydashboard · leaflet · sf · dplyr / tidyr / purrr · ggplot2 · plotly ·
DT · viridis · shinyapps.io

## Data coverage

- 25 Toronto wards
- ~500 spatial grid cells
- 2023–2028 forecast horizon
- Risk scored 0–12, bucketed into Low / Moderate / High / Very High Risk

## Author

Built by **Arpan Sharma** — [LinkedIn](https://linkedin.com/in/arpan-shrma) ·
[GitHub](https://github.com/Arpan-shrma) · [Portfolio](https://datascientistarpan.com)
