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

	•	Date – The trading date. Can be transformed into additional features like day of the week, month, or seasonal cycles.
	•	Open – The opening price. The first price at which the stock was traded during the day.
	•	High – The highest price. The maximum price reached by the stock during the trading day.
	•	Low – The lowest price. The minimum price reached by the stock during the trading day.
	•	Close – The closing price. The last price at which the stock was traded during the day; usually the most important column for prediction.
	•	Volume – The trading volume. The total number of shares traded during the day; indicates the level of market activity.

# Model Architecture
	•	CNN Layer: Extracts spatial features from sequential data.
	•	Conv1D with 64 output channels
	•	ReLU activation
	•	MaxPool1D for dimensionality reduction
	•	LSTM Layer: Captures temporal dependencies .
	•	Hidden size: 128
	•	Dropout: 0.4
	•	Fully Connected Layer: Outputs probability using Sigmoid activation for binary classification.

# Training Configuration
	•	Epochs: 50
	•	Batch size: 64
	•	Optimizer: Adam (lr = 0.001)
	•	Loss function: Binary Cross Entropy (BCE)
	•	Dropout applied to LSTM output to reduce overfitting.
	
    The training process was configured with 50 epochs, meaning the model iterates over the entire dataset 50 times to improve its performance and learn patterns effectively. The model is deployed on the available hardware using PyTorch's device management. If a GPU (CUDA) is available, it is utilized to accelerate training; otherwise, the CPU is used. This ensures efficient computation depending on the system capabilities.
    The architecture used is a hybrid CNN-LSTM model, which is transferred to the selected device to maintain consistency between the model and input data during training.
    For the loss function, Binary Cross Entropy Loss (BCELoss) is applied. This loss function is suitable for binary classification tasks, where the output is expected to be a probability between 0 and 1.
    The optimization process is handled using the Adam optimizer, which is known for its efficiency and adaptive learning capabilities. A learning rate of 0.001 is used to balance convergence speed and stability during training.
    Overall, this setup ensures a stable and efficient training process for the binary classification model.


# Results
	•	Training Accuracy: 83.10%
	•	Test Accuracy: 77.66%

The results show that the model learned well from training data and generalizes reasonably to test data, capturing meaningful patterns in stock price trends.

Notes
	•	Using multi-day future labeling reduces daily noise in stock price movement, improving model performance.
	•	Accuracy can be further improved by adding technical indicators or features derived from dates, such as weekday, month, or seasonal cycles.
