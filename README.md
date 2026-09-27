# UK Aviation Demand and Punctuality Analysis

An end-to-end data analysis and forecasting project examining UK airport passenger demand, operational punctuality and recovery between January 2015 and December 2025.

The project collects and cleans official UK Civil Aviation Authority (CAA) data, explores long-term and seasonal patterns, evaluates passenger-demand forecasting models, analyses airport punctuality and combines the results into an integrated airport scorecard.

## Project objectives

The analysis addresses five questions:

1. How did UK airport passenger demand change between 2015 and 2025?
2. How strongly did the pandemic disrupt demand, and which airports recovered most successfully?
3. Can monthly passenger demand be forecast accurately using interpretable time-series models?
4. How do UK airports compare on punctuality, delays and cancellations?
5. What operational and commercial insights emerge when passenger demand and punctuality are evaluated together?

## Data sources

The project uses monthly CSV files published by the UK Civil Aviation Authority:

- [UK airport data](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/airports/uk-airport-data/)
  - Table 09: Terminal and Transit Passengers
- [UK flight punctuality statistics](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/flight-punctuality/uk-flight-punctuality-statistics/)
  - Monthly Punctuality Matching Summary Analysis

The analysis covers January 2015 to December 2025.

Raw and generated data files are excluded from Git because they can be downloaded or reproduced by running the notebooks.

## Key findings

### Passenger demand

- UK airports handled **299.4 million terminal passengers in 2025**.
- Passenger demand was **0.9% above 2019**, indicating that the national market had recovered overall.
- Heathrow handled **84.5 million passengers**, representing **28.2%** of the 2025 market.
- The five largest airports accounted for approximately **69.1%** of passengers.
- August was the strongest seasonal month, with a seasonal index of **125.9**.
- January was the weakest, with an index of **75.0**.
- April 2020 was the lowest-demand month, with only **334,032 passengers**.

### Airport recovery

Recovery was uneven across airports:

- Bristol: **+20.9%** versus 2019
- Edinburgh: **+15.2%**
- Manchester: **+9.2%**
- Gatwick: **−8.2%**
- London City: **−27.0%**

### Forecasting

Two interpretable forecasting approaches were evaluated:

- Seasonal-naive forecasting
- Holt-Winters exponential smoothing

The seasonal-naive model was the best-performing model for **8 of 11 series**. Holt-Winters performed best for Manchester, Birmingham and Edinburgh.

For total UK passenger demand:

- Best model: **Seasonal naive**
- 2025 MAPE: **2.40%**

Annual backtesting showed that the seasonal-naive model performed well during stable operating periods but failed during the pandemic and early recovery:

| Operating period | Average MAPE |
|---|---:|
| Stable pre-pandemic | 4.39% |
| Disruption and recovery | 582.04% |
| Recent period | 4.67% |

This demonstrates that strong normal-period accuracy does not mean a model can predict structural shocks.

### Punctuality

In 2025:

- On-time flights: **72.7%**
- Average delay: **15.1 minutes**
- Cancellation rate: **1.04%**

Compared with 2019:

- The on-time rate was **2.3 percentage points lower**.
- Average delay was **1.1 minutes higher**.

Liverpool recorded the strongest 2025 on-time performance at **80.9%**, while Manchester recorded the lowest at **64.5%**.

During normal operating years, punctuality showed a strong seasonal pattern:

- July had the weakest performance: **62.7% on time** and **21.6 minutes average delay**.
- November had the strongest performance: **80.0% on time** and **11.2 minutes average delay**.

### Demand and operational performance

Excluding the disruption and early-recovery years of 2020–2022:

- Passenger demand and on-time performance had a correlation of **−0.635**.
- Passenger demand and average delay had a correlation of **+0.585**.

These relationships indicate that higher passenger volumes are associated with greater operational pressure, although correlation does not establish causation.

The integrated airport analysis identified four performance groups:

| Performance group | Airports | 2025 passengers | Average on-time rate |
|---|---:|---:|---:|
| Growth with operational pressure | 7 | 110.1 million | 69.0% |
| Resilient growth | 5 | 101.5 million | 76.6% |
| Demand and operational pressure | 2 | 43.7 million | 71.0% |
| Demand recovery opportunity | 9 | 40.5 million | 76.1% |

