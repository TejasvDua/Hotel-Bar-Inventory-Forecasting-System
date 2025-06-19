# Hotel Bar Inventory Forecasting System

This project automates the forecasting and inventory management process for hotel bars. It leverages historical alcohol consumption data to predict future demand and suggests optimal inventory levels to minimize stockouts and overstocking.

---

## Table of Contents

- [Features](#features)
- [Motivation](#motivation)
- [Installation](#installation)
- [Usage](#usage)
- [Methodology](#methodology)
- [Example Output](#example-output)
- [Supported Libraries](#supported-libraries)
- [File Structure](#file-structure)
- [Future Work](#future-work)
- [License](#license)
- [Contact](#contact)

---

## Features

- **Automated Forecasting:**  
  Uses `AutoARIMA` from the `sktime` library to generate accurate forecasts for each bar-brand pair.
- **Inventory Management:**  
  Recommends par levels and safety stock based on historical consumption and forecasted demand.
- **Performance Metrics:**  
  Tracks RMSE, stockout days, and average overstock to evaluate the effectiveness of the recommendations.
- **Interactive Web Interface:**  
  Provides an easy-to-use interface with `gradio` for selecting bars and brands and visualizing results.
- **Customizable:**  
  Easily adaptable to different datasets and bar setups.

---

## Motivation

Managing inventory in a hotel bar is challenging due to fluctuating demand and the need to avoid both stockouts and excess inventory. This system aims to:

- **Reduce Waste:** By recommending optimal inventory levels.
- **Improve Customer Satisfaction:** By minimizing stockouts.
- **Save Time:** By automating the forecasting and recommendation process.

---

## Installation

### Prerequisites

- **Python 3.11 or higher**
- **Jupyter Notebook** (optional, for running the notebook locally)

### Install Dependencies
- pip install numpy==1.24.3 scipy==1.10.1 statsmodels==0.13.5 pmdarima==2.0.4 sktime gradio pandas matplotlib seaborn


---

## Usage

1. **Prepare Your Data:**  
   Ensure your dataset contains the following columns:
   - `Date Time Served` (datetime)
   - `Bar Name`
   - `Alcohol Type`
   - `Brand Name`
   - `Consumed (ml)`

2. **Run the Notebook:**  
   Open `kristalball_assignment-2.ipynb` in your preferred environment (Google Colab, Jupyter, etc.).

3. **Explore the Interface:**  
   After running the notebook, a Gradio web interface will launch. Use it to:
   - Select a bar from the dropdown
   - Select a brand from the dropdown
   - View forecast results and recommended inventory levels

---

## Methodology

1. **Data Preparation:**  
   - Load and preprocess the consumption data.
   - Aggregate consumption by bar and brand over time.
2. **Time Series Forecasting:**  
   - Use `AutoARIMA` to fit a model to the historical consumption data.
   - Generate forecasts for future periods.
3. **Inventory Recommendation:**  
   - Calculate recommended par levels based on forecasted demand and safety stock.
4. **Performance Evaluation:**  
   - Compare actual vs. forecasted consumption using RMSE.
   - Track stockout days and average overstock.

---

## Example Output

```
# Example: Get inventory recommendation and forecast using the Gradio interface

def get_inventory_forecast(bar_name, brand_name):
    # Preprocess input data for selected bar and brand
    data = preprocess_data(bar_name, brand_name)
    # Generate forecast with AutoARIMA
    forecast = model.predict(data)
    # Calculate recommended par level
    par_level = calculate_par_level(forecast)
    # Return results
    return {
        "forecast": forecast,
        "recommended_par_level": par_level
    }
```

---

## Project Structure

```
.
├── kristalball_assignment-2.ipynb           # Main notebook with code and Gradio interface
├── data/
│   └── Consumption Dataset - Dataset (1).csv  # Example dataset (user-supplied)
├── requirements.txt                        # List of dependencies
└── README.md                               # Project documentation
```


After selecting a bar and brand, you will see:

- **Summary:**  
  - **RMSE:** Measure of forecast accuracy
  - **Recommended Par Level:** Suggested inventory level (ml)
  - **Stockout Days:** Number of days with insufficient stock in the test period
  - **Average Overstock:** Average excess inventory (ml)
- **Forecast Plot:**  
  - Actual vs. forecasted consumption
  - Recommended par level as a horizontal line
<img width="623" alt="image" src="https://github.com/user-attachments/assets/5926f32f-154e-4a78-b078-556d264d2caa" />
<img width="623" alt="image" src="https://github.com/user-attachments/assets/c89761f1-3b4c-4d36-83ca-6c23bc6b7895" />
<img width="623" alt="image" src="https://github.com/user-attachments/assets/49752989-4511-44b2-b0c9-b6b6636c693a" />



---

## Supported Libraries

- **sktime:** Time series forecasting with `AutoARIMA`
- **pmdarima:** ARIMA modeling (optional)
- **statsmodels:** Additional time series analysis
- **gradio:** Interactive web interface
- **pandas, numpy, matplotlib, seaborn:** Data manipulation and visualization

---



## File Structure

<img width="695" alt="image" src="https://github.com/user-attachments/assets/723c6f8c-a2f0-4af9-8f21-3564ad44e199" />



---

## Future Work

- **Integration with POS Systems:**  
  Automatically pull consumption data from point-of-sale systems.
- **Real-time Updates:**  
  Update forecasts and recommendations in real-time as new data becomes available.
- **Multi-brand Forecasting:**  
  Extend the system to forecast and recommend for multiple brands simultaneously.
- **User Management:**  
  Add authentication and user roles for different hotel staff.
- **Mobile App:**  
  Develop a mobile-friendly interface for on-the-go inventory management.

---

## License

This project is licensed under the MIT License. See the LICENSE file for more details.


---

## Contact

For questions or feedback, please open an issue on GitHub or contact the repository owner.

---

> Thank you for your interest in this project! 🍸
