# Central and Eastern Europe agriculture climate analysis

This repository contains data and code supporting a Reuters analysis of June and
July temperatures in Hungary, Romania and Poland.

Published September 2, 2026: [Climate shocks hit EU maize heartland in Hungary,
Romania](https://www.reuters.com/business/environment/climate-shocks-hit-eu-maize-heartland-hungary-romania-2026-09-02/).

![The top of the story](https://raw.githubusercontent.com/palewire/cee-agriculture-climate-analysis/refs/heads/main/top.png)
![The chart we made](https://raw.githubusercontent.com/palewire/cee-agriculture-climate-analysis/refs/heads/main/chart.png)

## Finding

"Over the past decade, Hungary's June and July highs have exceeded the 1961 to 1990 average by ​3.1 degrees Celsius (5.6 degrees Fahrenheit), according to [Reuters Climate Monitor](https://www.reuters.com/graphics/CLIMATE-AUTOMATED/MONITOR/akpeykqqapr/) data. Romania is close behind, with average summer highs 3 C (5.4 F) above historical norms."

## Data and method

The underlying data are [ERA5](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview) reanalysis estimates produced by the [Reuters
Climate Monitor](https://www.reuters.com/graphics/CLIMATE-AUTOMATED/MONITOR/akpeykqqapr/).

The notebook downloads daily area-weighted country averages from the private Reuters dataset at `analysis/daily-country-averages/era5.parquet`. It averages `t2m_max` from June
1 through July 31 for each country and year, then subtracts that country's
1961–1990 average for the same 61 calendar days.

## Reproduce

Install [uv](https://docs.astral.sh/uv/), then run:

```sh
uv sync
export S3_BUCKET_NAME="your-authorized-bucket"
uv run jupyter lab analysis.ipynb
```

The source data are private. Running the notebook requires authorized AWS
access through standard AWS credentials and the `S3_BUCKET_NAME` environment
variable. The notebook writes its annual values to `pivot.csv`, which is
included in this repository as a transparent analysis output.
