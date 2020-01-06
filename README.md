# Time Series Prediction using TensorFlow

## Introduction
* In this Google Colab notebook [TensorFlow](https://www.tensorflow.org/) and [Keras](https://keras.io/) are used to implement machine learning techniques of [Convolutional Neural Networks](https://www.tensorflow.org/tutorials/images/cnn), Recurrent NN such as [Long Short Term Memory](https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM?version=stable), and [Dense Neural Networks](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Dense?version=stable).
* The goal of this project is to predict the series of values of the SPY index by splitting the data into a training set and validation set to determine accuracy based on [mean absolute error](https://www.tensorflow.org/api_docs/python/tf/compat/v1/metrics/mean_absolute_error).
* The final steps include plotting the **training** vs **validation** losses per epoch in order to visually represent the accuracy of the system, allowing tweaks to variables such as `window_size` and `batch_size` as well as filters within the keras model. 

## Setup/Usage
* [TensorFlow 2.x](https://www.tensorflow.org/guide/effective_tf2) is required to have access to [eager execution](https://www.tensorflow.org/guide/eager) abilities.
* Required packages include [Numpy](https://numpy.org/), [matplotlib](https://matplotlib.org/), and a csv reader to extract the information of the chosen stock price from [Yahoo Finance](https://finance.yahoo.com/quote/SPY/history?p=SPY) data (this example evaluates the SPY index fund, therefore the link will lead to that historical data that may be downloaded). 
* The [csv file](https://github.com/tenaciousR/Time_Series_Prediction_TF/blob/master/spy.csv) containing the SPY price data includes the date, open, high, low, close, and adjusted close. The values saved and used in the neural netwowrk are the **date** and **close** values between 2016-11-28 to 2019-12-27.

## Process

Stock prediction using TensorFlow; utilizing methods of LSTM, DNN and CNN.