## Business implications

- Airports should protect operational capacity during the summer peak, particularly from June to September.
- Airports experiencing growth alongside weak punctuality require targeted operational improvement.
- Practices used by airports achieving both growth and strong punctuality may offer useful benchmarks.
- Seasonal-naive forecasts provide a strong and transparent baseline, while model selection should remain airport-specific.
- Forecasts should be supplemented with scenario analysis because statistical models trained on historical patterns cannot anticipate unprecedented shocks.

## Methodology

The project applies:

- Automated web-page parsing and CSV collection
- Data cleaning and schema standardisation
- Validation and data-quality testing
- Exploratory data analysis
- Weighted national punctuality calculations
- Seasonal-index analysis
- Market-share and airport-concentration analysis
- Seasonal-naive forecasting
- Holt-Winters exponential smoothing
- Holdout testing and annual backtesting
- MAE, RMSE and MAPE model evaluation
- Correlation analysis
- Integrated airport-performance segmentation
- Data visualisation with Matplotlib and Seaborn

## Notebook guide

| Notebook | Purpose |
|---|---|
| `01_data_collection_and_validation.ipynb` | Downloads, cleans, standardises and validates monthly CAA passenger data. |
| `02_exploratory_airport_analysis.ipynb` | Analyses demand trends, airport rankings, market concentration, seasonality and recovery. |
| `03_passenger_demand_forecasting.ipynb` | Builds and evaluates seasonal-naive and Holt-Winters passenger forecasts. |
| `04_punctuality_and_delay_analysis.ipynb` | Collects and analyses punctuality, delay and cancellation data. |
| `05_integrated_evaluation_and_business_insights.ipynb` | Combines demand, forecasting and punctuality results into an executive scorecard and business insights. |

## Repository structure

```text
uk-aviation-demand-punctuality/
├── data/
│   ├── raw/                  # Downloaded source files (not tracked)
│   ├── interim/              # Cleaned intermediate datasets (not tracked)
│   └── processed/            # Final analytical outputs (not tracked)
├── notebooks/
│   ├── 01_data_collection_and_validation.ipynb
│   ├── 02_exploratory_airport_analysis.ipynb
│   ├── 03_passenger_demand_forecasting.ipynb
│   ├── 04_punctuality_and_delay_analysis.ipynb
│   └── 05_integrated_evaluation_and_business_insights.ipynb
├── reports/
│   └── figures/              # Exported charts when required
├── sql/                      # Reserved for future SQL analysis
├── .gitignore
├── README.md
└── requirements.txt
```

## Installation

Clone the repository:

```bash
git clone https://github.com/DafyddFuture/uk-aviation-demand-punctuality.git
cd uk-aviation-demand-punctuality
```

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Start JupyterLab:

```bash
jupyter lab
```

## Reproducing the analysis

Run the notebooks in numerical order, beginning with Notebook 01.

Each notebook creates the datasets required by later notebooks. The `data/raw`, `data/interim` and `data/processed` files are deliberately excluded from version control.

An internet connection is required when running the data-collection notebooks.

## Limitations

- The analysis uses airport-level monthly aggregates rather than individual flight records.
- Relationships between demand and punctuality are correlations and should not be interpreted as proof of causation.
- Weather, staffing, air-traffic restrictions and airline-specific operating factors are not modelled directly.
- Passenger and punctuality datasets have different airport-reporting coverage.
- Isle of Man and Jersey appear in the punctuality data but are outside the matched UK passenger scorecard.
- Consistent cancellation measures are available only from 2018.
- The performance groups are screening categories, not causal classifications.
- Historical time-series models cannot anticipate unprecedented shocks such as the COVID-19 pandemic.

## Technology

- Python
- pandas
- NumPy
- Requests
- Beautiful Soup
- Matplotlib
- Seaborn
- statsmodels
- scikit-learn
- JupyterLab

## Author

**Dafydd Jones**

Finance and data analytics professional developing portfolio projects that combine commercial analysis, forecasting and operational insight.