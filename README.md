# ✨ Population Dynamics Foundations (PD-Foundations) Embeddings

PD-Foundations embeddings are **condensed vector representations** designed to encapsulate the complex, multidimensional interactions among human behaviors, environmental factors, and local contexts at specific locations.

These embeddings capture patterns in aggregated data such as **search trends, busyness trends, and environmental conditions** (maps, air quality, temperature), providing a rich, location-specific snapshot of how populations engage with their surroundings. Aggregated over space and time, these embeddings ensure **privacy** while enabling nuanced spatial analysis and prediction for applications ranging from public health to socioeconomic modeling.

-----

## 📝 Overview

PD-Foundations embeddings are generated using a **Graph Neural Network (GNN) model**, trained on a rich set of features:

  * **Aggregated Search Trends:** Regional interests and concerns reflected in search data.
  * **Aggregated Maps Data:** Geospatial and contextual data about locations.
  * **Aggregated Busyness:** Activity levels in specific areas, indicating density and frequency of human presence.
  * **Aggregated Weather and Air Quality:** Climate-related metrics, including temperature and air quality.

These features are aggregated at specific **spatial resolutions** (i.e., postal code, county, etc.) to generate localized, context-aware embeddings that preserve privacy. Embeddings are available for **17+ countries**, with more countries coming soon.

-----

## 📄 Paper

For more information on PD-Foundations embeddings, please see our [paper on arXiv](https://arxiv.org/abs/2411.07207), the [Earth AI Tech Report](http://goo.gle/earthai-techreport), this [YouTube video](https://www.youtube.com/watch?v=ZxmB8Z5i1Ls), and [ai.google/earth-ai](ai.google/earth-ai)

-----

## 🎯 Applications

PD-Foundations embeddings can be applied to a wide range of geospatial prediction tasks, similar to census and socioeconomic statistics. Example use cases include:

  * **Population Health Outcomes:** Predicting health statistics like disease prevalence or population health risks.
  * **Socioeconomic Factors:** Modeling economic indicators and living conditions.
  * **Retail:** Identifying promising locations for new stores, market expansion, and demand forecasting.
  * **Marketing and Sales:** Characterizing high-performance regions and identifying similar areas to optimize marketing and sales efforts.

By incorporating spatial relationships and diverse feature types, these embeddings serve as a powerful tool for geospatial predictions.

-----

## 🔓 Getting Access to the Embeddings

Embeddings for **17+ countries** (at varying spatial resolutions) are available for **research use** (subject to approval) at no cost and will be made available for **commercial and public sector use** via a paid Early Access Program.

Approved users can access the embeddings dataset via a **BigQuery Listing**. Use [this form](https://www.google.com/search?q=https://docs.google.com/forms/d/e/1FAIpQLSc6i5wQ4u-1_uF3R8sB8s6r8R7p8p9q8n8S8d7Q/viewform) to apply for research access or to join the Early Access Program waitlist.

> **Note:** Access to PD-Foundations embeddings is subject to Google’s [Terms of Service](https://policies.google.com/terms).

-----

## 🛠️ Using the Embeddings

### Prepare Ground Truth Data

To use PD-Foundations embeddings, prepare ground truth data (e.g., target variable for prediction tasks like asthma prevalence) at the **postal code or county level**.

### Option 1: Incorporate Embeddings into an Existing Model

  * **Prepare Existing Model-Based Ground Truth:** Use the embeddings as **geospatial covariates** to enhance an existing model.
  * **Train an Adapter Model:** Improve an existing model by integrating the embeddings.

### Option 2: Tune for Specific Use Cases

  * **Choose a Prediction Model:** Any model, such as GBDT, MLP, or linear, can be used for predictions.
  * **Use Embeddings for Prediction:** Use PD-Foundations embeddings as input features, alongside other contextual data, to improve prediction accuracy.

-----

## 📚 Demos / Notebooks

Explore our demo notebooks to understand various use cases of PD-Foundations embeddings. The code provided is available under the **Apache 2.0 license**.

| Notebook | Description |
| :--- | :--- |
| **Nowcasting Colab** | Uses past and partial present-day data for a county-level target variable to predict outcomes for remaining counties. |
| **Superresolution and Imputation Colab** | Helps train a model at the county level on a target variable to predict at the zip code level. Also demonstrates imputation (training on 20% of zip codes and predicting for the remaining 80%). |
| **Forecasting with TimesFM Colab** | An experimental use case incorporating **TimesFM** (a Univariate Forecasting Model) to perform spatiotemporal forecasting, where embeddings adjust for forecast errors and improve accuracy. |
| **Nighttime Lights Prediction with Earth Engine Colab** | Illustrates how Earth Engine data, such as nighttime lights, can also be predicted from the embeddings, enhancing geospatial understanding for environmental and socioeconomic forecasting. |

-----

## 📊 Benchmarks

The following benchmark files contain ground truth data used to evaluate PD-Foundations embeddings. They can be used alongside the embeddings to reproduce our results and assess performance.

### Interpolation, Superresolution, and Extrapolation

  * **`conus27` file:** A versatile dataset supporting tasks involving interpolation (filling gaps), superresolution (predicting at finer spatial scales), and extrapolation (projecting data over large missing regions). This file includes detailed columns for location information (place, county, state, latitude, longitude) and key population health indicators, along with geographic features such as tree cover, elevation, and nighttime lights.

### Forecasting

The model's capabilities in temporal forecasting are illustrated with two datasets:

  * **`county_unemployment.csv`:** Contains county-level unemployment data over a monthly timespan from 1990 to 2024, enabling users to track employment trends over time.
  * **`zcta_poverty.csv`:** Offers annual poverty estimates at the ZIP Code Tabulation Area (ZCTA) level from 2011 to 2022, providing insight into socioeconomic changes at finer spatial scales.

### Data Sources

All ground truth data included in the benchmarks are gathered from publicly available sources, through the **Data Commons** and **Google Earth Engine APIs**.

**Data Commons sources**

  * Health variables: CDC PLACES 2022
  * Unemployment: bls.gov
  * Poverty: census.gov

**Google Earth Engine sources**

  * ZCTA and County boundaries: TIGER/2010/ZCTA5, TIGER/2016/Counties
  * Tree cover: ESA/WorldCover/v100
  * Night lights: NOAA/VIIRS/DNB/ANNUAL\_V22
  * Elevation: USGS/SRTMGL1\_003
  * 2020 ZCTA to County relationship file

-----

## 🖋️ Citation

Please cite Population Dynamics Foundations as follows:

```
@article{agarwal2024pdfm,
  title={General Geospatial Inference with a Population Dynamics Foundation Model},
  author={Mohit Agarwal, Mimi Sun, Chaitanya Kamath, Arbaaz Muslim, Prithul Sarker, Joydeep Paul, Hector Yee, Marcin Sieniek, Kim Jablonski, Yael Mayer, David Fork, Sheila de Guia, Jamie McPike, Adam Boulanger, Tomer Shekel, David Schottlander, Yao Xiao, Manjit Chakravarthy Manukonda, Yun Liu, Neslihan Bulut, Sami Abu-el-haija, Arno Eigenwillig, Parth Kothari, Bryan Perozzi, Monica Bharel, Von Nguyen, Luke Barrington, Niv Efron, Yossi Matias, Greg Corrado, Krish Eswaran, Shruthi Prabhakara, Shravya Shetty, Gautam Prasad},
  journal={arXiv preprint arXiv:2411.07207},
  year={2024}
}
```

-----

## 📧 Contact

For questions, please email **pdfm-embeddings@google.com**.

