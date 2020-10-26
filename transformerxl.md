# [Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context]( https://arxiv.org/abs/1901.02860)

Written in 2019

tl;dr: TransformerXL adds recurrence to plain vanilla Transformers, aiming to gain better long-term dependency beyond the fixed-length of the latter. 

#### Overall impression
Original Transformer (Vaswani. et al 2017) has a fixed length of 512 tokens. When Al-Rfou et al presented an architecture to use transformer for language modeling [here](https://arxiv.org/abs/1808.04444), they split the inputs in to segments of 512 tokens, and shifting the window by one each step for each prediction.
![](https://miro.medium.com/max/3200/0*xKYSYsJkLjAZAoSr)


This paper provides a more efficient solution by fix the hidden states from previous segments and shift an entire segment. Subsequent work adopting this approach, such as XLNet, achieved SOTA performance in many tasks. 

#### Key ideas
After processing the first segment (such as first 512 tokens like original transformer), Transformer XL will keep the outputs of the hidden layers. Then it process the second segment (i.e token 513 – 1024), each hidden layer will receive two inputs: output from both current segment and previous segment. 
![]( https://miro.medium.com/max/3200/0*u-S6KtrNpYFtOl0k)

#### Technical details
- Attention calculation: Q, K, V
K and V are concatenations of two hidden sequences of current and previous segments (gradient stopped). While Q is current segment only. 
- Relative positional encoding: 
Because the calculation now includes two segments, using the absolute positional encoding would confuse the first token for previous segment and first token of current segment. Therefore, Transformer XL adopted relative positional encoding, which only record the relative position.

#### Notes
