# Global Nuclear Energy Demand Analysis & Forecasting

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Library](https://img.shields.io/badge/Library-Pandas%20|%20Plotly%20|%20Prophet-orange)
![Status](https://img.shields.io/badge/Status-Complete-green)
![License](https://img.shields.io/badge/License-Old%20Economy%20(Private)-red)

A comprehensive data science project analyzing global uranium demand trends using **Thermal Capacity (MWt)** as a primary proxy. This project utilizes data from the **IAEA Power Reactor Information System (PRIS)** to build a robust data pipeline, perform exploratory data analysis (EDA), forecast future demand using Facebook Prophet, and validate model performance.

> **RESTRICTED ACCESS:** This project is protected under the **Old Economy License**. It is intended for private use only and is **not for public distribution**.

---

## Project Overview

While most energy analysis focuses on *supply* (electricity generated), this project models the **demand side** (uranium consumption). By tracking the **Thermal Capacity** of the global reactor fleet, we can estimate fuel requirements independent of electrical conversion efficiency.

**Key Objectives:**
1.  **Data Engineering:** Transform raw, unformatted reactor database logs into clean, aggregated time-series data.
2.  **EDA:** Visualize historical trends, technology shifts, and the construction pipeline.
3.  **Forecasting:** Predict global thermal capacity 20 years into the future using time-series modeling.
4.  **Validation:** Rigorously backtest the model to ensure reliability.
5.  **Risk Analysis:** Analyze fleet aging and attrition to identify "demand destruction" risks.

---

## Project Structure

The project is modularized into **8 sequential notebooks** to ensure reproducibility and clear logic flow.

### Phase 1: Data Engineering
* **01_setup_ingestion.ipynb**: Loads the raw IAEA PRIS dataset, inspects 29+ columns, and establishes `Thermal Capacity, MWt` as the target variable.
* **02_cleaning_selection.ipynb**: Performs core cleaning: handling missing values, converting data types (dates, integers), and filtering relevant columns. Saves `pris_clean.csv`.
* **03_feature_engineering.ipynb**: The "Engine Room." Pre-aggregates the clean data into specialized time-series files (Global, National, Tech-specific, Pipeline) to optimize downstream performance.

### Phase 2: Exploratory Data Analysis (EDA)
* **04_eda_global_demand.ipynb**: Visualizes the "Macro" view. Global demand curves, top country rankings, and historical growth trends using interactive Plotly charts.
* **05_eda_tech_pipeline.ipynb**: Visualizes the "Micro" view. Analysis of reactor technologies (PWR, BWR, PHWR) and the "Operational vs. Under Construction" pipeline.

### Phase 3: Modeling & Forecasting
* **06_forecasting_model.ipynb**: Trains a **Prophet** time-series model on historical data (1950–Present) to generate a 20-year forecast with uncertainty intervals. Saves the model to JSON.
* **07_model_validation.ipynb**: **Rigorous Backtesting.** Splits data at 2015, trains a test model, and compares predictions vs. actuals to calculate RMSE and MAPE. Deconstructs the forecast into trend and seasonality components.

### Phase 4: Advanced Analytics
* **08_advanced_analytics.ipynb**: High-value leading indicators:
    * **Net Demand Churn:** New builds vs. Shutdowns.
    * **Fleet Age Profile:** Boxplots identifying countries with aging fleets (shutdown risk).
    * **Reality Check:** Overlays the statistical forecast against the actual construction pipeline.
    * **Tech Leading Indicators:** Shifts in reactor technology preferences over time.

---

## Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/nuclear-demand-analysis.git](https://github.com/yourusername/nuclear-demand-analysis.git)
    cd nuclear-demand-analysis
    ```

2.  **Install dependencies:**
    It is recommended to use a virtual environment.
    ```bash
    pip install pandas numpy plotly fbprophet scikit-learn ipywidgets
    ```

3.  **Data Prerequisite:**
    Place the raw file `Reactor Database - master(pris.iaea.xlsx - in.csv` in the root directory.

4.  **Run the Pipeline:**
    Execute the notebooks in order (01 through 08). Each notebook generates outputs required for the next.

---

## Key Visualizations

This project uses **Plotly** for interactive visualizations. Key outputs include:

* **Global Demand Curve:** Area chart showing the rise of nuclear thermal capacity from 1950 to present.
* **Forecast vs. Reality:** A dual-axis chart comparing the Prophet forecast (statistical potential) against the actual "Under Construction" pipeline (physical reality).
* **Fleet Age Distribution:** Boxplots revealing that established markets (USA, France) face retirement risks, while emerging markets (China) have "young" fleets.

---

## License & Usage

**This software is strictly controlled under the OLD ECONOMY LICENSE.**

* **NOT FOR PUBLIC USE.**
* **NO DISTRIBUTION.**

This codebase is proprietary and confidential. Unauthorized copying, modification, distribution, or public display of this file, via any medium, is strictly prohibited.
