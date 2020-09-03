
### LSTM(Long Short Term Memory):

LSTM networks are a type of RNN that uses special units in addition to standard units. LSTM units include a 'memory cell' that can maintain information in memory for long periods of time. ... Standard RNNs (Recurrent Neural Networks) suffer from vanishing and exploding gradient problems.

This model uses the notion of gates and has three :
* Input gate i: controls the flow of incoming information.
* Forget gate f: Controls the amount of information from the previous memory state.
* Output gate o: controls the flow of outgoing information.

To review, the Forget gate decides what is relevant to keep from prior steps. The input gate decides what information is relevant to add from the current step. The output gate determines what the next hidden state should be.

![img.png](https://i.stack.imgur.com/aTDpS.png)

* Each LSTM cell has three inputs h_{t-1},C_{t-1} and x_t and two outputs h_t and C_t. 

* For a given time t, h_t is the hidden state, C_t is the cell state or memory, x_t is the current data point or input. 

* The first sigmoid layer has two inputs–h_{t-1} and x_t where h_{t-1} is the hidden state of the previous cell. It is known as the forget gate as its output selects the amount of information of the previous cell to be included. The output is a number in [0,1] which is multiplied (point-wise) with the previous cell state C_{t-1}.

* The second sigmoid layer is the input gate that decides what new information is to be added to the cell. It takes two inputs h_{t-1} and x_t. The tanh layer creates a vector C_t of the new candidate values. Together, these two layers determine the information to be stored in the cell state. Their point-wise multiplication ( i_t ? C_t ) tells us the amount of information to be added to the cell state. The result is then added with the result of the forget gate multiplied with previous cell state ( f_t* C_{t-1} ) to produce the current cell state C_t. 

* Next, the output of the cell is calculated using a sigmoid and a tanh layer. The sigmoid layer decides which part of the cell state will be present in the output whereas tanh layer shifts the output in the range of [-1,1]. The results of the two layers undergo point-wise multiplication to produce the output ht of the cell.


#### Drawbacks:

* the cell has become quite complex now with the additional features (such as forget gates) being brought into the picture
* LSTMs are prone to overfitting 
* LSTMs get affected by different random weight initializations

#### Resource:

* https://colah.github.io/posts/2015-08-Understanding-LSTMs/
* https://medium.com/@purnasaigudikandula/recurrent-neural-networks-and-lstm-explained-7f51c7f6bbb9
* https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21
* https://www.analyticsvidhya.com/blog/2017/12/fundamentals-of-deep-learning-introduction-to-lstm/
* https://medium.com/@shiyan/understanding-lstm-and-its-diagrams-37e2f46f1714
* http://nikhilbuduma.com/2015/01/11/a-deep-dive-into-recurrent-neural-networks/


