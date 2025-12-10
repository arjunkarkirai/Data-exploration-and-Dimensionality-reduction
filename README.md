**Algerian Forest Fires — Data Exploration & Dimensionality Reduction
**
This project performs data preprocessing, missing-value handling, exploratory visualization, and dimensionality reduction on a modified version of the Algerian Forest Fires Dataset (originally from UCI).
The goal is to explore environmental variables linked to forest fires across two Algerian regions and analyze underlying patterns using PCA and MDS.

This project is designed as part of my data analyst portfolio, demonstrating skills in data cleaning, feature engineering, visualization, statistical analysis, and dimensionality reduction.

📁 Project Structure
├── dataset/
│   └── forest_fires.csv
├── Data exploration and Dimensionality reduction.ipynb   # analysis code
└── README.md

** Project Overview
**
The dataset contains over 244 observations collected in the summer of 2012 from Bejaia and Sidi Bel-Abbes, Algeria.

It includes:

Date variables: day, month, year

Environmental attributes: Temperature, RH, Wind Speed, Rain

Fire indices: FFMC, DMC

Target variable: fire or no fire

Region label: Bejaia / Sidi Bel-Abbes

This project includes:

Dataset inspection and validation

Missing-value identification & correction

Median imputation using scikit-learn and a custom function

Exploratory Data Analysis (EDA) with visualizations

Standardization

PCA (Principal Component Analysis)

MDS (Multi-Dimensional Scaling)

Monthly fire probability analysis

******Technologies & Tools Used**

Python 3.x

pandas

NumPy

matplotlib

seaborn

scikit-learn

** 1. Data Preprocessing
**
Key steps:

Loaded the dataset using pandas.read_csv()

Inspected distributions with .info(), .describe(), and range checks

Identified physically impossible values (e.g., RH > 100%)

Created an “invalid values summary” dictionary

Invalid Values Handling

Invalid value thresholds included:

Temperature: < -50 or > 60

RH: < 0 or > 100

Wind Speed: < 0 or > 200

FFMC: < 18.7 or > 96.2

All invalid values were replaced with NaN for proper imputation.

** 2. Missing Value Imputation
**
Two methods were implemented:

(a) SimpleImputer (Median Strategy)

Replaced invalid values → NaN

Applied median imputation across all numerical features

(b) Custom Imputation Function

A user-defined function:

Detected invalid values

Converted them to NaN

Filled NaN with column medians

Both methods yielded identical results (validated programmatically).

**3.** Exploratory Visualizations **
**Temperature Analysis**

A 3-panel figure was generated containing:

Boxplot

Histogram

Scatterplot (Temperature vs RH), colored by fire class

Relative Humidity (RH)

Binned into 5% intervals using pd.cut()

Counts computed per class

Visualized using bar plots

**4. Fire Probability by Month
**
As part of the analytic phase, the probability of fire occurrence for each month was calculated:

Fire Probability
=
fires in month
total observations in month
Fire Probability=
total observations in month
fires in month
	​


A line chart was plotted using seaborn to highlight seasonal fire patterns.

Key Insights

Fire probability is not evenly distributed across months

Warmer and drier months show a significant increase in fire risk

Provides actionable insight into seasonal fire behavior

This section demonstrates key data analyst skills:
✔ Grouping & aggregating data
✔ Feature transformations
✔ Analytical interpretation
✔ Communicating insights

5. **Standardization**

Used StandardScaler to standardize all numerical predictors.

Excluded:

Target variable (fire class)

Region (categorical)

Output:

data_standardized → standardized numeric features

y → class labels

**6. PCA (Principal Component Analysis)
**
Performed PCA with 2 components.

Outputs included:

explained_variance_ratio_

components_ (loadings matrix)

Identification of top contributing features to PC1

This helped uncover key variables driving environmental variability.

** 7. Multi-Dimensional Scaling (MDS)
**
Two MDS approaches were used:

✔️ (a) MDS with Euclidean distance

Input: standardized data

Output: 2D coordinates visualized by fire class

✔️ (b) MDS with precomputed distance matrix

Distance matrix created using euclidean_distances()

Results matched version (a), confirmed with assert_allclose()

**Results Summary
**
Dataset successfully cleaned and validated

Invalid environmental values corrected

Missing values imputed using two methods

PCA identified core contributors to variance

MDS visualized sample similarity in reduced dimensions

Fire probability peaked in summer months

Full workflow is reproducible for modeling or operational analysis

**How to Run
**
Install dependencies:

pip install numpy pandas matplotlib seaborn scikit-learn


Ensure the dataset is placed in:

dataset/forest_fires.csv


Run:

Jupyter Notebook


 References

UCI Machine Learning Repository — Algerian Forest Fires

scikit-learn documentation
Contributing

Contributions, suggestions, and improvements are welcome.
Feel free to fork this repo and submit a pull request.
