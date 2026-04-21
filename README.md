\# Pixel-Level CO₂ Growth Rate Analysis

\### CAMS Satellite XCO₂ | Dynamic Linear Models | 2014–2024



\## Overview

End-to-end data science pipeline for extracting 

annual CO₂ growth rates from CAMS satellite 

XCO₂ observations at pixel level using 

Dynamic Linear Models (DLM).



\*\*Research Institution:\*\* University of Bremen  

\*\*Supervisor:\*\* Nasrin Mostafavi Pak  

\*\*Head of Programme:\*\* Prof. Fakhteh Ghanbarnejad  

\*\*Period:\*\* October 2024 – March 2026  



\---



\## Key Results

\- Global mean CO₂ growth rate: \*\*2.493 ppm/yr\*\*

\- \*\*64,800 global pixels\*\* analysed

\- Results consistent with Mauna Loa Observatory ✅

\- \*\*150x\*\* computation speedup using Dask parallel processing

\- Interactive year-slider web map (Climate TRACE style)



\---



\## Project Structure

```

co2-growth-rate-analysis/

├── test.ipynb               ← Data download + QC

├── test2.ipynb              ← DLM fitting + results

├── requirements.txt         ← Python dependencies

├── README.md                ← This file

└── .gitignore               ← Ignored files

```



\---



\## Installation



```bash

git clone https://github.com/dream-codee/co2-growth-rate-analysis

cd co2-growth-rate-analysis

pip install -r requirements.txt

```



\---



\## Data Source

\- \*\*Dataset:\*\* CAMS Global Greenhouse Gas Inversion  

\- \*\*Variable:\*\* XCO₂ (column-averaged CO₂ dry mole fraction)  

\- \*\*Access:\*\* https://ads.atmosphere.copernicus.eu  

\- \*\*Period:\*\* October 2014 – December 2024  

\- \*\*Resolution:\*\* 1° × 1°, 3-hourly (31,656 time steps)  

\- \*\*Total pixels:\*\* 180 × 360 = 64,800  



\---



\## Methodology

1\. Download CAMS XCO₂ data via `cdsapi` API

2\. Resample 3-hourly → weekly means (536 weeks/pixel)

3\. Apply Dynamic Linear Model per pixel using `dlmhelper`

4\. Extract annual CO₂ growth rates with uncertainty

5\. Scale to global domain using Dask parallel processing

6\. Visualise with interactive year-slider HTML map



\---



\## Pipeline Architecture

```

CAMS ADS API

&#x20;   ↓

cdsapi download (123 NetCDF files, 750MB+)

&#x20;   ↓

xarray load + 3-hourly → weekly resample

&#x20;   ↓

4-step Quality Control

&#x20;   ↓

dlmhelper DLM fit (per pixel)

&#x20;   ↓

Annual growth rate extraction + uncertainty

&#x20;   ↓

Dask parallel (15 workers, 150x speedup)

&#x20;   ↓

NetCDF output + CSV per pixel

&#x20;   ↓

Matplotlib/Cartopy static maps

&#x20;   ↓

Leaflet interactive year-slider HTML map

```



\---



\## Study Regions



| Region  | Latitude    | Longitude   | Pixels |

|---------|-------------|-------------|--------|

| India   | 6°N – 37°N  | 67°E – 97°E | \~930   |

| Germany | 47°N – 55°N | 6°E – 15°E  | \~72    |

| Global  | 90°S – 90°N | 180°W–180°E | 64,800 |



\---



\## Tech Stack

```

Python 3.13

xarray        — NetCDF loading

Dask          — Parallel processing

NumPy         — Array operations

pandas        — Time series resampling

Matplotlib    — Static visualisation

Cartopy       — Geographic maps

Folium        — Interactive maps

Leaflet.js    — Year-slider web map

dlmhelper     — Dynamic Linear Models

NetCDF4       — File format

cdsapi        — CAMS API client

imageio       — GIF generation

Pillow        — Image processing

```



\---



\## References

\- Agustí-Panareda et al. (2023) — CAMS GHG reanalysis. \*Atmos. Chem. Phys.\*, 23, 3829–3859. https://doi.org/10.5194/acp-23-3829-2023

\- Hachmeister, J. (2025) — dlmhelper. \*Zenodo\*. https://doi.org/10.5281/zenodo.14772372

\- Hachmeister et al. (2024) — DLM for methane. \*Atmos. Chem. Phys.\*, 24, 577–595.

\- Laine, M. (2020) — Dynamic Linear Models. \*Springer Geophysics\*.

\- Lan et al. (2025) — Mauna Loa CO₂ trends. NOAA GML.

\- Lee et al. (2023) — IPCC AR6 Synthesis Report.



\---



\## License

MIT License — free to use with attribution.



\---



\## Contact

\*\*Saba Minhaj\*\*  

MSc Computer Science — Big Data and AI  

SRH University of Applied Sciences Heidelberg  

Campus Leipzig



