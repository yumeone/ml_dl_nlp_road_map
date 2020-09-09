  ## Attention model
  
  
#### Resources :
 
 
<a href = 'https://arxiv.org/pdf/1409.0473.pdf'>Neural_machine_translationby_jointly_learning_to_align_and_trnsalate</a>

<a href = 'https://arxiv.org/pdf/1502.03044.pdf'>Soft and Hard Attention</a>

< a href = 'https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/'>seq2seq model by jay</a>
  
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
 all the vectors h1,h2,h3…., hTx are representations of Tx number of words in the input sentence.

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image9.png)

* The weights are also learned by a feed-forward neural network .The context vector ci for the output word yi is generated using the weighted sum of the annotations:

![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image8.png)

 The weights αij are computed by a softmax function given by the following equation.The set of {αt,i} are weights defining how much of each source hidden state should be considered for each output
 
 ![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image11.png)
 
 ![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image10.png)
 
 eij is the output score of a feedforward neural network described by the function a that attempts to capture the alignment between input at j and output at i.
 
 #### Global and local attention :
 
 Global and Local Attention mechanism. Global Attention considers all hidden states (blue) whereas local Attention considers only a subset:
 
 * When a “global” Attention layer is applied, a lot of computation is incurred. This is because all the hidden states must be taken into consideration, concatenated into a matrix, and multiplied with a weight matrix of correct dimensions to get the final layer of the feedforward connection.
 
 ![img.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2019/11/image26.png)





```Soft Attention is the global Attention where all image patches are given some weight; but in hard Attention, only one image patch is considered at a time```
