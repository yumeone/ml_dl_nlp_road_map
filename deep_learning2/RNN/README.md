
### Recurrent Neural Networks:

Recurrent Neural Networks(RNN) are a type of Neural Network where the output from the previous step is fed as input to the current step.

Recurrent Neural Networks (RNN) are a class of Artificial Neural Networks that can process a sequence of inputs in deep learning and retain its state while processing the next sequence of inputs. Traditional neural networks will process an input and move onto the next one disregarding its sequence

#### Use case:

![img.png](https://miro.medium.com/max/875/1*hEa9ciQBUQcN2rtIDoK3CA.png)

![img.png](https://miro.medium.com/max/875/1*NKhwsOYNUT5xU7Pyf6Znhg.png)

First, it takes the x(0) from the sequence of input and then it outputs h(0) which together with x(1) is the input for the next step. 
So, the h(0) and x(1) is the input for the next step. Similarly, h(1) from the next is the input with x(2) for the next step and so on. 
This way, it keeps remembering the context while training.

#### Advantages of an RNN

* It can model non-linear temporal/sequential relationships.
* No need to specify lags to predict the next value in comparison to and autoregressive process.

#### Disadvantages of an RNN

* Vanishing Gradient Problem,As more layers containing activation functions are added, the gradient of the loss function approaches zero
* Not suited for predicting long horizons

#### Resources: 

https://towardsdatascience.com/recurrent-neural-networks-rnn-explained-the-eli5-way-3956887e8b75
https://towardsdatascience.com/recurrent-neural-networks-b7719b362c65

https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-recurrent-neural-networks
