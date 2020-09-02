
### Recurrent Neural Networks:

Recurrent Neural Networks(RNN) are a type of Neural Network where the output from the previous step is fed as input to the current step.

Recurrent Neural Networks (RNN) are a class of Artificial Neural Networks that can process a sequence of inputs in deep learning and retain its state while processing the next sequence of inputs. Traditional neural networks will process an input and move onto the next one disregarding its sequence

#### Use case:

![img.png](https://miro.medium.com/max/875/1*hEa9ciQBUQcN2rtIDoK3CA.png)

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06022525/bptt.png)

formula for current cell state. 

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06004252/hidden-state.png)

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06005300/eq2.png)


output state:

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06005750/outeq.png)

First, it takes the x(t-1) from the sequence of input and then it outputs h(t-1) which together with x(t) is the input for the next step. 
So, the h(t-1) and x(t) is the input for the next step. Similarly, h(t) from the next is the input with x(t) for the next step and so on. 
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