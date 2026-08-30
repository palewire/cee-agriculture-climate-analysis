# Central and Eastern Europe agriculture climate analysis

This repository contains the data and notebook behind a Reuters analysis of
June and July temperatures in Hungary, Romania and Poland.

## Finding

From 2017 through 2026, average daily highs in June and July were **3.1°C
(5.6°F) above the 1961–1990 normal in Hungary** and **3.0°C (5.4°F) above
normal in Romania**.

## Data and method

`data/annual-june-july-tmax-anomalies.csv` contains one value per country and
year. Each value is the average daily maximum temperature from June 1 through
July 31, less that country's average over the same 61 calendar days in
1961–1990. June therefore contributes 30 days and July 31 days.

The underlying data are ERA5 reanalysis estimates produced by the Reuters
Climate Monitor. They describe area-weighted country averages, not weather
station observations. This analysis does not measure rainfall, soil moisture,
crop yields, planted area or the causes of agricultural change.

## Reproduce

Install [uv](https://docs.astral.sh/uv/), then run:

```sh
uv sync
uv run jupyter lab analysis.ipynb
```

The notebook reads the committed CSV, recreates the decade averages and shows
the annual series. It needs no credentials or external download.

## Files

- `analysis.ipynb` — analysis and chart.
- `data/annual-june-july-tmax-anomalies.csv` — annual June–July anomalies,
  1961–2026.
- `pyproject.toml` and `uv.lock` — pinned Python environment.

## License

MIT. See [LICENSE](LICENSE).
