
### Encoder-Decoder Model

The encoder-decoder model is a way of using recurrent neural networks for sequence-to-sequence prediction problems.

![img.png](https://qph.fs.quoracdn.net/main-qimg-33f11b2a8d131e294caee052cc0e7e42)

The approach involves two recurrent neural networks, one to encode the input sequence, called the encoder, and a second to decode the encoded input sequence into the target sequence called the decoder.

#### How it works ?

* The encoder will read the English sentence word by word and store the final internal states (known as an intermediate vector) of the LSTM generated after the last time step and since the output will be generated once the entire sequence is read, therefore outputs (Yt) of the Encoder at each time step are discarded.

![img.png](https://miro.medium.com/max/1250/1*J-pyxBbWWT3gDJp74o_kUw.png)

*  Encoder LSTM which has the same role to play in both the training phase as well as in the inference phase, the Decoder LSTM has a slightly different role to play in both of these phases.

*  initial states (h0, c0) of the decoder are set to the final states of the encoder. This intuitively means that the decoder is trained to start generating the output sequence depending on the information encoded by the encoder.```We use a technique called “Teacher Forcing” wherein the input at each time step is given as the actual output (and not the predicted output) from the previous time step.```.

```During Trainning```
![img.png](https://miro.medium.com/max/1250/1*mBnKJGJWAbj45ZGW_w3Q0g.png)

* In the first time step we provide the START_ token so that the decoder starts generating the next token (the actual first word of Marathi sentence). And after the last word in the Marathi sentence, we make the decoder learn to predict the _END token. This will be used as the stopping condition during the inference procedure.Finally the loss is calculated on the predicted outputs from each time step and the errors are back propagated through time in order to update the parameters of the network. 

```Summarizing the encoder-decoder```
![img.png](https://miro.medium.com/max/1250/1*R8c4QECLVCQ8uYhZxP7mAQ.png)

```During Inference```
![img.png](https://miro.medium.com/max/1250/1*y3fNvBFJibYF7sVz4FRE0Q.png)

* During inference, we generate one word at a time. Thus the Decoder LSTM is called in a loop, every time processing only one time step.The initial states of the decoder are set to the final states of the encoder.The initial input to the decoder is always the START_ token. At each time step, we preserve the states of the decoder and set them as initial states for the next time step.At each time step, the predicted output is fed as input in the next time step.We break the loop when the decoder predicts the END_ token.


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
