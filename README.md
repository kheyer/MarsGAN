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


