
# Introduction
Amazon-Stock-Prediction is an approach aimed at forecasting the quarterly stock price movement of Amazon (AMZN) based on swing trading strategies.
Swing trading involves identifying short- to medium-term trends (ranging from a few days to several weeks) and capitalizing on upward or downward price swings. 
This project focuses on building a data-driven model that predicts the stock’s price behavior for the next three months using technical indicators, historical data patterns, and financial features.


# Solution 
To build a robust model for predicting stock price movements, multiple strategic approaches have been employed, with an emphasis on feature engineering, diverse machine learning models, and 
hyperparameter optimization using Optuna. Each approach leverages the strengths of advanced ensemble algorithms to improve both prediction accuracy and overall model performance.

## Price Movement Categorization Approaches: Overview Table

# Price Movement Categorization Approaches

| **Approach**                                | **Description**                                                                                                  | **Advantages**                                                    | **Disadvantages**                                      | **Example Classes**                                                                 |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------------------------------------|
| **Approach 1 - Price Change Categorization** | Classify the percentage change in the stock's close price into discrete categories (e.g., increase/decrease).    | Simple, captures the intensity of movements.                      | May not consider volatility or market conditions.     | 0: Large Decrease (< -5%), 1: Small Decrease (0% to -5%), 2: No Change (0% to 2%), 3: Small Increase (2% to 5%), 4: Large Increase (> 5%) |
| **Approach 2 - Volatility-Adjusted Classes** | Combines returns with volatility for a risk-adjusted view.                                                        | Adjusts for underlying volatility, ideal for diversified portfolios. | Requires accurate volatility calculation.              | 0: Significant Loss, 1: Loss, 2: Small Gain, 3: Large Gain                          |
| **Approach 3 - Multi-Feature Targets (Hybrid Target)** | Uses multiple features (e.g., RSI, MACD, and Cumulative Return) to create more nuanced target classes.            | Captures trend strength, momentum, and cumulative performance.   | Complex to design, requires multiple features.        | 0: Strong downtrend with cumulative loss and negative MACD, 1: Weak downtrend with neutral MACD, 2: Sideways trend (return between -5% and 5%), 3: Uptrend with positive cumulative return and positive MACD, 4: Strong uptrend with RSI > 70 and cumulative return > 10% |

## Approach 1 - Price Change Categorization
The following table presents the performance metrics for different machine learning models used to classify stock price changes. These models were evaluated based on **accuracy, precision, recall**, and **F1-score** using macro averages.

