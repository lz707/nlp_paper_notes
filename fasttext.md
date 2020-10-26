# [Bag of Tricks for Efficient Text Classification](https://arxiv.org/abs/1607.01759)

_written in 2016_

tl;dr: Fasttext is a strong baseline model that uses bag-of-ngrams to train very large corpus very quickly on CPU only

#### Overall impression
The method is a fast and strong baseline model for sentence classification.

#### Key ideas
- The authors use take average embedding of n-grams, and feed it into a linear classifier. This simple method is a strong baseline for sentence embedding

#### Technical details
- Model structure:
![](https://www.researchgate.net/publication/332287010/figure/fig1/AS:745599720775681@1554776234492/Model-architecture-of-FastText-for-a-post-with-N-n-gram-features-x-1-x-N-The.png)

#### Notes
- Although we have deep learning network architecures as complex as transformers, in practice I still find simpler models still form a quick and strong baseline. Fasttext is one of them. 
