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

