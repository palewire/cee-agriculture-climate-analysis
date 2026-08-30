# Central and Eastern Europe agriculture climate analysis

This repository contains the notebook behind a Reuters analysis of June and
July temperatures in Hungary, Romania and Poland.

## Finding

From 2017 through 2026, average daily highs in June and July were **3.1°C
(5.6°F) above the 1961–1990 normal in Hungary** and **3.0°C (5.4°F) above
normal in Romania**.

## Data and method

The notebook downloads daily country averages from the private Reuters Climate
Monitor dataset at
`analysis/daily-country-averages/era5.parquet`. It averages `t2m_max` from June
1 through July 31 for each country and year, then subtracts that country's
1961–1990 average for the same 61 calendar days. June therefore contributes 30
days and July 31 days.

The underlying data are ERA5 reanalysis estimates produced by the Reuters
Climate Monitor. They describe area-weighted country averages, not weather
station observations. This analysis does not measure rainfall, soil moisture,
crop yields, planted area or the causes of agricultural change.

## Reproduce

Install [uv](https://docs.astral.sh/uv/), then run:

```sh
uv sync
export S3_BUCKET_NAME="your-authorized-bucket"
uv run jupyter lab analysis.ipynb
```

The source data are private. Running the notebook requires authorized AWS
access through standard AWS credentials and the `S3_BUCKET_NAME` environment
variable.

## Files

- `analysis.ipynb` — analysis and chart.
- `pyproject.toml` and `uv.lock` — pinned Python environment.

## License

MIT. See [LICENSE](LICENSE).
