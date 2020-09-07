
### Generative adversarial network(GAN)

Given a training set, this technique learns to generate new data with the same statistics

* Generative models can generate new data instances.

* Discriminative models discriminate between different kinds of data instances.

![img.png](https://miro.medium.com/max/1394/1*fd3QUV45REqZ_f7tjYs31g.png)


### How it works ?

* In GANs, there is a generator and a discriminator. The Generator generates fake samples of data(be it an image, audio, etc.) and tries to fool the Discriminator.

* The ```discriminator``` looks at real images (training samples) and generated images separately. It distinguishes whether the input image to the discriminator is real or generated. The output D(X) is the probability that the input x is real, i.e. P(class of input = real image).
  We train the discriminator just like a deep network classifier. If the input is real, we want D(x)=1. If it is generated, it should be zero{D(x)=0}. Through this process, the discriminator identifies features that contribute to real images.

![img.png](https://miro.medium.com/max/875/1*_uFUaxXIEjCDm_UTzbyleA.png)

* we want the ```generator``` to create images with D(x) = 1 (matching the real image). So we can train the generator by backpropagation this target value all the way back to the generator, i.e. we train the generator to create images that towards what the discriminator thinks it is real.

![img.png](https://miro.medium.com/max/875/1*roO-E4KTolB-wttrs-u16g.jpeg)

* The Generator and the Discriminator are both Neural Networks and they both run in competition with each other in the training phase. The steps are repeated several times and in this, the Generator and Discriminator get better and better in their respective jobs after each repetition. The GAN model eventually converges and produces natural look images.


###  Loss in GAN

```Binary Cross Entrophy```

![img.png](https://cdn-images-1.medium.com/max/1600/1*C2sWPDEYdLV5wm7dNAmBOQ.png)

* The discriminator outputs a value D(x) indicating the chance that x is a real image.Our objective is to maximize the chance to recognize real images as real and generated images as fake

* The GANs are formulated as a minimax game, where the Discriminator is trying to minimize its reward V(D, G) and the Generator is trying to minimize the Discriminator’s reward or in other words, maximize its loss.

![img.pmg](https://media.geeksforgeeks.org/wp-content/uploads/g22-1.png)
 in this function .
  * D(x) is the discriminator's estimate of the probability that real data instance x is real.
  * G(z) is the generator's output when given noise z
  * D(G(z)) is the discriminator's estimate of the probability that a fake instance is real.
  * Ex is the expected value over all real data instances
  * Ez is the expected value over all random inputs to the generator (in effect, the expected value over all generated fake instances G(z)).
  
  
So, basically, training a GAN has two parts:

* ```Part 1:``` The Discriminator is trained while the Generator is idle. In this phase, the network is only forward propagated and no back-propagation is done. The Discriminator is trained on real data for n epochs, and see if it can correctly predict them as real. Also, in this phase, the Discriminator is also trained on the fake generated data from the Generator and see if it can correctly predict them as fake.

* ```Part 2:``` The Generator is trained while the Discriminator is idle. After the Discriminator is trained by the generated fake data of the Generator, we can get its predictions and use the results for training the Generator and get better from the previous state to try and fool the Discriminator.

The above method is repeated for a few epochs and then manually check the fake data if it seems genuine. If it seems acceptable, then the training is stopped, otherwise, its allowed to continue for few more epochs



### Resources: 

* https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf

* https://developers.google.com/machine-learning/gan
