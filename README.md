Housing Price Analysis in Dijon (France)

Using Official DVF Transaction Data (2024)

1. Project Objective

The objective of this project is to analyze and model residential housing prices in Dijon, France, using real transaction data provided by the French government (DVF – Demande de Valeurs Foncières).

The study focuses on identifying the main drivers of housing prices and evaluating the performance of different regression models under realistic data constraints.

This project is designed as an applied data science exercise, emphasizing data quality, methodological rigor, and honest interpretation, rather than metric maximization.

2. Data Source and Scope
Data Source

DVF (Demande de Valeurs Foncières)

Official public dataset published by the French government

Covers real real-estate transactions recorded by notaries

Temporal and Spatial Scope

Year: 2024

Location: Dijon (single city)

Property types:

Houses (Maison)

Apartments (Appartement)

The analysis is therefore cross-sectional, not temporal.

3. Data Preparation and Filtering
3.1 Initial Dataset

The raw DVF file contains:

Over 3.4 million rows

More than 40 columns

Multiple transaction types and property categories

3.2 Filtering Strategy

To ensure analytical relevance, the dataset was filtered to retain only:

Transactions located in Dijon

Residential properties (Maison and Appartement)

Standard market transactions (Nature mutation = "Vente")

This step removes non-market mechanisms such as auctions or administrative transfers that could distort price dynamics.

4. Feature Selection and Cleaning
4.1 Selected Variables

From the full dataset, only economically meaningful variables were retained:

Transaction value (Valeur fonciere)

Built surface (Surface reelle bati)

Number of main rooms

Property type

Transaction date

Postal code (used as a proxy for location)

4.2 Data Cleaning

The following cleaning steps were applied:

Removal of missing values

Conversion of monetary values from string to numeric format

Removal of unrealistic observations:

Extremely low or high prices

Implausible surface areas

After cleaning, the final dataset contained approximately 3,000 observations, which is consistent with the size of a local urban housing market.

5. Feature Engineering

Several additional variables were engineered to improve model performance and interpretability:

Binary encoding of property type
(Maison = 1, Appartement = 0)

Logarithmic transformation of price
Used to reduce skewness and stabilize variance

Price per square meter
Introduced to decouple price effects from property size

Postal code encoding
Implemented using one-hot encoding to partially capture locational effects

These transformations reflect standard practices in real-estate economics and applied machine learning.

6. Exploratory Data Analysis (EDA)

EDA revealed several important characteristics of the Dijon housing market:

Housing prices exhibit strong right-skewness, justifying log transformation.

A clear positive relationship exists between price and surface area.

Significant dispersion remains for properties with similar surface areas, indicating the presence of unobserved factors such as location and quality.

These findings already suggested that purely linear models would have limited explanatory power.

7. Modeling Strategy
7.1 Linear Regression (Baseline)

Linear regression was used as an interpretable baseline model.

Purpose:

Understand directional relationships

Establish a reference level of explanatory power

Results:

R² ≈ 0.39

Indicates that surface area is the dominant explanatory variable

This result is realistic given the absence of detailed spatial and qualitative features.

7.2 Random Forest Regressor

A Random Forest model was then implemented to capture non-linear patterns.

Advantages:

Handles interactions and non-linearities

Robust to outliers

Provides feature importance measures

Observations:

Surface area remains the most informative feature

Location (postal code) contributes meaningfully to prediction

Model performance improves compared to the linear baseline

Feature importance was interpreted as predictive contribution, not causal impact.

8. Model Evaluation

Model performance was evaluated using:

R² (explained variance)

RMSE (prediction error on log-scale)

Results were interpreted cautiously:

Moderate R² values were expected and considered appropriate

Overly high metrics would likely indicate leakage or overfitting

The emphasis was placed on model validity and transparency, not on achieving artificially high scores.

9. Key Findings

Housing prices in Dijon are primarily driven by surface area

Property type and location have secondary but meaningful effects

A large share of price variation remains unexplained due to omitted qualitative and spatial variables

These findings align with both economic intuition and empirical real-estate literature.

10. Limitations

This study has several acknowledged limitations:

Single-year analysis
No temporal dynamics can be inferred.

Limited spatial resolution
Postal codes are an imperfect proxy for neighborhood effects.

Absence of qualitative attributes
Property condition, age, floor level, and amenities are not available.

Cross-sectional design
Results describe associations, not causal relationships.

These limitations are intrinsic to the data and explicitly considered in interpretation.

11. Conclusion

This project demonstrates a complete and realistic data science workflow applied to real housing market data. While the models do not fully explain price variation, they provide meaningful insights into the structure of the Dijon real-estate market.

More importantly, the project prioritizes methodological correctness, honest evaluation, and economic interpretability, making it suitable as a foundation for further academic or professional work.

Final Remark

Rather than maximizing metrics, this project focuses on doing the right analysis with the available data, which is a core competency expected from a developing data scientist.