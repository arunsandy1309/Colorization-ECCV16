# Colorization - PyTorch Implementation

| Input | Output |
| --------------------------------- | --------------------------------- |
|<img src="https://user-images.githubusercontent.com/50144683/232332171-d7a3fde6-a959-4e62-a233-001f8ee1e71a.jpg" height="400"> | <img src="https://user-images.githubusercontent.com/50144683/232332191-6a055344-a86b-49c9-9273-31b7183653c9.png"  height="400">

This repository contains the Pytorch implementation of the following paper:
>**Colorful Image Colorization**</br>
>Richard Zhang, Phillip Isola, Alexei A. Efros</br>
>https://arxiv.org/abs/1603.08511
>
>**Abstract:** _Given a grayscale photograph as input, this paper attacks the problem of hallucinating a plausible color version of the photograph. This problem is clearly underconstrained, so previous approaches have either relied on significant user interaction or resulted in desaturated colorizations. We propose a fully automatic approach that produces vibrant and realistic colorizations. We embrace the underlying uncertainty of the problem by posing it as a classification task and use class-rebalancing at training time to increase the diversity of colors in the result. The system is implemented as a feed-forward pass in a CNN at test time and is trained on over a million color images. We evaluate our algorithm using a “colorization Turing test,” asking human participants to choose between a generated and ground truth color image. Our method successfully fools humans on 32% of the trials, significantly higher than previous methods. Moreover, we show that colorization can be a powerful pretext task for self-supervised feature learning, acting as a cross-channel encoder. This approach results in state-of-the-art performance on several feature learning benchmarks._

## Architecture
<img src="https://user-images.githubusercontent.com/50144683/232333135-3f4793ef-9320-43e6-acd4-4dd9dae0a7fd.png">
Each conv layer refers to a block of 2 or 3 repeated conv and ReLU layers, followed by a BatchNorm layer. The net has no pool layers. All changes in resolution are achieved through spatial downsampling or upsampling between conv blocks. We train a deep CNN to map from a grayscale input to a distribution over quantized color value outputs using the architecture. We train the network on the 1.3M images from the ImageNet training set, validate on the first 10k images in the ImageNet validation set, and test on a separate 10k images in the validation set. While image colorization is a boutique computer graphics task, it is also an instance of a difficult pixel prediction problem in computer vision. Here we have shown that colorization with a deep CNN and a well-chosen objective function can come closer to producing results indistinguishable from real color photos.

## Usage
The blow script will colorize an image.</br>
```
python colorization.py -i imgs/wild.jpg
```
If you have a Nvidia GPU, use the below script to run colorise the image using GPU's computational power.
```
python colorization.py -i imgs/wild.jpg --use_gpu
```

## Results
| Input | Output |
| --------------------------------- | --------------------------------- |
|<img src="https://user-images.githubusercontent.com/50144683/232334898-489384a2-9e1a-45b1-a387-c36a99fcf416.jpg"> | <img src="https://user-images.githubusercontent.com/50144683/232334813-e84472ae-33b4-457d-a30f-71226aab49c2.png"> |
|<img src="https://user-images.githubusercontent.com/50144683/232334903-432c5e6a-e97a-4b84-9508-839ae92234b8.jpg"> | <img src="https://user-images.githubusercontent.com/50144683/232334819-e66defe4-b9f8-404d-a82f-0cce908c6fd2.png"> | 
