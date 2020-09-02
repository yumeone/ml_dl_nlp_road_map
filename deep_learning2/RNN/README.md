
### Recurrent Neural Networks:

Recurrent Neural Networks(RNN) are a type of Neural Network where the output from the previous step is fed as input to the current step.

* uses:

predict the next word in a given sentence
Next word prediction.
Music composition.
Image captioning
Speech recognition
Time series anomaly detection
Stock market prediction

![img.png](https://miro.medium.com/max/875/1*NKhwsOYNUT5xU7Pyf6Znhg.png)

First, it takes the x(0) from the sequence of input and then it outputs h(0) which together with x(1) is the input for the next step. 
So, the h(0) and x(1) is the input for the next step. Similarly, h(1) from the next is the input with x(2) for the next step and so on. 
This way, it keeps remembering the context while training.