### Model Performance (Sorted by F1-Score Macro Average)
| **Model** | **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:-------------------------------------------:|:------------:|:----------------------------:|:----------------------------:|:----------------------------:|
| [AdaBoost Classification](https://github.com/leon7731/Amazon-Stock-Prediction/tree/main/Approach%201/AdaBoost%20(Classification%20AP1)) | 92 | 93 | 93 | 92 |
| [XGBoost Classification](https://github.com/leon7731/Amazon-Stock-Prediction/tree/main/Approach%201/CatBoost%20(Classification%20AP1)) | 75 | 42 | 50 | 45 |
| [CatBoost Classification](https://github.com/leon7731/Amazon-Stock-Prediction/tree/main/Approach%201/XGBoost%20(Classification%20AP1)) | 75 | 48 | 53 | 47 |
| [Random Forest Classification](https://github.com/leon7731/Amazon-Stock-Prediction/tree/main/Approach%201/Random%20Forest%20(Classification%20AP1)) | 67 | 38 | 43 | 40 |

### Backtesting Performance (Sorted by F1-Score Macro Average)
| **Model** | **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:-------------------------------------------:|:------------:|:----------------------------:|:----------------------------:|:----------------------------:|
| [AdaBoost Classification Backtesting](./Approach%201/AdaBoost%20(Classification%20AP1)/3%29%20AdaBoost%20(BackTesting).ipynb) | 86 | 60 | 67 | 63 |
| [CatBoost Classification Backtesting](Approach%201/CatBoost%20(Classification%20AP1)/3%29%20CatBoost%20(BackTesting).ipynb) | 86 | 60 | 67 | 63 |
| [XGBoost Classification Backtesting](Approach%201/XGBoost%20(Classification%20AP1)/3%29%20XGBoost%20(BackTesting).ipynb) | 86 | 60 | 67 | 63 |
| [Random Forest Classification Backtesting](Approach%201/Random%20Forest%20(Classification%20AP1)/3%29%20Random%20Forest%20(BackTesting).ipynb) | 57 | 27 | 33 | 30 |

---

## Approach 2 -  Volatility-Adjusted Classes
The following table presents the performance metrics for different machine learning models used to classify stock price changes. These models were evaluated based on **accuracy, precision, recall**, and **F1-score** using macro averages.

### Model Performance (Sorted by F1-Score Macro Average)

| **Model** | **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:-------------------------------------------:|:------------:|:----------------------------:|:----------------------------:|:----------------------------:|
| [XGBoost Classification]() | 57 | 47 | 67 | 52 |
| [CatBoost Classification]() | 50 | 41 | 45 | 34 |
| [AdaBoost Classification]() | 42 | 20 | 40 | 24 |
| [Random Forest Classification]() | 8 | 2 | 20 | 3 |

### Backtesting Performance (Sorted by F1-Score Macro Average)

| **Model** | **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:-------------------------------------------:|:------------:|:----------------------------:|:----------------------------:|:----------------------------:|
| [AdaBoost Classification Backtesting]() | 57 | 47 | 67 | 52 |
| [XGBoost Classification Backtesting]() | 57 | 47 | 67 | 52 |
| [CatBoost Classification Backtesting]() | 37 | 23 | 12 | 17 |
| [Random Forest Classification Backtesting]() | 29 | 11 | 33 | 17 |


---

## Approach 3 -  Multi-Feature Targets (Hybrid Target)
The following table presents the performance metrics for different machine learning models used to classify stock price changes. These models were evaluated based on **accuracy, precision, recall**, and **F1-score** using macro averages.


### Model Performance (Sorted by F1-Score Macro Average)

| **Model** | **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:------------------------------------------:|:----------------:|:-------------------------------:|:----------------------------:|:------------------------------:|
| [AdaBoost Classification](Approach%203/AdaBoost%20(Classification%20AP3)/2%29%20AdaBoost%20(Pipeline).ipynb) | 83 | 57 | 62 | 60 |
| [CatBoost Classification](Approach%203/CatBoost%20(Classification%20AP3)/2%29%20CatBoost%20(Pipeline).ipynb) | 83 | 57 | 62 | 60 |
| [Random Forest Classification](Approach%203/Random%20Forest%20(Classification%20AP3)/2%29%20Random%20Forest%20(Pipeline).ipynb) | 50 | 36 | 38 | 32 |
| [XGBoost Classification](Approach%203/XGBoost%20(Classification%20AP3)/2%29%20XGBoost%20(Pipeline).ipynb) |  |  |  |  |


### Backtesting Performance (Sorted by F1-Score Macro Average)
| **Model**| **Accuracy (%)** | **Precision Macro Average (%)** | **Recall Macro Average (%)** | **F1-Score Macro Average (%)** |
|:------------------------------------------:|:----------------:|:-------------------------------:|:----------------------------:|:------------------------------:|
| [AdaBoost Classification](Approach%203/AdaBoost%20(Classification%20AP3)/3%29%20AdaBoost%20(BackTesting).ipynb) | 100 | 100 | 100 | 100 |
| [CatBoost Classification](Approach%203/CatBoost%20(Classification%20AP3)/3%29%20CatBoost%20(BackTesting).ipynb) | 100 | 100 | 100 | 100 |
| [Random Forest Classification](Approach%203/Random%20Forest%20(Classification%20AP3)/3%29%20Random%20Forest%20(BackTesting).ipynb) | 71 | 28 | 33 | 30 |
| [XGBoost Classification](Approach%203/XGBoost%20(Classification%20AP3)/3%29%20XGBoost%20(BackTesting).ipynb) |  |  |  |  |








