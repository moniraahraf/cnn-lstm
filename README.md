## Netflix Stock Prediction using CNN-LSTM

# Overview

This project implements a CNN-LSTM hybrid model to predict the future trend of Netflix stock prices. The model is designed for classification, determining whether the stock price will increase (1) or decrease (0) after a specified future step.

The approach combines:
	•	CNN (Convolutional Neural Network) for feature extraction from sequential stock data.
	•	LSTM (Long Short-Term Memory) for temporal pattern learning and classification.

# Dataset
	•	The dataset used is historical Netflix stock prices.
	•	Selected features: Open, High, Low, Close, Volume.
	•	Preprocessing includes:
	•	Normalization using MinMaxScaler.
	•	Creating sequences of length 20 (seq_length = 20).
	•	Labeling based on future 5-day trend (future_step = 5).

# Explanation of Dataset Columns

    Date – The trading date. Can be transformed into additional features like day of the week, month, or seasonal cycles.
    Open – The opening price. The first price at which the stock was traded during the day.
	Close – The closing price. The last price at which the stock was traded during the day; usually the most important column for prediction.
    High – The highest price. The maximum price reached by the stock during the trading day.
    Low – The lowest price. The minimum price reached by the stock during the trading day.
    Volume – The trading volume. The total number of shares traded during the day; indicates the level of market activity.

# Model Architecture
	•	CNN Layer: Extracts spatial features from sequential data.
	•	Conv1D with 64 output channels
	•	ReLU activation
	•	MaxPool1D for dimensionality reduction
	•	LSTM Layer: Captures temporal dependencies and for classification .
	•	Hidden size: 128
	•	Dropout: 0.4

# Training Configuration
	•	Epochs: 50
	•	Batch size: 64
	•	Optimizer: Adam (lr = 0.001)
	•	Loss function: Binary Cross Entropy (BCE)
	•	Dropout applied to LSTM output to reduce overfitting.

# Results
	•	Training Accuracy: 83.10%
	•	Test Accuracy: 77.66%

The results show that the model learned well from training data and generalizes reasonably to test data, capturing meaningful patterns in stock price trends.

Notes
	•	Using multi-day future labeling reduces daily noise in stock price movement, improving model performance.
	•	Accuracy can be further improved by adding technical indicators or features derived from dates, such as weekday, month, or seasonal cycles.
