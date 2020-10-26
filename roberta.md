# [RoBERTa: A Robustly Optimized BERT Pretraining Approach]( https://arxiv.org/abs/1907.11692)

Written in 2019

tl;dr: RoBERTa, is a retraining of BERT with improved training methodology, 1000% more data and compute power.

#### Overall impression
RoBERTa removes the Next Sentence Prediction task from BERT’s pre-training and introduces a few tricks in training BERT. 

#### Key ideas
- Removed NSP
- Dynamically changing the masking pattern applied to the training data
- Larger batch size
- More data
- Longer training

#### Technical details
- Architecture: Same as BERT
- Data: Books Corpus and English Wikipedia used in BERT. Additionally, they added CommonCrawl News dataset (63 million articles, 76 GB), Web text corpus (38 GB) and Stories from Common Crawl (31 GB) 
- Pretraining task: Masked LM only

#### Notes
Although not too much innovation in the model structure, RoBERTa outperformed both BERT (expected) and XLNet (nice surprise).   
