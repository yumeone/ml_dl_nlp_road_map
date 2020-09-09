  ## Attention model
  
  #### Seq2Seq Model problem : 
  The seq2seq model normally has an encoder-decoder architecture, composed of:

* An encoder processes the input sequence and compresses the information into a context vector (also known as sentence embedding or “thought” vector) of a fixed length. This representation is expected to be a good summary of the meaning of the whole source sequence.

* A decoder is initialized with the context vector to emit the transformed output. The early work only used the last state of the encoder network as the decoder initial state.
Both the encoder and decoder are recurrent neural networks, i.e. using LSTM or GRU units.

![img.png](https://lilianweng.github.io/lil-log/assets/images/encoder-decoder-example.png)

*```A critical and apparent disadvantage of this fixed-length context vector design is incapability of remembering long sentences. Often it has forgotten the first part once it completes processing the whole input.``` 
