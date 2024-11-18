## Introduction
In this project I trained a LSTM (Long Short Term Memory) recurrent neural network with 3 layers to predict future stock closing prices. I have experience in implementing variety of data science algorithms such as linear regression and k-nearest neighbours but this is my first project using Tensorflow and Sequential Machine Learning models, hence many features were adapted from this [tutorial](https://www.youtube.com/watch?v=PuZY9q-aKLw&t=1099s&ab_channel=NeuralNine).

**Data Fetching and Preprocessing:** Queried historical stock data in the range of start and end with the yFinance. Fit and transformed the data using Scikit’s MinMaxScaler after reshaping it into a 2D array with one column including Closing Price data. Set the amount of prediction days and prepared the training data sets. The training the data is then converted into a 3D numPy array to allow for reshaping with the third dimension as 1 since it only represents one type of data, Closing Price.

**Model Building:** The sequential model was built with the Tensorflow.Keras Sequential API consisting of 3 LTSM layers with 50 neurons each. A dropout of 20% is applied to each layer to avoid overfitting until the final Dense layer is processed to provide the prediction for the next day’s price. The Adam (Adaptive Moment Estimation) optimizer is used to adjust the weights of the neural network so that the Mean Squared Error loss function is minimized. The model is then trained with 25 epochs and a batch size of 32 to prevent overfitting by seeing more diverse subsets.

**Back Testing Model:** Unseen stock data is then loaded from yFinance and concatenated horizontally with numPy. The model then predicts the Closing Prices in the range and the results are inverse transformed. Finally, a plot of predicted data (red) and actual data (black) are displayed using Matplotlib to create intuitive data visualizations.

**Analysis and Application:** Since the model uses historical closing prices for training, it is proficient in predicting price trends, but falls short when it comes to real-world shifts. For instance, the model can predict the Adidas stock with an R^2 of 0.97, but when examining the NVDA graph, the model predicts an average trend whereas the stock skyrockets due to advancements in artificial intelligence. When predicting the closing price of an Index Fund such as the SP500, it achieves an R^2 of 0.89, and can be seen falling short in recent years which is also likely due to the boom in technology stocks. I also implemented a feature to predict tomorrow's stock price by using data from the past 90 days. Although the model is good at predicting price trends, it dont believe that it is effective in predicting exact closing prices.

![Adidas Predictor](https://github.com/user-attachments/assets/c9e98c1b-46f2-4657-914b-af91f5e00211)

![NVDA Prediction](https://github.com/user-attachments/assets/a861d670-ad49-4698-b5de-64916cd43e09)

![SP500 Prediction](https://github.com/user-attachments/assets/c00513da-ef29-4bf0-8e90-db55808cdf2b)



