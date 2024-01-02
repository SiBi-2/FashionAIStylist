# FashionAIStylist: AI Powered Clothing Designer
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-mo/FashionAIStylist/blob/master/GenAIFashionStylist.ipynb)

![teaser](clothing-gan-thumbnail.gif)

## Inspiration
GAN or Generative Adversarial Network is a generative model that able to generate images by learning the probability distribution of a large image dataset. I always find GANs fascinating since they enable people to generate high-quality art or design without any deep technical or artistic skill in drawing. In the past, we've seen many face editing demonstrations of GAN, but seldom seen semantic manipulation of other datasets. That was the inspiration for FashionAIStylist, an application that allows users to collaboratively design clothes without deep technical expertise.

## What it does
FashionAIStylist is able to pull in original clothing images and mix these images. While mixing, you can control which structure or style that you want the clothing to reflect.  You can also edit the generated clothing by adjusting attributes such as brightness, color, or style.

## How it is built
FashionAIStylist is trained StyleGAN2-ADA on a subset of the Lookbook dataset. The total images used are 8,726 clothing images with a clean background. It used transfer learned from the FFHQ model and takes a day to train the model.

After finishing training the GAN, we've used the GANSpace method to find important directions in the latent space. Then, we guess what these directions represent and label them accordingly. The reason GANSpace is used is that it is unsupervised and does not need an attribute classifier.

Finally, we've created a UI with Gradio UI library. The notebook is published on Colab. Gradio makes deployment very easy. We can directly deploy the UI from Colab where Gradio will create a proxy from the Colab server to their domain and provide a working URL, allowing the general public to use the UI or demo.

## What's next for FashionAIStylist
There is a lot of potential for this project. Some features that can be added are appearance transfer, image inversion (uploading & editing real image), generating the fashion model itself, conditional text input with OpenAI CLIP model, etc.

## Citation
```
@inproceedings{härkönen2020ganspace,
  title     = {GANSpace: Discovering Interpretable GAN Controls},
  author    = {Erik Härkönen and Aaron Hertzmann and Jaakko Lehtinen and Sylvain Paris},
  booktitle = {Proc. NeurIPS},
  year      = {2020}
}
```
