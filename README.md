# cnn-lstm

CNN-LSTM Model for Stock Price Direction Prediction
	1.	Overview
This project aims to predict the next-day stock price direction (up or down) using a hybrid deep learning model that combines CNN and LSTM.
CNN is used as a feature extractor to capture local patterns in the data, while LSTM is used to learn temporal dependencies and perform the prediction.
The final classification layer (Fully Connected layer) is frozen, so the model mainly relies on LSTM for learning.

⸻

	2.	Data Preprocessing
The following features are used:

	•	Adjusted Close Price
	•	Volume
	•	Daily Return (percentage change)

The data is normalized using MinMaxScaler.
The dataset is converted into sequences with a length of 120 time steps.

Label definition:
	•	1 → price goes up
	•	0 → price goes down

⸻

	3.	Model Architecture
Input → CNN → LSTM → FC (Frozen) → Output

CNN:
Used as a feature extractor to capture local patterns and reduce noise.

LSTM:
Learns long-term dependencies in the time series and is the main component responsible for prediction.

Fully Connected Layer:
Used for final output, but it is frozen (not trainable).

⸻

	4.	Hyperparameters
Batch Size: 32
Epochs: 60
Hidden Size: 256
Learning Rate: 0.0005
Dropout: 0.3
Sequence Length: 120

⸻

	5.	Training Details
Loss Function: Binary Cross Entropy with Logits
Optimizer: Adam
Only parameters with requires_grad=True are updated during training.
The Fully Connected layer is frozen.

⸻

	6.	Results
Training Accuracy: 61.82%
Testing Accuracy: 57.84%

⸻


	7.	Analysis
The accuracy is relatively low, which is expected because:

	•	The dataset is small
	•	Stock market data is highly noisy and difficult to predict

The small gap between training and testing accuracy indicates there is no strong overfitting.
However, performance is still close to random guessing, so the model needs improvement.

⸻

	8.	Possible Improvements

	•	Increase dataset size
	•	Freeze CNN completely for better feature extraction
	•	Add more features (technical indicators)
	•	Tune hyperparameters
	•	Use attention mechanisms with LSTM

⸻

Final Conclusion
The model demonstrates basic learning capability, but performance is limited due to the small dataset and complexity of stock prediction.
The CNN-LSTM architecture is a solid starting point and can be improved further.
