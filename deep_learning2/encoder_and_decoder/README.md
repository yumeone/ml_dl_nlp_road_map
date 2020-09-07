
### Encoder-Decoder Model

The encoder-decoder model is a way of using recurrent neural networks for sequence-to-sequence prediction problems.

![img.png](https://qph.fs.quoracdn.net/main-qimg-33f11b2a8d131e294caee052cc0e7e42)

The approach involves two recurrent neural networks, one to encode the input sequence, called the encoder, and a second to decode the encoded input sequence into the target sequence called the decoder.

#### How it works ?

* The encoder will read the English sentence word by word and store the final internal states (known as an intermediate vector) of the LSTM generated after the last time step and since the output will be generated once the entire sequence is read, therefore outputs (Yt) of the Encoder at each time step are discarded.

![img.png](https://miro.medium.com/max/1250/1*J-pyxBbWWT3gDJp74o_kUw.png)

*  Encoder LSTM which has the same role to play in both the training phase as well as in the inference phase, the Decoder LSTM has a slightly different role to play in both of these phases.

![img.png](https://miro.medium.com/max/1250/1*mBnKJGJWAbj45ZGW_w3Q0g.png)




#### Applications
* It possesses many applications such as
* Google’s Machine Translation
* Question answering chatbots
* Speech recognition
* Time Series Application etc.,

#### Resources :

https://arxiv.org/pdf/1409.3215.pdf

https://blog.keras.io/a-ten-minute-introduction-to-sequence-to-sequence-learning-in-keras.html

https://medium.com/analytics-vidhya/machine-translation-encoder-decoder-model-7e4867377161
