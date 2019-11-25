# MarsGAN

### A GAN trained on satellite photos of Mars

Since 2006, the University of Arizona [HiRISE Satellite](https://www.uahirise.org/) has been photographing the surface of Mars, creating a rich dataset showing the Martian surface. I thought it would be interesting to train a GAN model on these images.

## Data Collection

Data collection is described in the [Data Generation](https://github.com/kheyer/MarsGAN/blob/master/Data%20Generation.ipynb) notebook. The code in the notebook downloads RGB colored HiRISE images from 2009 to 2019, collecting about 50,000 images in total. These images are split into 512x512 patches for training. This is an example of a raw HiRISE image:

<p align="center">
  <img src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_RGB.NOMAP.browse.jpg" alt="drawing" height="1024"/>
</p>

Which is then split into patches for training:

| | | |
|:-------------------------:|:-------------------------:|:-------------------------:|
|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_0_0.jpg">   |  <img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_1_0.jpg">|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_2_0.jpg">|
|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_3_0.jpg">  |  <img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_4_0.jpg">|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_5_0.jpg">|
|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_6_0.jpg">  |  <img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_7_0.jpg">|<img width="512" src="https://github.com/kheyer/MarsGAN/blob/master/media/ESP_011472_1225_8_0.jpg">|

## Basic GAN

The first model we train is detailed in the `Basic GAN` notebook. The model is an extremely simple Wasserstein GAN that uses transposed convolutions in the generator to create a 64x64 image. See the notebook for model architecture and training details. This model works as a proof of concept, but the generated images aren't great. For example:

![](https://github.com/kheyer/MarsGAN/blob/master/media/basic_gan.png)

Clearly the model has captured features of the dataset, such as color and some surface textures. There are also lots of artifacts.
The images are stuck at a low resolution (64x64), as training becomes unstable at higher resolutions. To create better images, we need a more sophistocated model and training proces.

## StyleGAN

We can generate higher quality images using a StyleGAN, a more modern GAN architecture. Details of the StyleGAN model and the training process can be found in the [StyleGAN Training Notebook](https://github.com/kheyer/MarsGAN/blob/master/StyleGAN.ipynb).

These are images that we can create with a StyleGAN:

![](https://github.com/kheyer/MarsGAN/blob/master/media/Mars_StyleGAN.png)

Compared to the basic GAN, StyleGAN can produce higher quality images with fewer artifacts at larger sizes without having issues training.
