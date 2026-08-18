# Predictive Modeling for the U.S. Second-Hand Car Market

A machine learning and market analytics project that predicts used-car selling prices, identifies the factors that drive resale value, and visualizes geographic sales patterns across the United States.

## Project Overview

The U.S. second-hand car market serves buyers, private sellers, dealerships, and online marketplaces, but pricing a vehicle accurately remains difficult. Vehicle condition, mileage, age, brand, specifications, and location can all affect market value.

This project combines exploratory data analysis, geographic visualization, feature engineering, and regression modeling to answer practical questions:

- What price should a buyer expect to pay for a used vehicle?
- How much could an owner reasonably sell a car for?
- Which vehicle characteristics have the greatest impact on price?
- Which states have the strongest used-car transaction activity?
- What types of vehicles may retain more resale value?

## Data

- **Source:** eBay Cars USA
- **Original dataset:** Approximately 160,000 sales records
- **Modeling dataset:** Approximately 60,000 cleaned records
- **Transaction period:** 2019-2020
- **Geographic coverage:** U.S. states and Washington, D.C.

Key fields include:

| Category | Variables |
| --- | --- |
| Transaction | Selling price, year sold, ZIP code, state |
| Vehicle | Make, model, model year, body type, drive type |
| Specifications | Engine, number of cylinders |
| Usage | Mileage and vehicle age |

## Workflow

1. Imported vehicle sales and ZIP-code reference data
2. Cleaned column names, invalid prices, missing values, and inconsistent categories
3. Converted ZIP codes into state-level geographic features
4. Explored price, mileage, age, brand, vehicle type, and regional patterns
5. Compared historical and modern vehicles, as well as luxury and non-luxury segments
6. Built preprocessing pipelines for numerical and categorical data
7. Evaluated seven regression algorithms using cross-validation
8. Tuned CatBoost and XGBoost with Halving Random Search
9. Analyzed feature importance and translated the results into market recommendations

## Data Preprocessing

The modeling pipeline applies:

- Frequent-value or constant imputation for categorical variables
- Iterative imputation for missing numerical values
- One-hot encoding for categorical features
- Standardization for numerical features
- Filtering of invalid and extreme selling prices
- Feature engineering for vehicle age and state

## Models Evaluated

| Model | Cross-validated RMSE |
| --- | ---: |
| Linear Regression | 8,799 |
| Decision Tree | 8,625 |
| Ridge Regression | 8,350 |
| Gradient Boosting | 7,863 |
| LightGBM | 6,948 |
| XGBoost | 6,833 |
| **CatBoost** | **6,822** |

After hyperparameter optimization:

| Tuned model | RMSE |
| --- | ---: |
| **CatBoost** | **6,395** |
| XGBoost | 6,497 |
| Baseline model | 11,866.67 |

The tuned CatBoost model delivered the strongest predictive performance, reducing RMSE by approximately **46%** relative to the baseline.

## Key Findings

### Price drivers

- Mileage had the strongest negative relationship with selling price: higher-mileage vehicles generally sold for less.
- Vehicle age affected price, but its observed influence was weaker than commonly assumed and lower than some specification variables such as cylinder count.
- Brand, model, vehicle condition, engine characteristics, and body type contributed to substantial price differences.
- Historical vehicles and newer vehicles followed different price distributions, supporting segmented analysis.

### Geographic patterns

- California had the largest number of transactions in the dataset.
- Florida and Michigan ranked second and third in sales volume.
- Pennsylvania, Texas, and New York also showed strong used-car market activity.
- Geographic demand patterns can help sellers and platforms target inventory and pricing strategies by state.

### Brand patterns

- Ford and Chevrolet had consistently high transaction volumes.
- Toyota performed particularly well among newer vehicles.
- Mercedes-Benz showed stronger activity in the historical-vehicle segment.

## Geographic Visualization

The project includes an interactive U.S. choropleth map showing used-car sales volume by state. The visualization makes it easy to compare regional market activity and identify high-volume locations.

Open `d3-cloropleth-map.html` in a browser to explore the map.

## Business Applications

- **Buyers:** Evaluate whether an asking price is consistent with comparable vehicles.
- **Sellers:** Estimate a competitive listing price and identify attractive markets.
- **Dealerships:** Support inventory acquisition, segmentation, and regional pricing.
- **Online platforms:** Improve automated valuation tools and market transparency.

## Technology

`Python` `Pandas` `NumPy` `scikit-learn` `CatBoost` `XGBoost` `LightGBM` `Plotly` `D3.js` 

## Repository Files

```text
├── test815.ipynb             # Data cleaning, EDA, modeling, and evaluation
├── d3-cloropleth-map.html    # Interactive state-level sales visualization
└── README.md                 # Project documentation
```

## Limitations and Future Work

The dataset does not fully capture vehicle-specific history such as VIN-level records, accidents, maintenance, ownership history, or local economic conditions. Future work could incorporate these variables, validate performance on newer transactions, create separate models for distinct market segments, and deploy the final pipeline as a consumer-facing price estimation application.


## Project Context

This project was completed for **BA815** in 2024. It demonstrates end-to-end data preparation, predictive modeling, hyperparameter optimization, feature interpretation, and interactive geographic visualization for a real-world pricing problem.
