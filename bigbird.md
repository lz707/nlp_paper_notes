# [Big Bird: Transformers for Longer Sequences]( https://arxiv.org/abs/2007.14062)

_July 2020_

tl;dr: BigBird uses a sparse attention mechanism (local + selectively global + random) to scale linearly with sequence length. 

#### Overall impression
Among recent attempts to reduce vanilla Transformer’s quadratic complexity, BigBird belongs to (what I call) the “smart attention patterns” group. This group of research aims to cover most of the information needed by only calculating attention on selective tokens, according to some carefully-chosen patterns. The team includes Blockwise Transformer ([Qiu et al., 2019]( https://openreview.net/forum?id=H1gpET4YDB)), Sparse Transformer ([Child et al., 2019]( https://arxiv.org/abs/1904.10509)), Longformer ([Beltagy et al., 2020]( https://arxiv.org/abs/2004.05150)) ([My notes](https://github.com/lz707/nlp_paper_notes/blob/master/longformer.md), ETC ([Ainslie et al., 2020]( https://arxiv.org/abs/2004.08483)), Big Bird (this one) etc. 

I personally believe that there is indeed redundancy in vanilla Transformer’s calculation. As shown by Transformer-XL([Dai et al., 2019]( https://arxiv.org/abs/1901.02860)) ([my notes]( https://github.com/lz707/nlp_paper_notes/blob/master/transformerxl.md)), when layers are stacked, tokens are able to indirectly recover from other tokens the information it did not see directly at previous layers. Therefore, I think theoretically this direction should work. However, empirically according to Google’s benchmark([Tay et al., 2020]( https://arxiv.org/abs/2011.04006)), none of these models consistently outperform original Transformer, though they are not far behind. Thus, it is more of a trade-off between a much longer max sequence length vs. a few points of performance loss.

All of the papers in this group has a certain level of overlap. BigBird is essentially longformer + random attention. 

#### Key ideas & Technical details
The authors added inductive bias to the original Transformer, limiting most token’s attention to a fixed local window +  a few special tokens attends globally + random attention. Random attention is a sparse attention were each query attends over r random number of keys.  

![](https://i2.wp.com/syncedreview.com/wp-content/uploads/2020/08/image-1.png)

#### Notes

In Google’s benchmark, BigBird has the most consistent performance comparable to vanilla Transformer across all tasks. Though the speed is also similar to vanilla Transformer, this does extends the sequence length longer while keeping the performance almost intact.  
