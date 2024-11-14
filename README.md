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

Access to Population Dynamics Embeddings is subject to Google’s Terms of Service. Users can download the embeddings and associated files after completing the intake form.

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

- **Nowcasting**: Predict outcomes for counties using partial data.
- **Superresolution and Imputation**: Train a model at the county level to predict at the ZIP code level, demonstrating imputation capabilities.
- **Forecasting with TimeSFM**: Use TimeSFM to perform predictive forecasting.
- **Nighttime Lights Prediction with Earth Engine**: Integrate Earth Engine data, like nighttime lights, with the embeddings for environmental and socioeconomic forecasting.

## Benchmarks

Benchmark files include ground truth data for evaluating PDFM Embeddings across prediction tasks.

- **Interpolation, Superresolution, and Extrapolation**: `conus27` file supports tasks involving spatial interpolation, superresolution, and extrapolation.
- **Forecasting**: Two datasets for temporal forecasting:
  - `county_unemployment.csv`: Monthly county-level unemployment data (1990-2024).
  - `zcta_poverty.csv`: Annual poverty estimates at the ZCTA level (2011-2022).

All ground truth data is gathered from publicly available sources, including Data Commons and Google Earth Engine.

### Data Sources

- **Health Variables**: CDC PLACES 2022
- **Unemployment**: bls.gov
- **Poverty**: census.gov
- **ZCTA and County Boundaries**: TIGER data
- **Tree Cover**: ESA/WorldCover
- **Night Lights**: NOAA VIIRS
- **Elevation**: USGS SRTM

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
