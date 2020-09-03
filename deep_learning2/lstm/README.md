
### LSTM(Long Short Term Memory) and GRU:

LSTM networks are a type of RNN that uses special units in addition to standard units. 

* LSTM ’s and GRU’s were created as the solution to short-term memory. They have internal mechanisms called gates that can regulate the flow of information.

![img.png](https://miro.medium.com/max/875/1*yBXV9o5q7L_CvY7quJt3WQ.png)

LSTM units include a 'memory cell' that can maintain information in memory for long periods of time. ... Standard RNNs (Recurrent Neural Networks) suffer from vanishing and exploding gradient problems.

This model uses the notion of gates and has three :
* Input gate i: controls the flow of incoming information.
* Forget gate f: Controls the amount of information from the previous memory state.
* Output gate o: controls the flow of outgoing information.

To review, the Forget gate decides what is relevant to keep from prior steps. The input gate decides what information is relevant to add from the current step. The output gate determines what the next hidden state should be.

![img.png](https://i.stack.imgur.com/aTDpS.png)

* Each LSTM cell has three inputs h_{t-1},C_{t-1} and x_t and two outputs h_t and C_t. 

* For a given time t, h_t is the hidden state, C_t is the cell state or memory, x_t is the current data point or input. 

* The first sigmoid layer has two inputs–h_{t-1} and x_t where h_{t-1} is the hidden state of the previous cell. It is known as the ```forget gate``` as its output selects the amount of information of the previous cell to be included. The output is a number in [0,1] which is multiplied (point-wise) with the previous cell state C_{t-1}. Instead of squishing values between -1 and 1, it squishes values between 0 and 1. That is helpful to update or forget data because any number getting multiplied by 0 is 0, causing values to disappears or be “forgotten.” Any number multiplied by 1 is the same value therefore that value stay’s the same or is “kept.” 

* The second sigmoid layer is the ```input gate``` that decides what new information is to be added to the cell. It takes two inputs h_{t-1} and x_t. The tanh layer creates a vector C_t of the new candidate values. Together, these two layers determine the information to be stored in the cell state. 

* Their point-wise multiplication ( i_t ? C_t ) tells us the amount of information to be added to the ```cell state```. The result is then added with the result of the forget gate multiplied with previous cell state ( f_t* C_{t-1} ) to produce the current cell state C_t. 

* Next, the output of the cell is calculated using a sigmoid and a tanh layer. The sigmoid layer decides which part of the cell state will be present in the output whereas tanh layer shifts the output in the range of [-1,1]. The results of the two layers undergo point-wise multiplication to produce the output ht of the cell.


#### Drawbacks:

* the cell has become quite complex now with the additional features (such as forget gates) being brought into the picture
* LSTMs are prone to overfitting 
* LSTMs get affected by different random weight initializations


### GRU : 

GRU’s got rid of the cell state and used the hidden state to transfer information. It also only has two gates, a reset gate and update gate.


* ```Update Gate(Z_t) ``` : The update gate acts similar to the forget and input gate of an LSTM. It decides what information to throw away and what new information to add.

When x_t is plugged into the network unit,  The same goes for h_(t-1) which holds the information for the previous t-1 units ,it is multiplied by its own respective  weights W(z). Both results are added together and a sigmoid activation function is applied to squash the result between 0 and 1.

![img.png](https://miro.medium.com/max/1580/1*1HJUlwKMWmAkHhUkwy9g3g.png)

* ```Reset Gate(r_t)``` : The reset gate is another gate is used to decide how much past information to forget.This formula is the same as the one for the update gate. The difference comes in the weights and the gate’s usage. plug in h_(t-1)  and x_t , multiply them with their corresponding weights, sum the results and apply the sigmoid function.

* We introduce a new memory content(h'_t) which will use the reset gate to store the relevant information from the past.Multiply the input x_t  and h_(t-1) with a weight respective weights W.
 The text starts with “This is a fantasy book which illustrates…” and after a couple paragraphs ends with “I didn’t quite enjoy the book because I think it captures too many details.” To determine the overall level of satisfaction from the book we only need the last part of the review. In that case as the neural network approaches to the end of the text it will learn to assign r_t vector close to 0, washing out the past and focusing only on the last sentences.

* As the last step, the network needs to calculate h_t — vector which holds information for the current unit and passes it down to the network. In order to do that the update gate is needed. It determines what to collect from the current memory content — h’_t and what from the previous steps — h_(t-1).
  ##### Apply element-wise multiplication to the update gate{ z_t and h_(t-1)} and {(1-z_t) and h’_t} and sum it 
  
  Let’s bring up the example about the book review. This time, the most relevant information is positioned in the beginning of the text. The model can learn to set the vector z_t close to 1 and keep a majority of the previous information. Since z_t will be close to 1 at this time step, 1-z_t will be close to 0 which will ignore big portion of the current content (in this case the last part of the review which explains the book plot) which is irrelevant for our prediction



#### Resource:

* https://colah.github.io/posts/2015-08-Understanding-LSTMs/
* https://medium.com/@purnasaigudikandula/recurrent-neural-networks-and-lstm-explained-7f51c7f6bbb9
* https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21
* https://www.analyticsvidhya.com/blog/2017/12/fundamentals-of-deep-learning-introduction-to-lstm/
* https://medium.com/@shiyan/understanding-lstm-and-its-diagrams-37e2f46f1714
* http://nikhilbuduma.com/2015/01/11/a-deep-dive-into-recurrent-neural-networks/

* https://towardsdatascience.com/understanding-gru-networks-2ef37df6c9be


