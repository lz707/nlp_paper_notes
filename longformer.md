# [Longformer: The Long-Document Transformer](https://arxiv.org/abs/2004.05150)

_April 2020_

tl;dr: Longformer uses a sparse attention mechanism (mostly local, selectively global) to scale linearly with sequence length. 

#### Overall impression
Among recent attempts to reduce vanilla Transformer’s quadratic complexity, Longformer belongs to (what I call) the “smart attention patterns” group. This group of research aims to cover most of the information needed by only calculating attention on selective tokens, according to some carefully-chosen patterns. The team includes Blockwise Transformer ([Qiu et al., 2019]( https://openreview.net/forum?id=H1gpET4YDB)), Sparse Transformer ([Child et al., 2019]( https://arxiv.org/abs/1904.10509)), Longformer (this one), ETC ([Ainslie et al., 2020]( https://arxiv.org/abs/2004.08483)), Big Bird ([Zaheer et al., 2020]( https://arxiv.org/abs/2007.14062)). etc. 

I personally believe that there is indeed redundancy in vanilla Transformer’s calculation. As shown by Transformer-XL([Dai et al., 2019]( https://arxiv.org/abs/1901.02860)) ([my notes]( https://github.com/lz707/nlp_paper_notes/blob/master/transformerxl.md)), when layers are stacked, tokens are able to indirectly recover from other tokens the information it did not see directly at previous layers. Therefore, I think theoretically this direction should work. However, according to Google’s benchmark([Tay et al., 2020]( https://arxiv.org/abs/2011.04006)), none of these models consistently outperform original Transformer, though they are not far behind. Thus, it is more of a trade-off between a much longer max sequence length vs. a few points of performance loss.

Among all the papers in this group, Longformer’s approach is simple yet effective. 

#### Key ideas & Technical details
The authors added inductive bias to the original Transformer, limiting most token’s attention to a fixed local window, with only a few special tokens attends to everyone else. The local attention is in charge of modeling contextual representations, while the global attention is in charge of full-sequence information for predictions. 
1.	Local Attention: for each token, calculate local attention using a fixed-size window. The window size can be different across layers, i.e smaller for lower layers and larger for higher layers.
2.	Dilated Local Attention: To further increase the receptive filed, the sliding window can be “dilated”, i.e calculate attention with a gap.
3.	Global Attention: For certain special tokens, such as [CLS] or question tokens in QA, attend to all tokens and all tokens attend to them as well.
![](https://paperswithcode.com/media/methods/Screen_Shot_2020-05-31_at_7.04.33_PM.png)

#### Notes

The authors compared with Roberta-base, and showed that Longformer outperformed Roberta-base in the tasks chosen.  However, in Google’s benchmark, Longformer underperformed vanilla Transformer by a few points in all tasks, though outperformed the simple local attention baseline quite significantly. 
 
 
![](https://lh6.googleusercontent.com/Hyl6szjPw54H37PsGd98HwDPOcW3jN-2ZE7cr0S780kaXsDli8Jl21Dlr3X_7ISbNdzp-1QnDUkvI8f9dXu8xdiGEKqtZPSei2XSTGw-1qZRx_sXgR5Y73NNICVudLFlSehDaCMR)
