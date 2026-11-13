# Food Delivery Data Analysis

## Project Overview

This project focuses on understanding, cleaning, and exploring a food delivery dataset using Python.

The objective is to investigate data quality, identify patterns in delivery operations, analyze factors associated with delivery duration, and generate insights that can support better delivery management decisions.

The project is divided into two phases:

- **Week 1:** Data Understanding and Cleaning.
- **Week 2:** Exploratory Data Analysis (EDA).

## Project Objectives

- Understand the structure and characteristics of the dataset.
- Identify missing values, duplicate records, and inconsistent data.
- Investigate invalid values and potential outliers.
- Standardize inconsistent time formats.
- Validate order and pickup time relationships.
- Analyze delivery duration patterns.
- Investigate relationships between delivery duration and operational factors.
- Create meaningful visualizations.
- Document findings and business recommendations.

## Dataset Information

| Description | Details |
|---|---|
| Original records | 45,584 |
| Original columns | 20 |
| Week 1 cleaned dataset columns | 23 |
| Week 2 analysis DataFrame columns | 25 |
| File format | CSV |
| Domain | Food Delivery |

The two additional Week 2 columns are `Distance_km` and `Distance_km_validated`. They are calculated during exploratory analysis and are not part of the original cleaned CSV.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- VS Code
- Git and GitHub

## Week 1: Data Understanding and Cleaning

### 1. Dataset Understanding

- Inspected dataset dimensions and column names.
- Examined data types and summary statistics.
- Investigated numerical and categorical variables.

### 2. Data Quality Checks

- Checked missing values.
- Checked exact duplicate records.
- Checked duplicate order IDs.
- Investigated unusual categorical values.
- Identified potential numerical outliers.

### 3. Invalid Value Investigation

- Identified 53 ratings outside the assumed 1–5 rating range.
- Converted those invalid ratings into missing values.
- Investigated delivery partner ages below 18.
- Investigated unusual geographical coordinates.

### 4. Time Standardization

- Investigated decimal time representations.
- Standardized order and pickup times into minutes.
- Preserved next-day pickup rollover information.
- Created an order-to-pickup time interval column.

### 5. Missing Value Treatment

Missing values were retained when their actual values could not be reliably established. No rows were deleted solely because of missing values.

### 6. Validation

- Verified that no exact duplicate rows remained.
- Confirmed that order and pickup intervals were positive for records with available order times.
- Exported the cleaned dataset separately from the raw dataset.

## Week 2: Exploratory Data Analysis (EDA)

### 1. Delivery Duration Analysis

- Calculated descriptive statistics for delivery duration.
- Analyzed average, median, minimum, maximum, and standard deviation.
- Created a histogram to understand the distribution.

**Key findings:**

- Average delivery duration: 26.29 minutes.
- Median delivery duration: 26 minutes.
- Minimum duration: 10 minutes.
- Maximum duration: 54 minutes.
- Standard deviation: approximately 9.38 minutes.

### 2. Traffic Density Analysis

Compared delivery duration across different traffic conditions.

| Traffic condition | Average duration |
|---|---:|
| High | 27.24 min |
| Jam | 31.18 min |
| Low | 21.27 min |
| Medium | 26.70 min |

Jam traffic had the highest average delivery duration, while low traffic had the lowest.

### 3. Weather Analysis

Investigated how delivery duration varied across weather conditions.

| Weather condition | Average duration |
|---|---:|
| Cloudy | 28.92 min |
| Fog | 28.91 min |
| Sandstorms | 25.88 min |
| Stormy | 25.87 min |
| Sunny | 21.86 min |
| Windy | 26.12 min |

Cloudy and foggy conditions showed higher average delivery durations than sunny conditions.

### 4. Vehicle Analysis

Compared average delivery duration across vehicle categories.

| Vehicle type | Average duration |
|---|---:|
| Motorcycle | 27.61 min |
| Scooter | 24.48 min |
| Electric scooter | 24.47 min |
| Bicycle | 26.43 min |

Motorcycle deliveries showed a higher average duration than scooter and electric scooter deliveries.

### 5. City Analysis

Compared delivery duration across city categories.

| City category | Average duration |
|---|---:|
| Metropolitian | 27.31 min |
| Urban | 22.98 min |
| Semi-Urban | 49.73 min |

Semi-Urban deliveries showed considerably higher average duration. However, this category contains only 164 records, so the result should be interpreted cautiously.

### 6. Distance Analysis

- Calculated geographical distance using the Haversine formula.
- Investigated suspicious restaurant and delivery coordinates.
- Identified 4,071 records with at least one suspicious coordinate condition.
- Created a separate validated distance column without modifying the original coordinate values.
- Excluded flagged records from the preliminary validated-distance analysis.

**Validated distance statistics:**

| Statistic | Result |
|---|---:|
| Available records | 41,513 |
| Average distance | 9.72 km |
| Median distance | 9.19 km |
| Minimum distance | 1.47 km |
| Maximum distance | 20.97 km |

