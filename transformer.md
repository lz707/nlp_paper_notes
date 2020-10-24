# [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

Written in 2017

tl;dr: Transformer is a network architecture based solely on attention. It is faster than RNN due to ability to parallel and better than CNN in modeling long distance dependency. Subsequent research adopting this structure generated SOTA performance in all major NLP tasks.  

#### Overall impression
The paper is quite innovative when the mainstream of NLP research was still improving RNN and CNN in various ways. This paper completely dispensed recurrence and convolutions. The fact that it can be parallelly calculated, making the large pre-trained models possible. This is truly a revolutionary paper and a milestone in recent NLP research, comparable to the impact of word embeddings.  

#### Key ideas
- Encoder: stack of 6 identical layers. Each layer has one multi-head self-attention sub-layer, and a feed-forward sub-layer. Residual connection and layer normalization are also employed after each sub-layer
- Decoder: stack of 6 identical layers. In addition to the two sub-layers similar to encoder, there’s another sub-layer that takes the self-attention of output so far. Also the self-attention here is modified so that each position can only attend to prior positions. 
![]( https://i0.wp.com/blog.exxactcorp.com/wp-content/uploads/2019/05/1_blSbN23mOGMZ_DWvTAcO1w.png)

#### Technical details
- Attention calculation: Q, K, V

  For each attention head, we have a matrix Wq, Wk, Wv. The matrices are learned, and they are shared across layers. Q, K, V are results of input embedding (or previous layer’s output) * Wq, Wk, Wv.  Attention = softmax(Q*K/sqrt(dk))*V.  sqrt(dk) is a scaling factor to keep the attention stable.

  Jay Alammar has an amazing [visualization](http://jalammar.github.io/illustrated-transformer/)

- Multi-head: the final results of each head are concatenated 
- Positional encoding: because self-attention does not have position information, the order of sequence has to be added by positional encoding. The encoding is added as a vector that has the same dimension as word embedding. There are a few properties we want to have for such positional encoding:
  1. the generated vector is unique for each position
  2. the difference between two time-steps is stationary
  3.  The model can learn this pattern, and generalize to longer sentences
  
  Using simple [0 , 1] does not meet #2. Using integer linearly (1, 2, 3…) does not meet #3, because if the model is asked to deal with a sequence longer than any training examples, it may not be able to understand because it has never seen it. The author chose a function with sin and cos. 
  Amirhossein Kazemnejad has a clear [explanation](https://kazemnejad.com/blog/transformer_architecture_positional_encoding/)


#### Notes
- The encoder can be fully parallelized but the decoder can not because it still needs input from previous outputs. In later research, apprently researchers found that the encoder only is powerful enough, so some of the most famous models use only the encoder.
