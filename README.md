# Medical Data Visualizer

## Overview

The **Medical Data Visualizer** project is aimed at analyzing and visualizing medical examination data using Python libraries such as **Pandas**, **Seaborn**, and **Matplotlib**. The dataset includes medical details from patients, including body measurements, blood test results, and lifestyle choices. The goal is to understand the relationship between these features and the presence of cardiovascular disease.

## Dataset Description

The dataset used in this project is `medical_examination.csv` and contains **70,000 rows** with the following columns:

| Column Name  | Description                              |
|--------------|------------------------------------------|
| `id`         | Unique identifier for each patient       |
| `age`        | Age of the patient (in days)             |
| `sex`        | Gender of the patient (binary code)      |
| `height`     | Height of the patient (in cm)            |
| `weight`     | Weight of the patient (in kg)            |
| `ap_hi`      | Systolic blood pressure (in mm Hg)       |
| `ap_lo`      | Diastolic blood pressure (in mm Hg)      |
| `cholesterol`| Cholesterol level (1: normal, 2: above normal, 3: well above normal) |
| `gluc`       | Glucose level (1: normal, 2: above normal, 3: well above normal) |
| `smoke`      | Smoking status (binary: 0 = non-smoker, 1 = smoker) |
| `alco`       | Alcohol intake (binary: 0 = no, 1 = yes) |
| `active`     | Physical activity level (binary: 0 = inactive, 1 = active) |
| `cardio`     | Presence of cardiovascular disease (binary: 0 = no, 1 = yes) |
| `overweight` | Overweight status (binary: 0 = not overweight, 1 = overweight) |

## Project Requirements

1. **Data Preprocessing**
   - Import the data from `medical_examination.csv`.
   - Add an "overweight" column calculated using the formula: 
     \[
     BMI = \frac{weight (kg)}{height (m)^2}
     \]
     A BMI greater than 25 is considered overweight.

2. **Data Normalization**
   - Normalize categorical features like cholesterol and glucose, where:
     - 1 -> 0 (good)
     - 2 or 3 -> 1 (bad)

3. **Visualization Tasks**

   - **Categorical Plot**: A plot showing the counts of good and bad outcomes for cholesterol, glucose, alcohol consumption, physical activity, smoking, and overweight status for patients with and without cardiovascular disease. This is achieved using `sns.catplot()`.
   
   - **Heatmap**: A heatmap showing the correlation between features after cleaning the data by:
     - Filtering out rows where diastolic pressure is higher than systolic.
     - Filtering out rows with extreme values (height and weight outside the 2.5th and 97.5th percentiles).
     - Calculating the correlation matrix for the remaining data and plotting it using `sns.heatmap()`.

## Functions

### `draw_cat_plot()`

This function creates a categorical plot that visualizes the relationship between various lifestyle and health features and the presence of cardiovascular disease.

- **Parameters**: None
- **Returns**: Matplotlib figure object (`fig`), saved as 'catplot.png'.

### `draw_heat_map()`

This function generates a heatmap to visualize correlations between the features in the cleaned dataset.

- **Parameters**: None
- **Returns**: Matplotlib figure object (`fig`), saved as 'heatmap.png'.

## Results
### Categorical Plot

From the categorical plot comparing health indicators with the presence (`cardio = 1`) or absence (`cardio = 0`) of cardiovascular disease, we can infer the following:

- **Overweight:** There is a strong positive association between being overweight and cardiovascular disease. A significantly higher number of individuals with `cardio = 1` are overweight (`value = 1`) compared to those with `cardio = 0`.

- **Cholesterol:** Individuals with cardiovascular disease show a higher frequency of elevated cholesterol levels (`value = 1`), indicating that high cholesterol is a contributing factor or marker.

- **Glucose:** A higher number of people with `cardio = 1` also have elevated glucose levels (`value = 1`), though the difference is less pronounced than cholesterol or overweight.

- **Activity:** Fewer individuals with `cardio = 1` are physically active (`active = 1`) compared to those without the disease, suggesting inactivity may be a risk factor.

- **Alcohol Consumption:** People without cardiovascular disease (`cardio = 0`) show a slightly higher alcohol usage. This may indicate a weak or inverse correlation, but not a strong or clear trend.

- **Smoking:** Smoking levels appear similar between both groups, indicating no strong correlation with the cardiovascular condition based on this data.

### Correlation Analysis

A heatmap of Pearson correlation coefficients was generated to assess linear relationships among variables. The key takeaways are:

- No feature has a strong correlation (≥ 0.5) with the target variable `cardio`.
- Mild positive correlations were observed between `cardio` and the following variables:
  - `ap_lo` (diastolic BP): 0.3
  - `ap_hi` (systolic BP): 0.2
  - `cholesterol`: 0.2
  - `age`: 0.2
  - `glucose`: 0.1
  - `overweight`: 0.1

- The most notable correlation in the entire heatmap is between `weight` and `overweight` (0.7), which is intuitive.

These results suggest that **no single feature strongly predicts cardiovascular disease**, emphasizing the **multifactorial** nature of heart-related conditions. A model would likely need to consider combinations of features for better prediction.
