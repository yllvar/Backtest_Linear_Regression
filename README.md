# Kucoin Logistic Regression Trading Strategy

The provided code represents a data-driven approach to cryptocurrency trading strategy development and evaluation. Here's a general explanation of the code:

## Data Loading and Preprocessing
The code loads historical cryptocurrency price data from a CSV file and preprocesses it by removing unnecessary columns. It computes technical indicators such as Bollinger Bands and generates additional features like returns and directional signals.

## Model Training and Prediction
After preprocessing, a logistic regression model is trained using the preprocessed data to predict the directional movement of cryptocurrency prices. Input features for the model include lagged returns and Bollinger Bands derived from historical price data.

## Trading Strategy Implementation
The predicted directional signals from the trained model are used to generate trading signals. These signals are based on specific conditions derived from Bollinger Bands. The strategy determines entry points for long and short trades and dynamically sets target profit (TP) and stop-loss (SL) levels based on Bollinger Bands.

## Evaluation of Trade Performance
The effectiveness of the trading strategy is evaluated through backtesting on historical data. Various performance metrics, including total trades, profitable trades, total profit, average profit per trade, maximum drawdown, and profit factor, are calculated. The code also provides visualizations of entry, TP, and SL points on a price chart.

## Model Persistence
Finally, the trained logistic regression model is serialized and saved to a pickle file for future use. The code includes functionality to load the saved model to ensure its integrity and usability for further analysis or deployment.

![Price Chart with Entry, TP, and SL Points](plot1.png)

Next step the code defines a class called `MLTrader` that implements a machine learning-based cryptocurrency trading strategy. 

- **Imports**: The code imports necessary libraries such as pandas, numpy, ccxt for accessing cryptocurrency exchange APIs, sklearn for logistic regression modeling, and other utilities for logging and time handling.

- **MLTrader Class**: This class encapsulates the functionality required for trading based on a machine learning model.

  - **Initialization**: The constructor `__init__` initializes the trader with parameters such as the trading instrument, lag period for features, model path, trading units, and leverage. It also initializes the cryptocurrency exchange object using the ccxt library with provided API credentials.

  - **Model Loading**: The `load_model` method loads a pre-trained machine learning model from a specified path using pickle.

  - **Data Retrieval**: The `get_most_recent` method fetches historical OHLCV (open, high, low, close, volume) data for a specified number of days from the exchange API. It continuously fetches data until the specified stop condition is met.

  - **Strategy Definition**: The `define_strategy` method defines the trading strategy based on the fetched data and the loaded machine learning model. It preprocesses the data, generates lag features, computes technical indicators like Bollinger Bands, and makes predictions using the model.

  - **Execution of Trades**: The `execute_trades` method executes trades based on the defined strategy. It determines the trading signal (long, short, or neutral) based on the predicted position from the model and executes corresponding buy or sell orders on the exchange.

- **Main Loop**: The main loop continuously fetches historical data, defines the trading strategy, executes trades, and repeats the process after a specified time interval. It also handles closing any open positions before executing new trades based on the updated strategy.

This code provides a framework for implementing and executing a machine learning-based trading strategy in the cryptocurrency market. It demonstrates the integration of data retrieval, model loading, strategy definition, and trade execution functionalities.

#### Disclaimer
Please note that cryptocurrency trading involves significant risk, and past performance is not indicative of future results. This code is provided for educational and informational purposes only. Always conduct thorough research and consult with a financial advisor before making any investment decisions.
