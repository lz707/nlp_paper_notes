# [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding]( https://arxiv.org/abs/1810.04805)

Written in 2018

tl;dr: BERT uses transformer encoder structure and two training tasks: masked language modeling and next sentence prediction. Using masked LM can encode bidirectional information, contrary to traditional LM task used by GPT. So far it is one of the best-known pre-trained models. 

#### Overall impression
BERT is now one of the most famous pre-trained models. The MLM and NSP tasks are innovative, simple and empirically powerful. (though there are some pros and cons)

#### Key ideas
- Masked LM: Standard language modeling can only be trained from left to right or right to left, as the bidirectional encoding would leak current word information to the model. Masked LM is to replace 15% of tokens to [MASK] and ask the model to predict the masked token. This way it can fully utilize bidirectional contextual information. However, one downside is that the [MASK] token does not exist during inference or fine-tuning for downstream tasks, thus causing some discrepancy in performance. 
- Next Sentence Prediction: In order to train a model that understands sentence relationships, for tasks such as Question Answering and Natural Language Inference, the authors added the next sentence prediction task. Each training example is consist of two sentences, separated by a [SEP] token, and 50% of them are actual consecutive sentences while 50% of time they are two random sentences. The model is asked to predict whether the second sentence is the actual next sentence. 

![](https://1.bp.blogspot.com/-RLAbr6kPNUo/W9is5FwUXmI/AAAAAAAADeU/5y9466Zoyoc96vqLjbruLK8i_t8qEdHnQCLcBGAs/s1600/image3.png)

#### Technical details
- Architecture: Transformer Encoder. 12- layer for base, 24-layer for large
- Parameters: 110M for base, 340M for large
- Data: BooksCorpus (800M words) and English Wikipedia (2,500M words)
- Pretraining task: Masked LM and Next Sentence Prediction

#### Notes
[Tenney et al.](https://arxiv.org/abs/1905.06316) analyzed the roles of BERT’s layers in different tasks and found that BERT solves tasks in a similar order to that in NLP pipelines: basic syntactic information appears earlier in the network, while high-level semantic information appears at higher layers. 