Note: These are straight-line geographical distance estimates, not actual road distances. Coordinate validation is preliminary and does not establish the correct coordinates for flagged records.

### 7. Distance vs Delivery Duration

Used a scatter plot and Pearson correlation to investigate the relationship between delivery distance and delivery duration.

- Pearson correlation: **+0.321**
- Interpretation: Weak-to-moderate positive linear association.
- Longer calculated distances tend to be associated with longer delivery durations.

### 8. Multiple Deliveries Analysis

Compared average delivery duration across recorded multiple-delivery values.

| Recorded value | Average duration |
|---|---:|
| 0 | 22.88 min |
| 1 | 26.85 min |
| 2 | 40.45 min |
| 3 | 47.82 min |

Higher recorded values showed an increasing association with delivery duration.

### 9. Correlation Analysis

Investigated numerical relationships with delivery duration.

| Feature | Pearson correlation |
|---|---:|
| Multiple deliveries | +0.387 |
| Validated distance | +0.321 |
| Delivery person age | +0.300 |
| Delivery person ratings | -0.341 |
| Vehicle condition | -0.234 |
| Order time | +0.173 |
| Pickup time | +0.173 |

Correlation indicates association, not causation. Correlations involving encoded categorical or ordinal values should be interpreted carefully.

## Visualizations

The project includes the following visualizations:

| Visualization | File |
|---|---|
| Delivery duration distribution | `delivery_duration_distribution.png` |
| Distance distribution | `distance_distribution.png` |
| Distance vs delivery duration | `initial_distance_vs_duration.png` |
| Traffic vs delivery duration | `traffic_vs_duration.png` |
| Weather vs delivery duration | `weather_vs_duration.png` |
| Vehicle vs delivery duration | `vehicle_vs_duration.png` |
| City vs delivery duration | `city_vs_duration.png` |
| Multiple deliveries vs duration | `multiple_deliveries_vs_duration.png` |
| Correlation heatmap | `correlation_heatmap.png` |

All visualization files are available in the `visualizations/` directory.

## Business Insights and Recommendations

Based on the exploratory analysis:

1. **Traffic management:** Consider traffic density when estimating delivery arrival times.
2. **Multiple delivery planning:** Review multiple-order assignment strategies to reduce delivery delays.
3. **Distance-based planning:** Include geographical distance in delivery-time estimation.
4. **City-level performance:** Investigate operational challenges associated with longer Semi-Urban delivery durations.
5. **Weather considerations:** Consider weather conditions when planning delivery operations.
6. **Vehicle performance:** Monitor delivery performance across different vehicle categories.

These recommendations are based on observed patterns and require further investigation before operational implementation.

## Project Limitations

- Some geographical coordinates contained suspicious values.
- Validated distances are straight-line estimates rather than road distances.
- Semi-Urban deliveries have a relatively small sample size.
- Missing values were retained where reliable replacements were unavailable.
- Correlation results do not establish causal relationships.
- Additional operational information may be needed to explain delivery performance fully.

## Project Structure

```text
food-delivery-data-analysis/
│
├── data/
│   ├── raw/
│   │   └── README.md
│   └── processed/
│       └── cleaned_food_delivery.csv
│
├── notebooks/
│   ├── 01_data_understanding_and_cleaning.ipynb
│   └── 02_exploratory_data_analysis.ipynb
│
├── docs/
│   └── cleaning_log.csv
│
├── visualizations/
│   ├── city_vs_duration.png
│   ├── correlation_heatmap.png
│   ├── delivery_duration_distribution.png
│   ├── distance_distribution.png
│   ├── initial_distance_vs_duration.png
│   ├── multiple_deliveries_vs_duration.png
│   ├── traffic_vs_duration.png
│   ├── vehicle_vs_duration.png
│   └── weather_vs_duration.png
│
├── README.md
└── requirements.txt
```

## How to Run the Project

1. Clone the repository.
2. Install the required dependencies.
3. Open the project in VS Code or Jupyter Notebook.
4. Navigate to the `notebooks/` directory.
5. Execute the notebooks in order.

Install dependencies:

```bash
pip install -r requirements.txt
```

Run Week 1 first, followed by Week 2.

## Project Status

- [x] Week 1: Dataset Understanding and Cleaning
- [x] Week 2: Exploratory Data Analysis
- [x] Delivery duration analysis
- [x] Traffic, weather, vehicle, and city analysis
- [x] Distance calculation and preliminary coordinate validation
- [x] Correlation analysis
- [x] Visualization creation
- [x] Business insights and recommendations

## Future Scope

- Perform deeper statistical analysis.
- Investigate additional factors influencing delivery duration.
- Explore predictive modelling for delivery-time estimation.
- Analyze delivery performance using more detailed geographical and operational data.

## Author

**Gnanesh Buddabathina**