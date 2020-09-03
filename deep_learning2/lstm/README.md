
### LSTM(Long Short Term Memory):

LSTM networks are a type of RNN that uses special units in addition to standard units. LSTM units include a 'memory cell' that can maintain information in memory for long periods of time. ... Standard RNNs (Recurrent Neural Networks) suffer from vanishing and exploding gradient problems.

This model uses the notion of gates and has three :
* Input gate i: controls the flow of incoming information.
* Forget gate f: Controls the amount of information from the previous memory state.
* Output gate o: controls the flow of outgoing information.

To review, the Forget gate decides what is relevant to keep from prior steps. The input gate decides what information is relevant to add from the current step. The output gate determines what the next hidden state should be.

![img.png](https://i.stack.imgur.com/aTDpS.png)


#### Resource:

* https://colah.github.io/posts/2015-08-Understanding-LSTMs/
* https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21
