# [Bidirectional Attention Flow for Machine Comprehension](https://arxiv.org/abs/1611.01603)
Written in 2016

tl;dr: Bi-Directional Attention Flow (BIDAF) network, a multi-stage hierarchical process that represents the context at different levels of granularity and uses bidirectional attention flow mechanism to obtain a query-aware context representation without early summarization

#### Overall impression
Machine comprehension (MC), answering a query about a given context paragraph, requires modeling complex interactions between the context and the query. The model uses a group of advanced techniques at its time to form a multi-stage hierarchical model that achieves SOTA performance.
#### Key ideas
-	Background: A significant contributor to the advancement of machine comprehenshion models has been the availability of large datasets. Early datasets were too small to train end-to-end neural models, until the following two large datasets were collected:

-	SQuAD is a machine comprehension dataset on a large set of Wikipedia articles, with more than 100,000 questions. The answer to each question is always a span in the context. The model is given a credit if its answer matches one of the human written answers. Two metrics are used to evaluate models: Exact Match (EM) and a softer metric, F1 score, which measures the weighted average of the precision and recall rate at character level. It is one of the largest available MC datasets with human-written questions and serves as a great test bed for our model.

-	In a cloze test, the reader is asked to fill in words that have been removed from a passage, for measuring one’s ability to comprehend text. Hermann et al. (2015) have compiled a massive Cloze-style comprehension dataset, consisting of 300k/4k/3k and 879k/65k/53k (train/dev/test) examples from CNN and DailyMail news articles, respectively. Each example has a news article and an incomplete sentence extracted from the human-written summary of the article. To distinguish this task from language modeling and force one to refer to the article to predict the correct missing word, the missing word is always a named entity, anonymized with a random ID. Also, the IDs must be shuffled constantly during test, which is also critical for full anonymization.

-	The model starts with both character and word embedding, then use a LSTM to embed contextual information. This is done for both Context and Query. Then the model calculates attention between query and context in both directions (query-to-context and context-to-query). Then the output, which is query-aware context representation, will go through two layers of LSTM before it procures the output.


#### Technical details
- Model procedure:
1. Character Embedding Layer maps each word to a vector space using character-level CNNs. 
2. Word Embedding Layer maps each word to a vector space using a pre-trained word embedding model. 
3. Contextual Embedding Layer utilizes contextual cues from surrounding words to refine the embedding of the words. These first three layers are applied to both the query and context. 
4. Attention Flow Layer couples the query and context vectors and produces a set of query-aware feature vectors for each word in the context. 
5. Modeling Layer employs a Recurrent Neural Network to scan the context. 
6. Output Layer provides an answer to the query.
![]( https://miro.medium.com/max/1200/0*zp66pJbgc8w-bmAb.png)

#### Notes
BiDAF is a rather complex yet effective model in MC. 
