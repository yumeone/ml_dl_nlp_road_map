  ## Attention model
  
  #### Seq2Seq Model problem : 
  The seq2seq model normally has an encoder-decoder architecture, composed of:

* An encoder processes the input sequence and compresses the information into a context vector (also known as sentence embedding or “thought” vector) of a fixed length. This representation is expected to be a good summary of the meaning of the whole source sequence.

* A decoder is initialized with the context vector to emit the transformed output. The early work only used the last state of the encoder network as the decoder initial state.
Both the encoder and decoder are recurrent neural networks, i.e. using LSTM or GRU units.

![img.png](https://lilianweng.github.io/lil-log/assets/images/encoder-decoder-example.png)

*```A critical and apparent disadvantage of this fixed-length context vector design is incapability of remembering long sentences. Often it has forgotten the first part once it completes processing the whole input.``` 


#### Attention model: 

*  it was born to help memorize long source sentences in neural machine translation (NMT)Instead of encoding the input sequence into a single fixed context vector, the attention model develops a context vector that is filtered specifically for each output time step.

![img.png](https://lilianweng.github.io/lil-log/assets/images/encoder-decoder-attention.png)

##### How it works: 
* we have a source sequence x of length n and try to output a target sequence y of length m:

* The encoder is a bidirectional RNN (or other recurrent network setting of your choice) with a forward hidden state h→i and a backward one h←i. A simple concatenation of two represents the encoder state. The motivation is to include both the preceding and following words in the annotation of one word.

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image9.png)


#### Resources :
 
 
<a href = 'https://arxiv.org/pdf/1409.0473.pdf'>NEURAL MACHINE TRANSLATIONBY JOINTLY LEARNING TO ALIGN AND TRANSLATE</a>
