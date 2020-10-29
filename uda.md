# [Unsupervised Data Augmentation for Consistency Training](https://arxiv.org/abs/1904.12848)
Written in 2019

tl;dr: Utilizing very few labeled data and a large amount of unlabeled data to get good results.

#### Overall impression
The result of this paper is amazing, reaching SOTA for IMDB using only 20 labeled examples. 


#### Key ideas
Consistency training methods simply regularize model predictions to be invariant to small noise applied to either input examples or hidden states. This framework makes sense intuitively because a good model should be robust to any small change in an input example or hidden states. The main idea this paper contributed is to use high quality data augmentation (e.g. back-translation for NLP) to improve consistency training.

#### Technical details
- Model procedure: Basic idea is to add back-translated versions of input and the original labeling as additional training data, and minimize the divergence between original data and augmented data.
![]( https://camo.githubusercontent.com/0896cb65f9a87983bee3f2f71f3c064c33216413/68747470733a2f2f692e696d6775722e636f6d2f4c38476b3634622e706e67)

#### Notes
The UDA code for generating back-translations is useful. 
