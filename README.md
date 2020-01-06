# Time Series Prediction using TensorFlow

## Introduction
* In this Google Colab notebook [TensorFlow](https://www.tensorflow.org/) and [Keras](https://keras.io/) are used to implement machine learning techniques of [Convolutional Neural Networks](https://www.tensorflow.org/tutorials/images/cnn), Recurrent NN such as [Long Short Term Memory](https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM?version=stable), and [Dense Neural Networks](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Dense?version=stable).

## Setup/Usage
* Required packages include [Numpy](https://numpy.org/), [matplotlib](https://matplotlib.org/), and a csv reader to extract the information of the chosen stock price from [Yahoo Finance](https://finance.yahoo.com/quote/SPY/history?p=SPY) data (this example evaluates the SPY index fund, therefore the link will lead to that historical data that may be downloaded). 
* The [csv file in use](https://github.com/tenaciousR/Time_Series_Prediction_TF/blob/master/spy.csv) contains the date, open, high, low, close, and adjusted close. The values saved from this are the **date and close value.**

## Process

Stock prediction using TensorFlow; utilizing methods of LSTM, DNN and CNN.
