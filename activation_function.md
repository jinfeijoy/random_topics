# [Activation Function](https://www.v7labs.com/blog/neural-networks-activation-functions#:~:text=%F0%9F%93%A2%20Note%3A%20All%20hidden%20layers,prediction%20made%20by%20the%20model.)

**An Activation Function** decides whether a neuron should be activated or not. This means that it will decide whether the neuron’s input to the network is important or not in the process of prediction using simpler mathematical operations. 

All hidden layers usually use the same activation function. However, the output layer will typically use a different activation function from the hidden layers.

* Binary Step Function: It cannot provide multi-value outputs

* Linear Activation Function: also known as "no activation," or "identity function" (multiplied x1.0), is where the activation is proportional to the input.

* Non-Linear Activation Functions
    * Softmax Function
        * the Softmax function is described as a combination of multiple sigmoids.
        * It is most commonly used as an activation function for the last layer of the neural network in the case of **multi-class classification**. 
    * Sigmoid / Logistic Activation Function 
        * It is commonly used for models where we have to predict the probability as an output.
        * output range between 0 and 1
        * As the gradient value approaches zero, the network ceases to learn and suffers from the Vanishing gradient problem. not good for hidden layer
        * can be used for output layer for **binary classification** and **multilabel classification (Sigmoid)**
    * Tanh Function (Hyperbolic Tangent) 
        * Usually used in hidden layers of a neural network as its values lie between -1 to; therefore, the mean for the hidden layer comes out to be 0 or very close to it. It helps in centering the data and makes learning for the next layer much easier.
        * it also faces the problem of vanishing gradients similar to the sigmoid activation function. Plus the gradient of the tanh function is much steeper as compared to the sigmoid function.
    * ReLU Function
        * ReLU stands for Rectified Linear Unit. 
        * best activation function for hidden layer
        * other ReLU: Leaky ReLU Function, Parametric ReLU Function, Exponential Linear Units (ELUs) Function
    * Swish
        * used for hidden layer
        * Swish consistently matches or outperforms ReLU activation function on deep networks applied to various challenging domains such as image classification, machine translation etc. 
        * Swish function is used in neural networks having a depth greater than 40 layers.
    * Gaussian Error Linear Unit (GELU)
        * activation function is compatible with BERT, ROBERTa, ALBERT, and other top NLP models. This activation function is motivated by combining properties from dropout, zoneout, and ReLUs.
        * hidden layer

* Output Layer
    * Regression - Linear Activation Function
    * Binary Classification—Sigmoid/Logistic Activation Function
    * Multiclass Classification—Softmax
    * Multilabel Classification—Sigmoid

* Hidden Layer
    * Convolutional Neural Network (CNN): ReLU activation function.
    * Recurrent Neural Network: Tanh and/or Sigmoid activation function.