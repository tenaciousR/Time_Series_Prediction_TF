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

### Data preprocessing 
* Any stock market ticker available in Yahoo Finance will work with these methods. Here the [SPY](https://github.com/tenaciousR/Time_Series_Prediction_TF/blob/master/spy.csv) csv is first opened and read with the program selecting only the columns in consideration, time (row 0) and close price (row 4). The values are then stored as numpy arrays now, which allows the data to take up less memory when being manipulated.
* This is then plotted on a simple graph to visualize the full data set. 
 
![image](https://user-images.githubusercontent.com/55423732/71840325-1d658000-308b-11ea-982e-4e2b091510f7.png)

* The data set is then split about 80% train, 20% validation. 
* The windowed_dataset function allows for the parameters:
* `series` : a portion of the examples in the dataset (x_train or x_validation)
* `window_size` : indicates how many data points to look at in one iteration at a time
* `batch_size` : the size set for [Stochastic Gradient Descent on TensorFlow](https://www.tensorflow.org/probability/api_docs/python/tfp/optimizer/VariationalSGD).
* `shuffle_buffer` : shuffles the data in order to prevent bias on learning the training set.

* The model_forecast function includes the parameter `model` which will be returned after training is complete. 

### Neural Network 
* The initial model is used to plot the **learning rate** vs **loss** in order to visualize the optimal learning rate for the algorithm. The learning rate is selected where the graph begins to level out and has smoother points surrounding it.
* This model contains roughly the same inputs as the model used for training, the inputs will be explained in the following steps.

![image](https://user-images.githubusercontent.com/55423732/71840351-29e9d880-308b-11ea-80d7-dd5a1f8a573e.png)

* The model used for training is a [keras sequential model](https://keras.io/getting-started/sequential-model-guide/).
* Different neural network methods are used within the model, including but not limited to:
* 1 layer of convolutions
* 2 layers of LSTM
* 3 Dense layers (including the final output layer)
* 1 [lambda layer](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Lambda?version=stable) to allow quick experimentation

* An [optimizer](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Lambda?version=stable) using SGD is used and a loss set tothe class [Huber](https://www.tensorflow.org/api_docs/python/tf/keras/losses/Huber?version=stable).
* The model is then set to run for 500 epochs.

![image](https://user-images.githubusercontent.com/55423732/71840369-353d0400-308b-11ea-90a7-53bdaac15e09.png)
