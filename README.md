# Distribution-Gan

A simple GAN that aims to generate multiple distributions of independent variables. This project was motivated for further developments and use in ...

The architecture used for the model (in both the generator and discriminator) was of 3 dense fully conected hidden layers with LeakyReLU activation and a dense layer with sigmoid activation as output for the discriminator and no activation for the generator.

For the loss function, a non-saturating loss was chosen. This is an improvement upon the original gan loss proposed in [Goodfellow et al, 2014](https://arxiv.org/abs/1406.2661), which by manipulating the generator loss we obtain a alternative that converges smoothly. 

Furthermore, a small offset $\varepsilon$ on the discriminator results is used to alleviate exploding gradient problems that could arise due to taking the log of infinitesimals. Hence, the final loss expresionn follows:

$\nabla \theta_{g} = -\frac {1}{m} \sum ln(D(G(z))+\varepsilon)$

$\nabla \theta_{d} = -\frac {1}{m} \sum [ln(D(x)+\varepsilon)+ln(1 - D(G(z))+\varepsilon) ] $

Where $z$ represents noise sample and $x$ a dataset sample.
