# project-22

# Country Statistics and Machine Learning Analysis

## Project Overview

This project analyzes country-level demographic, geographic, economic, and development indicators using machine learning and clustering techniques.

The analysis investigates how variables such as population, population density, internet usage, fertility, mortality, human development, and external debt are related across countries. Multiple supervised learning models are compared for prediction tasks, while unsupervised learning is used to identify broader country development profiles.

The project emphasizes not only predictive performance but also model interpretation, feature importance, clustering structure, and the limitations of country-level data.

---

## Dataset

The dataset contains country-level observations covering geographic, demographic, development, and economic characteristics.

Key variables include:

- Country name
- Total area
- Land area
- Inland water area
- Percentage of water
- Population
- Percentage of world population
- Population density
- Human Development Index (HDI)
- Fertility rate
- Mortality rate
- Percentage of internet users
- External debt

Each observation represents one country.

---

## Research Questions

### RQ1 — Human Development

**Can country-level demographic, geographic, technological, and economic indicators predict Human Development Index (HDI)?**

Regression models are compared to evaluate how well the available country characteristics explain differences in human development.

Permutation feature importance is used to identify the variables that contribute most strongly to prediction.

---

### RQ2 — Fertility Rate

**Can country characteristics predict fertility rate?**

This analysis examines whether development, internet access, mortality, population characteristics, and other country-level indicators contain useful information for predicting fertility patterns.

Multiple regression models are evaluated and compared.

---

### RQ3 — Mortality Rate

**How well can the available country-level indicators predict mortality rate?**

This research question intentionally evaluates whether the dataset contains sufficient information to explain cross-country differences in mortality.

The analysis also considers whether important determinants of mortality may be missing from the available dataset.

---

### RQ4 — External Debt

**Can demographic and development indicators predict a country's external debt?**

External debt is highly skewed across countries, so logarithmic transformation is incorporated into the modeling process.

The analysis evaluates whether development, population, internet access, demographic characteristics, and geographic variables can help explain differences in debt magnitude.

---

### RQ5 — Country Development Profiles

**Do countries form distinct profiles based on demographic, development, technological, and economic characteristics?**

K-Means clustering is used to identify groups of countries with similar characteristics.

Candidate solutions with three, four, and five clusters are evaluated using:

- Elbow Method
- Silhouette Score
- Cluster interpretability

The final clustering solution is selected by considering both statistical evidence and the interpretability of the resulting country profiles.

Principal Component Analysis (PCA) is used to visualize the clusters in two dimensions.

---

## Data Preparation

The project includes several preprocessing steps before modeling.

These include:

- Cleaning numeric variables
- Converting external debt into a usable numeric format
- Handling missing values using median imputation
- Applying logarithmic transformations to highly skewed variables when appropriate
- Standardizing features for K-Means clustering
- Separating predictors and target variables for each research question

Preprocessing is performed within the modeling workflow where appropriate to reduce the risk of data leakage.

---

## Machine Learning Models

Three regression algorithms are compared for the supervised research questions:

### Ridge Regression

Ridge Regression provides a regularized linear baseline and helps evaluate whether relationships between predictors and target variables can be adequately represented using a linear model.

### Random Forest

Random Forest is an ensemble tree-based method capable of modeling nonlinear relationships and interactions between variables.

### Extra Trees

Extra Trees is another ensemble tree-based method that introduces additional randomness during tree construction. This can improve generalization when relationships among variables are complex and nonlinear.

Model selection is based primarily on cross-validated Mean Absolute Error (MAE), with RMSE and R² also reported for additional evaluation.

---

## Model Evaluation

Regression models are evaluated using:

- **MAE (Mean Absolute Error)** — Measures the average magnitude of prediction errors.
- **RMSE (Root Mean Squared Error)** — Gives greater weight to large prediction errors.
- **R² (Coefficient of Determination)** — Measures the proportion of target variation explained by the model.

Cross-validation is used to provide a more reliable estimate of model performance than a single train-test split.

Actual-versus-predicted plots are also used to visually evaluate prediction quality and identify systematic prediction errors.

---

## Feature Importance

Permutation Feature Importance is used for the selected tree-based models.

This method evaluates how much model performance decreases when the values of a feature are randomly shuffled.

Feature importance is interpreted as **predictive importance rather than causal influence**. A highly important variable may contain useful information about the target without directly causing changes in that target.

Special caution is also required when predictors are strongly correlated because their predictive importance may overlap.

---

## Clustering Analysis

K-Means clustering is used to investigate whether countries naturally form broader statistical profiles.

The clustering analysis includes variables representing:

- Population characteristics
- Population density
- Human development
- Fertility
- Mortality
- Internet usage
- External debt
- Geographic characteristics

Highly skewed variables are transformed before clustering, and all clustering features are standardized so that variables measured on different scales can contribute more comparably.

The Elbow Method and Silhouette Score are used together to evaluate alternative cluster solutions.

---

## PCA Visualization

Principal Component Analysis (PCA) is used only for visualization of the clustering results.

PCA reduces the standardized feature space to two principal components so that country clusters can be displayed on a two-dimensional plot.

The final K-Means model itself is fitted using the complete set of clustering features rather than only the two PCA components.

---

## Project Structure

```text
country-stats-project/
│
├── country_stats.csv
├── country_stats_project.qmd
├── README.md
└── outputs/