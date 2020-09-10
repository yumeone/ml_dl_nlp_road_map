
### Recurrent Neural Networks:

Recurrent Neural Networks(RNN) are a type of Neural Network where the output from the previous step is fed as input to the current step.

Recurrent Neural Networks (RNN) are a class of Artificial Neural Networks that can process a sequence of inputs in deep learning and retain its state while processing the next sequence of inputs. Traditional neural networks will process an input and move onto the next one disregarding its sequence

* LSTM networks are a type of RNN that uses special units in addition to standard units. LSTM units include a 'memory cell' that can maintain information in memory for long periods of time. ... Standard RNNs (Recurrent Neural Networks) suffer from vanishing and exploding gradient problems


##### * RNN VIsual intuition

* A RNN takes two inputs at each time step: an input (in the case of the encoder, one word from the input sentence), and a hidden state. The word, however, needs to be represented by a vector. To transform a word into a vector, we turn to the class of methods called “word embedding” algorithms.

* The next RNN step takes the second input vector and hidden state #1 to create the output of that time step.

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/rnn.gif)

* each pulse for the encoder or decoder is that RNN processing its inputs and generating an output for that time step. Since the encoder and decoder are both RNNs, each time step one of the RNNs does some processing, it updates its hidden state based on its inputs and previous inputs it has seen.The decoder also maintains a hidden states that it passes from one time step to the next. 

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/seq2seq2.gif)

#### Use case:

![img.png](https://miro.medium.com/max/875/1*hEa9ciQBUQcN2rtIDoK3CA.png)

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06022525/bptt.png)

formula for current cell state. 

RNN cell takes in two inputs, output from the last hidden state{h(t-1} and observation at time = t x(t)

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06004252/hidden-state.png)

```ht -> current state,ht-1 -> previous state,xt -> input state```

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06005300/eq2.png)

```whh -> weight at recurrent neuron,wxh -> weight at input neuron```

output state:

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2017/12/06005750/outeq.png)

```Yt -> output,Why -> weight at output layer```

First, it takes the x(t-1) from the sequence of input and then it outputs h(t-1) which together with x(t) is the input for the next step. 
So, the h(t-1) and x(t) is the input for the next step. Similarly, h(t) from the next is the input with x(t) for the next step and so on. 
This way, it keeps remembering the context while training.

#### Advantages of an RNN

* It can model non-linear temporal/sequential relationships.
* No need to specify lags to predict the next value in comparison to and autoregressive process.

#### Disadvantages of an RNN

* Recurrent Neural Networks suffer from short-term memory. If a sequence is long enough, they’ll have a hard time carrying information from earlier time steps to later ones. So if you are trying to process a paragraph of text to do predictions, RNN’s may leave out important information from the beginning.

* During back propagation, recurrent neural networks suffer from the vanishing gradient problem. Gradients are values used to update a neural networks weights. The vanishing gradient problem is when the gradient shrinks as it back propagates through time. If a gradient value becomes extremely small, it doesn’t contribute too much learning

#### Resources: 

https://towardsdatascience.com/recurrent-neural-networks-rnn-explained-the-eli5-way-3956887e8b75
https://towardsdatascience.com/recurrent-neural-networks-b7719b362c65

https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-recurrent-neural-networks
