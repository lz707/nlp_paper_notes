# [ALBERT: A Lite BERT for Self-supervised Learning of Language Representations]( https://arxiv.org/abs/1909.11942)

Written in 2019

tl;dr: ALBERT reduced the number of parameters in BERT, by using parameter sharing. However the training and inference time of ALBERT are even longer than BERT.

#### Overall impression
Recently the direction of NLP research seems to be generating larger and larger pretrained models. ALBERT is one attempt to reduce the model size and prove that many parameters are actually inefficient in those large models. (though it did not help to increase speed)

#### Key ideas
Architecture improvements for more efficient parameter usage:

- Factorized Embedding Parameterization:

The authors argue that the network dimensions are determined by input embedding dimension E x hidden layer dimension H. However, most of this huge matrix is not frequently updated (because they are tied to embedding not context). Therefore, they split the embedding into two items, resulting in a much smaller parameter matrix size. .

- Cross Layer Parameter Sharing

ALBERT further improves parameter efficiency by sharing all parameters, across all layers. That means Feed Forward Network parameters and Attention parameters are all shared.

- Sentence Order Prediction: 

NSP used by BERT can be cheated by topic prediction. Therefore the ALBERT authors designed another task to encode inter-sentence coherence: test if two sentence are in the correct order, or swapped order.

#### Technical details
- Architecture: Same as BERT except embedding parameterization.
- Data: Same as BERT
- Pretraining task: Masked LM and Sentence Order Prediction

#### Notes
