# everything-about-gans

## Introduction
Generative adversarial networks (GANs) are a class of neural networks that are designed to generate new images from a training set of images. GANs are very effective at fooling a classifier, because they are able to generate images that are very close to the training set. GANs can be used for may other tasks such as noise suppression / community detection & text generation.

## Why needs to detach the generated tensors from the computational graph?

Because you want the discriminator loss to only compute gradients for the discriminator and not the generator.
The .detach() here allows you to make sure this happens. {If you coludn't break the graph (detach) then the discriminator
whould calculate the gradients for the generator as well.}

If you do it for the generator loss, then the generator loss won’t contribute to the generator gradient which is not what you want.

## Table of Contents

### 1. Basic GAN

Basic GAN is a GAN that uses a simple discriminator and a simple generator. Only Consists of Linear Layers. Images are flattened and then passed through a fully connected layer. The performance of this model is not very good. Also training is very slow.

### 2. Deep Convolutional GAN

Deep Convolutional GAN is a GAN that uses a deep discriminator and a deep generator. Consists of Convolutional Layers. Images are 3D & Latent Dimension is also 3D tensor. Perfoemance is reletively good. But still has their own drawbacks such as **Mode Collapse**