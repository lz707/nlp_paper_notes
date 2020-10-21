# [Effective Approaches to Attention-based Neural Machine Translation](https://arxiv.org/pdf/1508.04025.pdf)

Written in 2015

tl;dr: Tested two attentional mechanism: a global approach which always attends to all source words and a local one that only looks at a subset of source words at a time.

#### Overall impression
The paper is one further step over [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473). It discussed two versions of attention and some alternative forms of attention formula. The local attention version is a bit like CNN which only focuses on words within a moving window.

#### Key ideas
- Global Attention: though the authors claimed 3 key differences of their design and Bahdanau et al. (2015): single direction vs bi-directional; calculation path; multiple attention formula. Structural-wise, they are very similar
- Local Attention: intuitively, local attention set to only X words nearby. X is empirically selected. The goal is to reduce calculation and making it easier to train. This results in a slight improvement in the BLEU score.


#### Technical details
- The paper also compared a few alignment functions for input hidden Sj and output hidden Hj: 
1. dot product of the two vectors
2. general: Sj*Wa*Hj
3. Concatenate: tanh(Wa*[Sj;Hj] (This is what Bahdanau et al. used)
The conclusion is that dot works better for global attention and general works better for local attention. Local+general gives the best system.


#### Notes
- It is very interesting that the local attention outperformed, although only by a slight margin and the alignment function is also playing a role here. By introducing the local attention, we are injecting a bias from human intuition - only nearby X words are relevant. This bias is apparently useful knowledge, just like how CNN and LSTM also have such biases comparing to MLP. Though recent trend is to train larger and more general models. 
