# Montgomery County Crime EDA

This repository contains an exploratory data analysis (EDA) of crime incidents in **Montgomery County** for the years **2016‑2022**. The goal is to uncover temporal and spatial patterns in reported crimes, identify hotspots and trends, and produce clear visualisations to support public safety insights.

## Data

The dataset comprises more than **306 k records** of reported crime incidents provided by Montgomery County open data sources. Each record includes fields such as:

- **Incident date and time** (year, month, day, hour)
- **Crime category** and detailed description
- **Police district** and **zip code**
- **Latitude** and **longitude** coordinates

After loading the raw CSV data, missing values were handled and columns were normalised (e.g. consistent casing, trimmed whitespace). Additional features were engineered:

- **Temporal features:** year, month, day of week, hour of day
- **Spatial features:** groupings by police district and zip code; K‑means cluster labels based on geographical coordinates to identify hotspots

## Methods

The analysis was carried out in Python using Pandas for data manipulation and Matplotlib/Seaborn for visualisation. Key steps include:

1. **Data cleaning:** removed null or erroneous records, standardised categorical variables and created indices for grouping.
2. **Feature engineering:** added temporal variables to examine seasonality and daily patterns, and applied **K‑means clustering** (with K determined via the elbow method) to latitude‑longitude pairs to segment the county into hotspots.
3. **Visualisations:** produced roughly twenty plots, including:
   - Bar charts of crime counts by category, district and zip code
   - Heatmaps showing incidents by day of week vs hour of day
   - Line plots of monthly crime trends over the six‑year period
   - Geographic scatter plots highlighting clusters and high‑crime areas

## Results & Insights

The EDA revealed several notable patterns:

- **Pandemic dip:** Overall crime dropped sharply during the **COVID‑19 pandemic** in 2020, particularly between March and June. A gradual rebound was observed in subsequent years, though levels have not fully returned to pre‑pandemic highs.
- **Hotspots:** Burglaries and assaults were concentrated in specific police districts and zip codes. K‑means clustering highlighted a handful of geographic hotspots requiring targeted policing.
- **Temporal patterns:** Many offences peaked on **weekends** and during late evening hours. Seasonal analysis showed higher burglary rates in summer months and increased assaults during winter.
- **Crime mix:** Property crimes (theft, burglary) accounted for the majority of incidents, followed by assaults. Trends differ across districts, emphasising the need for localised strategies.

These findings can inform resource allocation, community outreach and further predictive modelling.

## Repository Structure

```
montgomery‑crime‑eda/
├── README.md     # Project overview and results
├── LICENSE       # MIT Licence
├── data/         # Scripts or notes on obtaining and cleaning the crime dataset
├── src/          # Python scripts/notebooks performing EDA and clustering
├── plots/        # Generated visualisations (PNG/CSV)
└── reports/      # Project report or presentation summarising the analysis
- The file `AP_Coursework1_Group_sanitized.zip` in the repository root contains the Montgomery County crime analysis report with personal information removed.
- The `ap_coursework-*.png` files are extracted figures from the report (e.g., top crime types bar chart, crime categories pie chart, total crimes per year line plot).
```

- The `src` directory contains Jupyter notebooks and scripts used to clean the data, compute statistics and produce plots.
- The `plots` folder holds exported figures illustrating trends and hotspots.
- The `reports` folder may include a written report or slide deck summarising the methodology and findings.

## Usage

To replicate the analysis or extend it:

1. **Clone** the repository:

   ```bash
   git clone https://github.com/Ayesha-code-arch/montgomery-crime-eda.git
   cd montgomery-crime-eda
   ```

2. **Install dependencies** (e.g. Pandas, NumPy, Scikit‑learn, Seaborn):

   ```bash
   pip install -r requirements.txt
   ```

3. **Run the EDA notebook or script**:

   ```bash
   jupyter notebook src/eda.ipynb
   # or
   python src/eda.py --input data/montgomery_crime.csv --output_dir plots/
   ```

   The script/notebook will load the raw data, perform cleaning and feature engineering, and save visualisations to the `plots/` directory.

## Licence

This project is distributed under the **MIT Licence**. See `LICENSE` for details.

## Acknowledgements

Crime data are provided by **Montgomery County Open Data** and are used here for educational purposes. Many thanks to the course instructors and peers for feedback on the analysis.
