# Implementation-of-GAN-and-cGAN


## The data:

The MNIST dataset is a collection of handwritten digits images widely used for machine learning and computer vision tasks. 
It contains 60,000 grayscale images of handwritten digits, each with a size of 28x28 pixels.
The images are labeled with their corresponding digit classification, from 0 to 9. 
The MNIST dataset is commonly used as a benchmark dataset for image classification tasks and is widely used in research and industry applications.

## GAN model:

The model used in this work is a neural network consisting of two networks: a generator and a discriminator.
The generator network is responsible for generating new data that is similar to the data in the training set. 
Once the generator has produced a new data point, the discriminator network is used to determine whether the generated data is real or fake. 
In other words, the discriminator tries to distinguish between the data generated by the generator and the real data from the training set. 
The goal of this model is to train the generator to generate realistic data that can fool the discriminator into thinking it is real. 
This approach is known as a Generative Adversarial Network (GAN) and is commonly used in generative modeling tasks.


**Architecture:**
Generator:

![image](https://user-images.githubusercontent.com/96613758/220575951-fc0b0c93-0972-4030-9d37-f6edb7c3891e.png)

Discriminator:

![image](https://user-images.githubusercontent.com/96613758/220575990-f1abfb66-83be-4a5a-bb44-fb63ecfe0a9f.png)
In this work, the model was trained for 200 epochs to generate high-quality images.
An epoch refers to one complete iteration through the entire training dataset. 
By training the model for 200 epochs, it was allowed to adjust its parameters for a longer period of time,
potentially improving the quality of the generated images.

**Generated images:**

![image](https://user-images.githubusercontent.com/96613758/220576312-d667cbad-11d8-467c-b34e-12588f1364b5.png)

![image](https://user-images.githubusercontent.com/96613758/220576372-c56e3f7c-9e9d-4106-a8d7-1f623facb445.png)
![image](https://user-images.githubusercontent.com/96613758/220576407-34a71f45-fbf6-4c02-aedd-c75abb6e5f8e.png)

![image](https://user-images.githubusercontent.com/96613758/220576425-b500e12a-73c8-40a3-a89d-ae9e472304e2.png)

We can note that there are many genereated images of the digits 1 and 7,  it is possible that the generator is collapsing to a single mode, meaning it is only generating a limited range of images that all look very similar.
This can happen if the generator is not being sufficiently constrained or guided to produce a diverse range of images for these particular digits.

![image](https://user-images.githubusercontent.com/96613758/220577388-821660c7-8e30-4a9e-9527-be6876cd0692.png)

## cGAN model:

CGAN stands for Conditional Generative Adversarial Networks.
It is a variation of the GAN architecture, where both the generator and discriminator networks are provided with an additional input, known as the conditional input, 
which is usually a label or a class. In the case of the MNIST dataset, the label is the digit that the model should generate.

The conditional input is concatenated with the input to the generator and the input to the discriminator to create a joint representation, which allows the model to generate images based on the given label. 
This way, we can control the output of the generator and ask it to generate a specific digit, instead of generating random images.

The CGAN model is trained in a similar way to the standard GAN, with the generator trying to fool the discriminator, and the discriminator trying to correctly classify between the real and generated images, but with the additional constraint that the generated image should belong to the given label.

**Architecture:**

![image](https://user-images.githubusercontent.com/96613758/220577425-e0ebac7b-e028-4912-ba65-0cc5572a38c7.png)

![image](https://user-images.githubusercontent.com/96613758/220577490-242ac8a4-e056-4a44-be39-6169b38681b5.png)

**Generated images:**

![image](https://user-images.githubusercontent.com/96613758/220577512-7170c8ef-1913-4461-b8f0-5df6826accf0.png)

## Models Comparisons:

**first model - GAN :**
![image](https://user-images.githubusercontent.com/96613758/220578685-576a9fb4-32ef-4dd3-94bb-ae01f36ae22f.png)

**seccond model - cGAN:**

![image](https://user-images.githubusercontent.com/96613758/220578703-92d001d5-c63a-412e-b6f2-51f7adee2b6a.png)

between the generator and discriminator in the GAN framework. The generator tries to generate realistic images to fool the discriminator,
while the discriminator tries to correctly classify the real images and distinguish them from the fake ones.
As the generator improves, it becomes harder for the discriminator to distinguish between real and fake images, so its loss function increases. 
At the same time, the generator's loss function decreases as it generates more realistic images that fool the discriminator.
This tradeoff can lead to fluctuations in the loss functions of both networks over the course of training.


* the implementation of the cGAN model is based on this paper - https://arxiv.org/pdf/1411.1784.pdf%EF%BC%88CGAN%EF%BC%89
