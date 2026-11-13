# Amsterdam Airbnb Data Analysis

An exploratory data analysis (EDA) project examining Airbnb listings in Amsterdam using Python. The project explores how prices, room types, neighbourhoods, review activity, and availability vary across the city's short-term rental market.

Developed by **Roei Yaakov and Gefen** as a student team project.

## Project Overview

The analysis starts with a CSV dataset containing **10,168 listings and 18 columns**. It covers data exploration, missing-value handling, feature engineering, outlier analysis, and visual investigation of relationships between listing characteristics.

The notebook includes Python code, tables, charts, and explanations in Hebrew and English. This is an exploratory analysis, not a price-prediction model.

## Main Questions

- How do prices and availability differ across neighbourhoods?
- How do room types compare in price and frequency?
- What relationships exist between prices, review counts, and host listing counts?
- How do minimum-night requirements vary by neighbourhood?
- Where are listings and review activity geographically concentrated?
- Which neighbourhoods have the highest share of listings priced below €100 per night?

## Technologies

| Tool | Purpose |
| --- | --- |
| Python | Data processing and analysis |
| pandas | Data loading, cleaning, grouping, and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Chart creation and customization |
| Seaborn | Statistical and geographic visualizations |
| Google Colab | Notebook execution and Google Drive access |

## Dataset

The input is an Amsterdam Airbnb listings CSV. Its original filename in the notebook is:

`listings airbnb proj roei gefen.csv`

Selected fields include:

- Listing and host identifiers
- Neighbourhood and geographic coordinates
- Room type and nightly price
- Minimum-night requirements
- Total reviews and reviews per month
- Number of listings associated with a host
- Annual availability and reviews in the last twelve months

The original dataset provider and snapshot date are not specified in the supplied project text.

## Analysis Workflow

### 1. Initial Exploration

- Inspect the first and last rows, dimensions, and data types.
- Separate numerical and categorical variables.
- Calculate descriptive statistics.
- Rename host listing count and annual availability columns for readability.

### 2. Data Cleaning

- Remove the entirely empty `neighbourhood_group` column.
- Remove `license` and `last_review` from the working dataset.
- Fill missing host names with `"no name"`.
- Fill missing prices using the median price within each room type.
- Fill missing `reviews_per_month` values with zero.
- Identify outliers using the interquartile range (IQR).
- Apply explicit filters to selected charts, rather than deleting all outliers globally.

### 3. Feature Engineering

| Derived feature | Definition used in the notebook |
| --- | --- |
| Price category | Low: below €100; Medium: €100–€300 inclusive; High: above €300 |
| Host experience proxy | New: 0 listing reviews; Intermediate: 1–50; Experienced: more than 50 |
| Availability category | 0 days, 1–90 days, 91–180 days, or 181–365 days |
| Activity indicator | Active when reviews per month is greater than zero; otherwise inactive |

### 4. Exploratory Analysis

- Histograms and distribution plots
- Counts and comparisons by neighbourhood and room type
- Price comparisons across listing characteristics
- Scatter plots, strip plots, and violin plots
- Geographic density plots of listings and review activity
- Grouped summaries and stacked charts of minimum-night requirements

## Selected Findings

- The price distribution is right-skewed, with a small number of extreme values.
- Listings and review activity are concentrated around central Amsterdam.
- Entire homes and apartments show a broad price range, including higher-priced listings.
- In the notebook's neighbourhood comparison excluding prices of €3,000 or more, **Zuid** has the highest mean nightly price, at approximately **€278.41**.
- In the analysis of listings below €2,000, **Bijlmer-Centrum** has the largest share priced below €100, at **25.4%**.
- Comparisons of host listing count and price do not show a consistent relationship.

These observations describe the supplied dataset and preprocessing choices; they are not claims about current market conditions or causal effects.

## Running in Google Colab

1. Open the project's original `.ipynb` notebook in Google Colab.
2. Place the listings CSV in your Google Drive.
3. Run the Google Drive mounting cell and authorize access to your own Drive.
4. Update `file_path` in the loading cell to match the CSV's location. The original notebook uses:

   ```python
   file_path = "/content/drive/MyDrive/airbnb_proj_roei_gefen/listings airbnb proj roei gefen.csv"
   df = pd.read_csv(file_path)
   ```

5. Run the notebook cells in order to reproduce the tables and visualizations.

The notebook and CSV are required to reproduce the analysis. This README alone does not include them.

## Interpretation & Limitations

- **Missing prices:** 3,847 prices were imputed, so price summaries depend substantially on the chosen imputation method.
- **Date parsing:** Converting `last_review` to datetime increased the missing-value count before the column was removed. The original CSV should be checked with an explicit date format before drawing conclusions about date completeness.
- **Availability is not occupancy:** Unavailable dates may be booked or blocked by the host.
- **Review counts are not ratings:** The analysis uses the number of reviews, not guest satisfaction scores.
- **Host experience is a proxy:** The category is derived from listing review counts, not verified host tenure. Comparisons with review counts are therefore partly defined by construction.
- **Activity is a heuristic:** Zero or missing monthly reviews does not establish that a listing is inactive.
- **Minimum nights are requirements:** They do not measure actual guest stay lengths.
- **Filters differ by analysis:** Some plots use price or review-count thresholds, so results should be compared with those filters in mind.
- **Descriptive comparisons:** The notebook explores hypotheses visually; it does not establish statistical significance or causation.
- **Missing fields:** Neighbourhood-group analyses could not be completed because that field was entirely empty.

## Authors

- Roei Yaakov
- Gefen

