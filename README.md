# UK Aviation Demand and Punctuality Analysis

This project analyses passenger demand and flight punctuality across major UK airports using official data published by the UK Civil Aviation Authority.

## Objectives

- Collect and validate monthly UK aviation data
- Compare passenger demand across airports
- Examine seasonality, long-term trends and unusual periods
- Analyse flight delays and punctuality
- Build and evaluate passenger-demand forecasts
- Store prepared analytical data in a SQL database
- Present the findings through clear charts, tables and conclusions

## Business questions

1. How have passenger volumes changed across major UK airports?
2. Which airports experienced the strongest recovery after the COVID-19 disruption?
3. What seasonal patterns appear in passenger demand?
4. Which airports and airlines experience the greatest delays?
5. Can future monthly passenger demand be forecast accurately?
6. What operational and commercial insights can be drawn from the results?

## Planned notebooks

1. `01_data_collection_and_validation.ipynb`
2. `02_exploratory_airport_analysis.ipynb`
3. `03_passenger_demand_forecasting.ipynb`
4. `04_punctuality_and_delay_analysis.ipynb`
5. `05_model_evaluation_and_business_insights.ipynb`

## Methods

- Data collection and validation
- Exploratory data analysis
- SQL data storage and querying
- Time-series decomposition
- Baseline forecasting
- Exponential-smoothing forecasting
- Forecast evaluation
- Delay and punctuality analysis
- Interactive visualisation

## Data source

The project uses official airport and flight-punctuality statistics published by the UK Civil Aviation Authority:

- [UK airport data](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/airports/uk-airport-data/)
- [UK flight-punctuality statistics](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/flight-punctuality/uk-flight-punctuality-statistics/)

## Project structure

```text
data/
├── raw/
├── interim/
└── processed/
notebooks/
sql/
reports/
└── figures/
