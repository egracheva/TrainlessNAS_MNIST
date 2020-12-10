# TrainlessNAS_MNIST
Trainless NAS metric search

This repository contains files to reproduce the training of the reduced MNIST dataset.
The training is performed using a set of 2 layer vanilla neural networks, compiled with Keras.

The number of units in each of two hidden layers is set to be one of the 12 values:
[8,16,24,32,56,64,96,128,256,512,1024,2048], with a total of 144 architectures.

These architectures are trained for 200 epochs with 100 different seeds. The final weights are fixed for the 
epoch showing thelowest validation error (not taking into account the first 50 epochs).

Before the training, the untrained accuracy (after a single forward pass) is assessed for the union
of training and validation set, for each seed. We use this data to find the optimal predictive
metric for the final accuracy, wich turns out to be the relative standard deviation of the untrained accuracy.

In other words, the untrained accuracy's standard deviation divided by its mean allows to distinguish
one of the best performing architectures.

No need to train the model to know it's future performance.
We continue digging in this direction...
