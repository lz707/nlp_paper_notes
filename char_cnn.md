# [Character-level Convolutional Networks for Text Classification](https://arxiv.org/abs/1509.01626)

_written in 2015_

tl;dr: When trained with large corpus, we may not need word-level syntatic or semantic knowledge.

#### Overall impression
This paper is very innovative and interesting in applying the models at character-level. This solves the challenge of unknown words. In later research, a more popular way is to use sub-words, which is between characters and words, which I think is probably inspired by the research done in this paper.

#### Key ideas
- character + CNN

#### Technical details
- Model structure:

![](https://miro.medium.com/max/1200/0*fovAEUSdSkbsnJw5.png)



#### Notes
- Though there seems no clear winnder across all tasks, Character-level ConvNet is an effective method. It generated strong results in most experiments. The biggest contribution is that now we realized that we can use sub-word information to model language and therefore avoid the unknown words problem.
