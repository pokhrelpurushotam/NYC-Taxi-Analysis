#  NYC Yellow Taxi Trip Analysis — Capstone Project

**Capstone Project**  
**Tools:** Python · Tableau · Scikit-learn · TensorFlow · Pandas · Seaborn

---

## Project Overview

An end-to-end data analytics capstone, analyzing **NYC Yellow Taxi trip records** (10% monthly sample, ~383K trips across 2023). The project spans exploratory data analysis, interactive dashboard design, predictive modeling, and hyperparameter tuning — delivering actionable insights into taxi demand patterns, fare drivers, and trip characteristics across New York City.

---

## Tableau Dashboards

### Dashboard 1 — NYC Taxi Trip Demand Insights
![Dashboard 1 — Demand Insights](<images/Screenshot (913).png>)

- Five KPI cards (Total Trips, Avg Fare, Avg Distance, Total Revenue, Avg Passengers)
- Interactive pickup zone map with action filters
- Click a zone on the map to filter all KPIs dynamically

### Dashboard 2 — NYC Taxi Trip Trends & Patterns
![Dashboard 2 — Trends & Patterns](<images/Screenshot (914).png>)

- Top 10 pickup and dropoff locations (bar charts)
- Total revenue by payment method (pie chart)
- Top ten destinations by revenue (bar chart)
- Filters for dropoff zone, year/month, payment method, and trip distance

> **Note:** To view the interactive Tableau workbook, open `NYC Taxi Tableu project.twbx` in [Tableau Public](https://public.tableau.com/) or Tableau Desktop.

---

## Repository Contents

| File | Description |
|------|-------------|
| `NYC_Taxi_Analysis_Final.ipynb` | Full Python notebook — EDA, cleaning, feature engineering, modeling (Linear Regression, Random Forest, Gradient Boosting, ANN) |
| `NYC Taxi Tableu project.twbx` | Tableau packaged workbook — two interactive dashboards with KPIs, maps, and filters |
| `README.md` | This file |

---

## Key Findings

- **Short trips dominate:** Most trips are under 5 miles with fares below $30
- **Peak demand:** Weekday evenings (5–8 PM), especially Thursdays and Fridays
- **Payment insights:** Credit card is the dominant method and correlates with higher tip percentages
- **Top zones:** Pickup and dropoff activity is concentrated in Manhattan (Midtown, Upper East Side) and airports (JFK, LaGuardia)
- **Strongest fare predictors:** `trip_distance` and `trip_duration_min` are the most influential features

---

## Methodology

### 1. Data Cleaning & Preprocessing
- Removed invalid trips (zero distance, negative fares, durations > 10 hours)
- Median/mode imputation for missing values (`passenger_count`, `RatecodeID`, `congestion_surcharge`)
- Outlier removal using IQR method and percentile trimming
- Dropped duplicate columns from data joins

### 2. Feature Engineering
- **Temporal features:** `pickup_hour`, `pickup_dayofweek`, `pickup_month`, `pickup_day`
- **Trip features:** `trip_duration_minutes`, `distance_per_passenger`, `same_borough_trip`, `same_zone_trip`
- **Demand indicator:** Demand level (Low/Medium/High) based on weekday-hour trip volume

### 3. Exploratory Data Analysis
- Distribution analysis (histograms, boxplots)
- Bivariate analysis (fare vs distance scatter, payment type vs tips)
- Demand heatmap (weekday × hour)
- Correlation matrix across all encoded features

### 4. Predictive Modeling

Four models were trained for **two targets**: `fare_amount` and `trip_distance`.

| Model | Approach |
|-------|----------|
| **Linear Regression** | Baseline with StandardScaler + OneHotEncoder pipeline |
| **Random Forest** | 30 estimators, max_depth=15, trained on 50K sample |
| **Gradient Boosting** | Default → tuned via RandomizedSearchCV (3-fold CV, 15 iterations) |
| **ANN (Deep Learning)** | 512→256→128→64 dense layers with dropout, early stopping |

**Best model for both targets: Tuned Gradient Boosting** — highest R², lowest RMSE, with interpretable feature importances.

---

## Tech Stack

| Category | Tools |
|----------|-------|
| **Language** | Python 3 |
| **Data** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Tableau |
| **ML/Modeling** | Scikit-learn (LinearRegression, RandomForest, GradientBoosting) |
| **Deep Learning** | TensorFlow / Keras |
| **Preprocessing** | ColumnTransformer, StandardScaler, OneHotEncoder, LabelEncoder |
| **Tuning** | RandomizedSearchCV |

---

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/pokhrelpurushotam/NYC-Taxi-Analysis.git
   cd NYC-Taxi-Analysis
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn tensorflow
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook NYC_Taxi_Analysis_Final.ipynb
   ```

4. **View the Tableau dashboard**  
   Open `NYC Taxi Tableu project.twbx` in Tableau Public or Tableau Desktop.

---

## Dataset

**Source:** [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)  
**Sample:** 10% stratified sample by month (383,102 records, 31 columns)  
**Spatial data:** NYC Taxi Zone shapefile (263 zones)

---

## Authors

**Group 9** — DAB Capstone Project II

---

