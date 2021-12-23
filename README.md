# Quantum-machine-learning-project

Here is my final project for quantum machine learning course.

# Introduction

Quantum machine learning is a new sphere in computer science. This field developing so quickly that I decided to make my own project. The project conststs of two parts : feature extractor and quantum classifier. The idea of the project was taken from [this](https://towardsdatascience.com/hybrid-quantum-neural-network-for-reduced-mnist-data-840897ad08a) article.

# Overview

The project consists of two tasks: 
1. Extract features from images
2. Classify features with quantum classifier

For feature extracting I used fully-connected autoencoder. I tried to decode image in latent space and decode it back with minimal losses.
For classification I used StronglyEntanglingLayer from pennylane and fully connected layer with 10 neurons as output.

A StronglyEntanglingLayer applying rotations on each qubit followed by cascades of 2-qubit entangling gates.

The 2-qubit or imprimitive gates act on each qubit i chronologically. The second qubit for each gate is determined by (i+r)modn, where n is equal to len(wires) and range a layer hyperparameter called the range.

This is an example of two 4-qubit strongly entangling layers (ranges r=1 and r=2, respectively) with rotations R and RYs as imprimitives

# Technical details

1. Feature extractor

The features embedding size consists of 64 layers and here is some images for example of decoding:
![image](https://user-images.githubusercontent.com/32843048/147247680-bbefdc5b-7411-4118-8e99-db9f602c6838.png)

2. Quantum classifier

1. Before sending features to quantum layer we should make normalizing of input to [-1;1].
2. We apply technic called “Data re-uploading” which consists on sampling the input data several times into the network. 

# Results

My quantum classifier shows accuracy over 85% that is good result for that task and such low number of qubits.

19/19 [==============================] - 152s 8s/step - loss: 0.3431 - categorical_accuracy: 0.8517


