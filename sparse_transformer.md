# [Generating Long Sequences with Sparse Transformers]( https://arxiv.org/abs/1904.10509)

_April 2019_

tl;dr: Sparse Transformer is an early attempt to use a sparse attention mechanism (local + stride) to reduce transformer’s memory need and increase maximum possible sequence length. 

#### Overall impression
Among recent attempts to reduce vanilla Transformer’s quadratic complexity, Sparse Transformer is one of the earliest effort of (what I call) the “smart attention patterns” group. This group of research aims to cover most of the information needed by only calculating attention on selective tokens, according to some carefully-chosen patterns. The team includes Sparse Transformer (this one), Blockwise Transformer ([Qiu et al., 2019]( https://openreview.net/forum?id=H1gpET4YDB)), Longformer ([Beltagy et al., 2020]( https://arxiv.org/abs/2004.05150)) ([My notes](https://github.com/lz707/nlp_paper_notes/blob/master/longformer.md), ETC ([Ainslie et al., 2020]( https://arxiv.org/abs/2004.08483)), Big Bird ([Zaheer et al., 2020]( https://arxiv.org/abs/2007.14062))  ([My notes](https://github.com/lz707/nlp_paper_notes/blob/master/bigbird.md)) etc. 

I personally believe that there is indeed redundancy in vanilla Transformer’s calculation. As shown by Transformer-XL([Dai et al., 2019]( https://arxiv.org/abs/1901.02860)) ([my notes]( https://github.com/lz707/nlp_paper_notes/blob/master/transformerxl.md)), when layers are stacked, tokens are able to indirectly recover from other tokens the information it did not see directly at previous layers. Therefore, I think theoretically this direction should work. However, empirically according to Google’s benchmark([Tay et al., 2020]( https://arxiv.org/abs/2011.04006)), none of these models consistently outperform original Transformer, though they are not far behind. Thus, it is more of a trade-off between a much longer max sequence length vs. a few points of performance loss.
Sparse Transformer is a pioneer in this group. All the later papers included the local attention idea that was tested in this paper. The memory complexity is O(nlogn).

#### Key ideas & Technical details
The authors added inductive bias to the original Transformer, limiting half attention heads to a fixed local window, and half attention heads to a fixed strided patterns. 
![](https://miro.medium.com/max/1900/0*w5asBwYu7Vl-gYEZ)

#### Notes
In addition to performance loss, as with all sparse attention transformers published so far, this model has one more caveat – it needs custom GPU kernels to implement. A few months’ later, Blockwise Transformer took the block-transformer idea and implemented with a much simpler calculation.
