
# Introduction
Amazon-Stock-Prediction is an approach aimed at forecasting the quarterly stock price movement of Amazon (AMZN) based on swing trading strategies.
Swing trading involves identifying short- to medium-term trends (ranging from a few days to several weeks) and capitalizing on upward or downward price swings. 
This project focuses on building a data-driven model that predicts the stock’s price behavior for the next three months using technical indicators, historical data patterns, and financial features.


# Solution 
To build a robust model for predicting stock price movements, multiple strategic approaches have been employed, with an emphasis on feature engineering, diverse machine learning models, and 
hyperparameter optimization using Optuna. Each approach leverages the strengths of advanced ensemble algorithms to improve both prediction accuracy and overall model performance.

## Price Movement Categorization Approaches: Overview Table

| **Approaches**                         | **Description**                                                                                                 | **Advantages**                                                    | **Disadvantages**                                      | **Example Classes**                                                                 |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------------------------------------|
| **Approach 1 - Price Change Categorization**    | Classify the percentage change in the stock's close price into discrete categories (e.g., increase/decrease).    | Simple, captures intensity of movements.                         | May not consider volatility or market conditions.     | 0: Large Decrease (< -5%), 1: Small Decrease (0% to -5%), 2: No Change (0% to 2%)  |
| **Approach 2 - Volatility-Adjusted Classes**    | Combines returns with volatility for a risk-adjusted view.                                                       | Adjusts for underlying volatility, ideal for diversified portfolios. | Requires accurate volatility calculation.              | 0: Significant Loss, 1: Loss, 2: Small Gain, 3: Large Gain                          |
| **Approach 3 - Relative Performance to Market** | Compares the stock's return against a market or sector index.                                                    | Useful for sector-specific strategies, reflects market trends.   | Requires additional market or sector data.            | 0: Underperforming (< -5%), 1: Neutral (-5% to 5%), 2: Outperforming (> 5%)         |
| **Approach 4 - Momentum-Based Classes**         | Uses momentum indicators like RSI to define trends (uptrend, downtrend, or no trend).                            | Captures short- to medium-term sentiment.                         | Sensitive to short-term fluctuations, may be noisy.   | 0: Oversold (< 30 RSI), 1: Neutral (30-70 RSI), 2: Overbought (> 70 RSI)            |
| **Approach 5 - Earnings Surprise Impact**       | Classifies stock movement based on the impact of earnings surprises.                                             | Captures event-driven behavior, useful during earnings season.   | Limited to earnings seasons, needs accurate EPS data. | 0: Large Negative Surprise (< -10%), 1: Neutral (-10% to 10%), 2: Positive Surprise (> 10%) |
| **Approach 6 - Multi-Factor Model**             | Combines several indicators (returns, volatility, momentum, etc.) for a composite target.                         | Comprehensive and robust.                                         | Complex to design, requires extensive feature engineering. | 0: Bearish (< -0.5), 1: Neutral (-0.5 to 0.5), 2: Bullish (> 0.5) |


## Approach 1 - Price Change Categorization
The following table presents the performance metrics for different machine learning models used to classify stock price changes. These models were evaluated based on **accuracy, precision, recall**, and **F1-score** using macro averages.

### Model Performance

| Model | Accuracy (%) | Precision Macro average (%) | Recall Macro average (%) | F1-Score Macro average (%) |
|:-----------:|:------------:|:------------:|:-----------:|:-----------:|
| [AdaBoost Classification](https://github.com/leon7731/Amazon-Stock-Prediction/tree/main/2)i)%20Approach%201%20(Classification)/AdaBoost%20(Classification%20AP1)) | 53 | 47 | 45 | 45 |
| [XGBoost Classification]() | 51 | 43 | 44 | 43 | 
| [Random Forest Classification]() | 49 | 45 | 43 | 43 |
| [CatBoost Classification]() | 55 | 38 | 43 | 38 |

### Model Performance
| Model | Accuracy (%) | Precision Macro average (%) | Recall Macro average (%) | F1-Score Macro average (%) |
|:-----------:|:------------:|:------------:|:-----------:|:-----------:|
| [AdaBoost Classification](https://github.com/leon7731/English-Premier-League-Prediction/tree/main/Approach%201/AdaBoost) | 53 | 47 | 45 | 45 |
| [XGBoost Classification](https://github.com/leon7731/English-Premier-League-Prediction/tree/main/Approach%201/XGBoost) | 51 | 43 | 44 | 43 | 
| [Random Forest Classification](https://github.com/leon7731/English-Premier-League-Prediction/tree/main/Approach%201/Random%20Forest) | 49 | 45 | 43 | 43 |
| [CatBoost Classification](https://github.com/leon7731/English-Premier-League-Prediction/tree/main/Approach%201/CatBoost) | 55 | 38 | 43 | 38 |
