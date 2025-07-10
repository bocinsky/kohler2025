[![Last-updated](https://img.shields.io/badge/last%20update-July%202025-brightgreen.svg)](https://github.com/bocinsky/kohler2025)
[![License](https://img.shields.io/github/license/mashape/apistatus.svg)](http://choosealicense.com/licenses/mit/)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/bocinsky/kohler2025/main?urlpath=rstudio)

## Research compendium package for Kohler, Brumbaugh, and Bocinsky (2025)

This R-based research compendium supports an analysis of climate variability and its impact on ancestral Pueblo demography in the Chaco Regional System. It draws on high-resolution paleoclimate reconstructions and spatial regional boundaries to estimate the frequency and duration of agricultural potential over time, and their relationship to the demography of the region.

### Overview

The main script is [`kohler2025.qmd`](kohler2025.qmd) and output is written to [`kohler2025.html`](kohler2025.html). This is a Quarto markdown document that includes code to perform all analyses reported in the manuscript, as well as text descriptions of those analyses.

[`kohler2025.qmd`](kohler2025.qmd) performs the following steps:

1. **Load spatial boundaries** for Chaco and Mesa Verde subregions from GeoJSON.
2. **Access paleoclimatic precipitation reconstructions**, either from Amazon S3.
3. **Extract seasonal climate summaries** (e.g., water-year precipitation, summer growing degree days) for each region and year.
4. **Compute sliding window niche statistics**, identifying consecutive years of shortfall.
5. **Model pre-European net primary productivity** using the LightGBM framework.
6. **Export all figures tables** included in the 

_Note_: The script uses `AWS_NO_SIGN_REQUEST = "YES"` to access public climate datasets hosted on S3.

### 🗂 Directory Structure

- `kohler2025.qmd`: Performs all analyses and produces data, tables, and figures
- `data-raw/`: Directory containing un-processed datasets used in the analysis. Not archived on Github, as many of these data are quite large.
- `data-derived/`: Directory containing processed datasets created in the analysis.
- `figures/`: Directory containing figures used in the manuscript.
- `tables/`: Directory containing tabular data used in the manuscript.
- `README.Rmd`: This README file, providing an overview and usage
  instructions.

### Citation

**When using the code included in this research compendium, please cite *all* of the following:**

> Kohler, Timothy A., Laura E. Brumbaugh, and R. Kyle Bocinsky. How Many People lived in the Chaco Regional System, and Why It Matters. KIVA, In review.

> Kohler, Timothy A., Laura E. Brumbaugh, and R. Kyle Bocinsky. Research compendium for: *How Many People lived in the Chaco Regional System, and Why It Matters*, 2025. Version 1.0.0. Zenodo. [DOI]

## Requirements

This analysis requires R (≥ 4.2.0) and the following packages:

- `pak`
- `magrittr`
- `tidyverse`
- `fs`
- `sf`
- `terra`
- `paletteer`
- `tidyterra`
- `sbtools`
- `exactextractr`
- `openxlsx`
- `slider`
- `lightgbm`
- `furrr`
- `ragg`

Ensure GDAL and PROJ are properly configured to support spatial operations with `sf` and `terra`.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
