
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

### Transformers

```Transformers do not require that the sequential data be processed in the order. For example, if the input data is a natural language sentence, the Transformer does not need to process the beginning of it before the end. Due to this feature, the Transformer allows for much more parallelization than RNNs and therefore reduced training times.```

###### Basic
* Transformers are based on an encoder-decoder architecture that comprises of encoders which consists of a set of encoding layers that processes the input iteratively one layer after another and decoders that consists of a set of decoding layers that does the same thing to the output of the encoder.

![img.png](https://miro.medium.com/max/875/1*V2435M1u0tiSOz4nRBfl4g.png)


So, when we pass a sentence into a transformer, it is embedded and passed into a stack of encoders. The output from the final encoder is then passed into each decoder block in the decoder stack. The decoder stack then generates the output.

![img.png](https://deepfrench.gitlab.io/deep-learning-project/resources/transformer.png)

* Each ```encoder``` consists of two layers: Self-attention and a feed Forward Neural Network.Helps the encoder look at other words in the input sentence as it encodes a specific word

![img.png](http://jalammar.github.io/images/t/Transformer_decoder.png)

* The ```decoder``` has both those layers, but between them is an attention layer that helps the decoder focus on relevant parts of the input sentence.The Encoder-Decoder Attention layer works just like multiheaded self-attention, except it creates its Queries matrix from the layer below it, and takes the Keys and Values matrix from the output of the encoder stack. The remaining 2 layers work exactly the same as those in the encoder cell.

![img.png](https://miro.medium.com/max/875/1*l4iIupatrLqKgaJR7BgdBg.png)

###### self attention
* As the model processes each word (each position in the input sequence), ```self attention``` allows it to look at other positions in the input sequence for clues that can help lead to a better encoding for this word.

  EX: The animal didn't cross the street because it was too tired.

  When the model is processing the word “it”, self-attention allows it to associate “it” with “animal”

  1. The first step is to calculate the Query, Key, and Value matrices. We do that by packing our embeddings into a matrix X, and multiplying it by the weight matrices we’ve          trained (WQ, WK, WV)
  
 ![img.png](https://i.vimeocdn.com/video/824107246.jpg?mw=1920&mh=1080&q=70)
  
   dk is  the column-dimension of vectors Q, K, V.
   
 * ```Position encoding:``` since the self-attention layer does not distinguish the item order in a sequence, a positional encoding layer is used to add sequential information into each sequence item.
 
 
 ###### Deocder
 
 * The input to the decoder stack is sequential unlike the simultaneous input in encoder stack, meaning the first output word is passed into the decoder as an input using which it generates the second output now this output is again passed as an input to the decoder and using that it generates the third output and so on…
 
 * The encoder start by processing the input sequence. The output of the top encoder is then transformed into a set of attention vectors K and V. These are to be used by each decoder in its “encoder-decoder attention” layer which helps the decoder focus on appropriate places in the input sequence:

![img.png](http://jalammar.github.io/images/t/transformer_decoding_1.gif)

* After finishing the encoding phase, we begin the decoding phase. Each step in the decoding phase outputs an element from the output sequence (the English translation sentence in this case).
The following steps repeat the process until a special symbol is reached indicating the transformer decoder has completed its output. The output of each step is fed to the bottom decoder in the next time step, and the decoders bubble up their decoding results just like the encoders did. And just like we did with the encoder inputs, we embed and add positional encoding to those decoder inputs to indicate the position of each word.

![img.png](http://jalammar.github.io/images/t/transformer_decoding_2.gif)

###### Final Linear and Softmax Layer

* The output of the decoders is passed into a linear layer with softmax activation using which, the correct word is predicted.

![img.png](https://miro.medium.com/max/1250/1*ERDmCo4ihoB7Vntth88DOw.png)

* Once the transformer predicts a word using forward propagation, the prediction is compared with the actual label using a loss function like cross-entropy and then all the trainable parameters are updated using back-propagation.

















