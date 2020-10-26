# [Convolutional Neural Networks for Sentence Classification](https://arxiv.org/abs/1408.5882)

_written in 2014_

tl;dr: Pre-trained word embedding + CNN achieved excellent results

#### Overall impression
This structure is one of the most popular model for sentence/document classification before the age of transformers. Even now, it still serve as a strong baseline and a solid choice for resource-constrained projects.

#### Key ideas
- The author use pre-trained word embedding, with multi-head CNN and max pooling.

#### Technical details
- Model structure:

![](https://miro.medium.com/max/475/1*NwheEVSDxEJZAGBWwomZpw.png)

#### Notes
- Although we have deep learning network architecures as complex as transformers, in practice I still find simpler models still form a quick and strong baseline. This model is one of them. 
