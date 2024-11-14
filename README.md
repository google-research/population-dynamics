# Population Dynamics Foundation Model (PDFM) Embeddings

**PDFM Embeddings** are condensed vector representations designed to encapsulate the complex, multidimensional interactions among human behaviors, environmental factors, and local contexts at specific locations. These embeddings capture patterns in aggregated data such as search trends, busyness trends, and environmental conditions (maps, air quality, temperature), providing a rich, location-specific snapshot of how populations engage with their surroundings. Aggregated over space and time, these embeddings ensure privacy while enabling nuanced spatial analysis and prediction for applications ranging from public health to socioeconomic modeling.

## Overview

PDFM Embeddings are generated using a Graph Neural Network (GNN) model, trained on a rich set of features:
- **Aggregated Search Trends**: Regional interests and concerns reflected in search data.
- **Aggregated Maps Data**: Geospatial and contextual data about locations.
- **Aggregated Busyness**: Activity levels in specific areas, indicating density and frequency of human presence.
- **Aggregated Weather and Air Quality**: Climate-related metrics, including temperature and air quality.

These features are aggregated at the postal code and county levels to generate localized, context-aware embeddings that preserve privacy.

Embeddings are available for all counties and ZIP codes within the contiguous United States. For additional coverage, please reach out to [pdfm-embeddings@google.com](mailto:pdfm-embeddings@google.com).

## Paper

