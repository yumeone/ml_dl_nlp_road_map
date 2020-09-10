
## Transfomers

###  ```Resources :```

<a href = 'http://jalammar.github.io/illustrated-transformer/'>The Illustrated Transformer by Jay</a>

<a href = 'https://arxiv.org/pdf/1706.03762.pdf'> Attention all you need </a>


### Basics :

#### * seq2seq.

A sequence-to-sequence model is a model that takes a sequence of items (words, letters, features of an images…etc) and outputs another sequence of items. A trained model would work like this,
* The encoder processes each item in the input sequence, it compiles the information it captures into a vector (called the context). After processing the entire input sequence, the encoder sends the context over to the decoder, which begins producing the output sequence item by item


![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/seq2seq.gif)

#### * RNN

* A RNN takes two inputs at each time step: an input (in the case of the encoder, one word from the input sentence), and a hidden state. The word, however, needs to be represented by a vector. To transform a word into a vector, we turn to the class of methods called “word embedding” algorithms.

* The next RNN step takes the second input vector and hidden state #1 to create the output of that time step.

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/rnn.gif)

* each pulse for the encoder or decoder is that RNN processing its inputs and generating an output for that time step. Since the encoder and decoder are both RNNs, each time step one of the RNNs does some processing, it updates its hidden state based on its inputs and previous inputs it has seen.The decoder also maintains a hidden states that it passes from one time step to the next. 

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/seq2seq2.gif)


#### * Attention model : 

* model isn’t just mindless aligning the first word at the output with the first word from the input. It actually learned from the training phase how to align words in that language pair.

* the encoder passes a lot more data to the decoder. Instead of passing the last hidden state of the encoding stage, the encoder passes all the hidden states to the decoder:

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/attention.gif)

```How attention works ?```

* The attention decoder RNN takes in the embedding of the <END> token, and an initial decoder hidden state(h_init).
* The RNN processes its inputs, producing an output and a new hidden state vector (h4). The output is discarded.
* Attention Step: We use the encoder hidden states and the h4 vector to calculate a context vector (C4) for this time step.
* We concatenate h4 and C4 into one vector.
* We pass this vector through a feedforward neural network (one trained jointly with the model).
* The output of the feedforward neural networks indicates the output word of this time step.
* Repeat for the next time steps.
  
  ![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/ezgif.com-video-to-gif.gif)

![img.png](https://github.com/Uttam580/ml_dl_nlp_road_map/blob/master/deep_learning2/basic_transfomers/gif/ezgif.com-video-to-gif.gif)








