# [A Simple but Tough-to-Beat Baseline for Sentence Embeddings ](https://openreview.net/forum?id=SyK00v5xx)

_Written in 2017_

tl;dr: Sentence embedding use weighted average word embedding, and subtract first principal component. Simple and effective in similarity tasks.

#### Overall impression
As the name suggests, indeed simple and tough-to-beat. It can serve as a great similarity measure.

#### Key ideas & Technical details
Sentence embedding use weighted average word embedding, and subtract first principal component.
- Smooth Inverse Frequency (SIF): similar idea with TF-IDF. Weight = a/(a+p(w)), a is a small number, empirically the authors picked [10^(-5), 10^(-3)]. p(W) is the word frequency in a reference corpus (such as Wikipedia)
- Remove first principal component: after getting all the sentence vectors, calculate the first principal component. This would remove the most frequent discourse that is often related to syntax.

#### Notes
The author tested the model is robust against different corpus choice for calculating frequency. However their corpus is all broad-based, such as enwiki, poliblogs, commoncrawl.etc. Maybe it does matter when the sentences are all from a specific domain and choose a corpus that is more relevant to the domain.

