# R_World_Hunger_Analysis
A data analysis project on global hunger, exploring underweight, stunting, and wasting prevalence in children under 5 across different countries and years, with visualizations and regression analysis.

# 🌍 World Hunger Analysis

### 📌 Overview
This project analyzes **global hunger trends** using datasets from Kaggle.  
The main objective is to raise awareness about the impact of hunger worldwide and to evaluate whether there are significant changes in global hunger distribution across different years.

The analysis is aligned with **SDG Goal #2: Zero Hunger**, aiming to provide insights that may help organizations, researchers, and policymakers in addressing world hunger.

---

### 👥 Contributors
- Jonathan William Gunawan (2702251794)  
- Vincentius Jonathan Tanujaya (2702259632)  
- I Made Bagus Narendra (2702268561)  
- Nixon Alexander (2702248420)  

---

### 🎯 Objectives
- Measure and visualize hunger levels across countries and time periods.  
- Identify trends in global hunger distribution (2000–2021).  
- Highlight the most affected countries.  
- Explore correlations between different malnutrition indicators. 

---

### 📊 Data Description
Datasets were sourced from **Kaggle** and merged into a single dataset containing:  
- `Entity` : Country name  
- `Code` : Country code  
- `Year` : Observation year  
- `Prevalence underweight under 5` : % of underweight children under 5  
- `Prevalence stunting under 5` : % of stunted children under 5  
- `Prevalence wasting weight under 5` : % of wasted children under 5  
- `Hunger Indexes` : Global Hunger Index (when available)

📂 Resource: [Kaggle – Global Hunger Index Dataset](https://www.kaggle.com/datasets/whenamancodes/the-global-hunger-index)

---

### 🔧 Methodology
#### 1. Data Preprocessing
- Imported and merged multiple datasets.  
- Removed irrelevant columns.  
- Dropped rows with excessive missing values.  
- Imputed missing values using column means (when <5%).  
- Created a new feature
  
##### Hunger Rate Calculation
The original variable **`Hunger Indexes`** contained **too many missing values** (836 out of 949 rows).  
If kept, it would distort the analysis and reduce data usability.  
Therefore, this column was **dropped** to avoid bias and inconsistencies during data exploration.
To replace the missing `Hunger Indexes`, we introduced a new variable called **`hunger_rate`**, calculated as:

```r
  hunger_rate = (underweight + stunting + wasting) / 3
```

##### Why Hunger Rate?
- ✅ **Replaces missing Hunger Indexes** → provides an alternative indicator.  
- ✅ **More complete data** → underweight, stunting, and wasting had much fewer missing values.  
- ✅ **Represents child malnutrition** → combines three key dimensions of undernutrition in children under 5.  
- ✅ **Balances the analysis** → avoids bias from focusing on a single variable.  
- ✅ **Acts as a proxy for Global Hunger Index** → enabling meaningful comparisons across countries and years.

---

#### 4. Outlier Detection
- Applied **Three Sigma**, **Hampel Method**, and **Boxplot Rule**.  
- Outliers were <5% of total data → acceptable.  

#### 5. Data Exploration & Visualization
- Global Hunger Index distribution by year (density plots).  
- Top 10 countries with the highest hunger levels (bar chart).  
- Hunger severity by country (world heatmap).  
- Correlation analysis between underweight and stunting (scatterplot & regression). 

---

### 📊 Results & Key Findings
- Hunger levels are **highest in Asia and Africa**, especially in developing nations.  
- Over the years, the **distribution of hunger has decreased**, showing progress toward SDG #2.  
- Strong correlation found between **underweight prevalence** and **stunting** in children (R² ≈ 0.71, correlation ≈ 84.5%).

---

### 🛠️ Library
- **R Language**  
- Libraries: `ggplot2`, `tidyverse`, `maps`, `knitr`  

---

### 📚 References
- [World Hunger Facts – World Vision](https://www.worldvision.ca/stories/food/world-hunger-facts-how-to-help#What%20is%20world%20hunger)  
- [Global Hunger Index – Byju’s](https://byjus.com/free-ias-prep/global)  
- [RRI Indonesia – Kelaparan, Krisis Serius](https://www.rri.co.id/kupang/nasional/714100/kelaparan-krisis-serius-yang-menjadi-perhatian-dunia)  

---

### 🚀 How to Run
1. Clone this repository:  
   ```bash
   git clone https://github.com/lynscrat/world-hunger-analysis.git
   cd world-hunger-analysis