For more information on PDFM Embeddings, please see our [paper on arXiv](https://arxiv.org/abs/2411.07207).

## Applications

PDFM Embeddings can be applied to a wide range of geospatial prediction tasks, similar to census and socioeconomic statistics. Example use cases include:

- **Population Health Outcomes**: Predicting health statistics like disease prevalence or population health risks.
- **Socioeconomic Factors**: Modeling economic indicators and living conditions.
- **Retail**: Identifying promising locations for new stores, market expansion, and demand forecasting.
- **Marketing and Sales**: Characterizing high-performance regions and identifying similar areas to optimize marketing and sales efforts.

By incorporating spatial relationships and diverse feature types, these embeddings serve as a powerful tool for geospatial predictions.

## Getting Access to the Embeddings

Access to Population Dynamics Embeddings is subject to Google’s [Terms of Service](https://policies.google.com/terms). Users can download the embeddings and associated files after completing the [intake form](https://docs.google.com/forms/d/e/1FAIpQLSeZLIqTCIx1-OiBzUnqXZpu_k5M223ZvMmqwQhMZ_0TkaWhEQ/viewform?usp=dialog).

## Using the Embeddings

### Prepare Ground Truth Data
To use Population Dynamics Embeddings, prepare ground truth data (e.g., target variable for prediction tasks like asthma prevalence) at the postal code or county level.

### Option 1: Incorporate Embeddings into an Existing Model
1. **Prepare Existing Model-Based Ground Truth**: Use the embeddings as geospatial covariates to enhance an existing model.
2. **Train an Adapter Model**: Improve an existing model by integrating the embeddings.

### Option 2: Tune for Specific Use Cases
1. **Choose a Prediction Model**: Any model, such as GBDT, MLP, or linear, can be used for predictions.
2. **Use Embeddings for Prediction**: Use PDFM Embeddings as input features, alongside other contextual data, to improve prediction accuracy.

## Demos / Notebooks

Explore our demo notebooks to understand various use cases of PDFM Embeddings. The code provided is available under the Apache 2.0 license.

- **Nowcasting** [Colab](https://colab.sandbox.google.com/github/google-research/population-dynamics/blob/master/notebooks/pdfm_nowcasting.ipynb): Predict outcomes for counties using partial data.
- **Superresolution and Imputation** [Colab](https://colab.sandbox.google.com/github/google-research/population-dynamics/blob/master/notebooks/pdfm_superresolution_and_imputation.ipynb): Train a model at the county level to predict at the ZIP code level, demonstrating imputation capabilities.
- **Forecasting with TimesFM** [Colab](https://colab.sandbox.google.com/github/google-research/population-dynamics/blob/master/notebooks/pdfm_timesfm_forecasting_final.ipynb): Use TimeSFM to perform predictive forecasting.
- **Nighttime Lights Prediction with Earth Engine** [Colab](https://colab.sandbox.google.com/github/google-research/population-dynamics/blob/master/notebooks/pdfm_earth_engine.ipynb): Integrate Earth Engine data, like nighttime lights, with the embeddings for environmental and socioeconomic forecasting.

## Benchmarks

The following benchmark files contain ground truth data used to evaluate Population Dynamics Based Embeddings. They can be used alongside the embeddings to reproduce our results and assess performance across various geospatial and temporal prediction tasks..

- **Interpolation, Superresolution, and Extrapolation**: The conus27 file is a versatile dataset that supports tasks involving interpolation (filling gaps), superresolution (predicting at finer spatial scales), and extrapolation (projecting data over large missing regions). This file includes detailed columns for location information (place, county, state, latitude, longitude) and key population health indicators, along with geographic features such as tree cover, elevation, and nighttime lights.
- **Forecasting**: The model's capabilities in temporal forecasting are illustrated with two datasets:
  - `county_unemployment.csv`: Contains county-level unemployment data over a monthly timespan from 1990 to 2024, enabling users to track employment trends over time.
  - `zcta_poverty.csv`: This file offers annual poverty estimates at the ZIP Code Tabulation Area (ZCTA) level from 2011 to 2022, providing insight into socioeconomic changes at finer spatial scales.

All ground truth data included in the benchmarks are gathered from publicly available sources, through the Data Commons and Google Earth Engine APIs. Here's a list of the original sources:

- #### Data Commons sources 
  - Health variables: [CDC PLACES 2022](https://data.cdc.gov/500-Cities-Places/PLACES-ZCTA-Data-GIS-Friendly-Format-2022-release/c76y-7pzg/about_data) 
  - Unemployment: [bls.gov](http://bls.gov)
  - Poverty: [census.gov](https://www.census.gov/programs-surveys/acs/data/data-via-ftp.html)

- #### Google Earth Engine sources
  - ZCTA and County boundaries: [TIGER/2010/ZCTA5](https://developers.google.com/earth-engine/datasets/catalog/TIGER_2010_ZCTA5#terms-of-use), [TIGER/2016/Counties](https://developers.google.com/earth-engine/datasets/catalog/TIGER_2016_Counties)
  - Tree cover: [ESA/WorldCover/v100](https://developers.google.com/earth-engine/datasets/catalog/ESA_WorldCover_v100)
  - Night lights: [NOAA/VIIRS/DNB/ANNUAL_V22](https://developers.google.com/earth-engine/datasets/catalog/NOAA_VIIRS_DNB_ANNUAL_V22)
  - Elevation: [USGS/SRTMGL1_003](https://developers.google.com/earth-engine/datasets/catalog/USGS_SRTMGL1_003)
- [2020 ZCTA to County relationship file](https://www2.census.gov/geo/docs/maps-data/data/rel2020/zcta520/tab20_zcta520_county20_natl.txt)



## License & Contact

We release Population Dynamics Foundation Model Embeddings under the [Creative Commons Attribution 4.0 International (CC BY 4.0) license](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt this data, but please cite our work if you incorporate these embeddings in your research or applications.

```bibtex
@article{agarwal2024pdfm,
  title={General Geospatial Inference with a Population Dynamics Foundation Model},
  author={Mohit Agarwal, Mimi Sun, Chaitanya Kamath, Arbaaz Muslim, Prithul Sarker, Joydeep Paul, Hector Yee, Marcin Sieniek, Kim Jablonski, Yael Mayer, David Fork, Sheila de Guia, Jamie McPike, Adam Boulanger, Tomer Shekel, David Schottlander, Yao Xiao, Manjit Chakravarthy Manukonda, Yun Liu, Neslihan Bulut, Sami Abu-el-haija, Arno Eigenwillig, Parth Kothari, Bryan Perozzi, Monica Bharel, Von Nguyen, Luke Barrington, Niv Efron, Yossi Matias, Greg Corrado, Krish Eswaran, Shruthi Prabhakara, Shravya Shetty, Gautam Prasad},
  journal={arXiv preprint arXiv:2411.07207},
  year={2024}
}
```
For questions, please email pdfm-embeddings@google.com.
