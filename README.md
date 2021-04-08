# ANN1
Artificial Neural Network to estimate Customer churn in a bank
1. We are using ANN to estimate the Customer Churn in a bank.
2. The first 3 features should have no significance on the modelling and thus can be removed from our model.
3. There are no missing values in our data
4. We have some categorical columns that need to be encoded using one-hot-encoding and label encoder.
5. LabelEncoder can turn [dog,cat,dog,mouse,cat] into [1,2,1,3,2], but then the imposed ordinality means that the average of dog and mouse is cat. Still there are algorithms like decision trees and random forests that can work with categorical variables just fine and LabelEncoder can be used to store values using less disk space.

6.One-Hot-Encoding has the advantage that the result is binary rather than ordinal and that everything sits in an orthogonal vector space. The disadvantage is that for high cardinality, the feature space can really blow up quickly and you start fighting with the curse of dimensionality. In these cases, I typically employ one-hot-encoding followed by PCA for dimensionality reduction. I find that the judicious combination of one-hot plus PCA can seldom be beat by other encoding schemes. PCA finds the linear overlap, so will naturally tend to group similar features into the same feature.
7.Scaling the data in a neural network gives it a smaller working range and thus in turn increases its accuracy and we have used standard scaler to scale our data. We subtract the mean and divide by the standard deviation.
8.Note here that : Since keras 2.0 it has been integrated into TensorFlow
9.Deciding the number of neurons in the hidden layers need to be experimented with.(Part of training our hyperparameters)
10.As we have just a binary output, we just need a single neuron at the end. The output layer needs the sigmoid function as the activation function.
11.Sequential specifies to keras that we are creating model sequentially and the output of each layer we add is input to the next layer we specify.
12.Due to the binary output we will use binary_crossentropy as the loss function.
13.We are performing batch learning here. Usually taken as 32.
14.The complete picture here shows here that the recall(sensitivity) is pretty low here owing to the low number of values for the people who have churned. This makes the model follow more closely the entries for the non-churners and not so much with the ones that have. This kind of problem needs to be solved using oversampler or undersamplers.
