
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



### Resources: 

* https://developers.google.com/machine-learning/gan
