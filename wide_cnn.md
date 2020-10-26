# [A Convolutional Neural Network for Modelling Sentences](https://arxiv.org/abs/1404.2188)

_written in 2014_

tl;dr: Another version of CNN structure to model sentences. One interesting design is wide convolution

#### Overall impression
This paper is published around the same time with the one authored by [Yoon Kim](https://arxiv.org/abs/1408.5882). Both paper use CNN and word embedding. This paper has a more complex structure than the other one. While performance-wise there's no clear winner.

#### Key ideas
- Narrow and wide convolution:

![](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRs-5xCllMwV3EVA9__bB8D_pKwh2jMy1dIng&usqp=CAU)

#### Technical details
- Model structure:

![](https://d3i71xaburhd42.cloudfront.net/27725a2d2a8cee9bf9fffc6c2167017103aba0fa/4-Figure3-1.png)



#### Notes
- This paper has some innovative ideas, such as wide convolution and k-max pooling. However it seems the simpler structure of [Yoon Kim](https://arxiv.org/abs/1408.5882) is more popular among practitioners. 
