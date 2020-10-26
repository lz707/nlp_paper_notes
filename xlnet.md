# [XLNet: Generalized Autoregressive Pretraining for Language Understanding]( https://arxiv.org/abs/1906.08237)

Written in 2019

tl;dr: XLNet is a generalized autoregressive pretraining method that leverages the best of both autoregressive language modeling (e.g., Transformer-XL) and autoencoding (e.g., BERT) while avoiding their limitations.

#### Overall impression
XLNet is one step further than BERT by incorporating autoregressive architecture and does not mask any word. It achieves better performance on many tasks than previous SOTA model BERT. But no free lunch – it requires more on computational power. 

#### Key ideas
- Permutated Language modeling - encoding bidirectional context information without MLM: 
Training a model in a bidirectional way poses a challenge if there are multiple layers. The model would see the word it is supposed to predict from higher layers.
![]( https://qph.fs.quoracdn.net/main-qimg-a3d8fd4f86d54c725e8388f0700a58c1)

BERT solved this problem by masking 15% of tokens, however, created discrepancy between pre-training and fine-tuning because the [MASK] token does not exist in real texts. 

XLNet solved this problem by selecting a group of attention dependency paths that are not include the to-be-predicted word itself. To select such paths, XLNet first randomize the word sequence, and then compute the attention vector for a given word using only the words before it in this permutation sequence. Because in the permutation sequence, words from both left and right side of the word in the original sequence can appear before the word, bidirectional information is encoded in the computation in this way.

![]( https://qph.fs.quoracdn.net/main-qimg-0445daa86f6291e59e80de84af15048f)

[Here](https://www.quora.com/q/handsonnlpmodelreview/XLNet-a-clever-language-modeling-solution) is a great explanation of the PLM task

- Incorporate the segment recurrence and relative positional encoding from Transformer XL.

#### Technical details
- Architecture: Two-stream TransformerXL Encoder. Similar model size as BERT
- Data: Giga5 (16GB text), ClueWeb 2012-B and Common Crawl
- Pretraining task: Permutated Language modeling
#### Notes
