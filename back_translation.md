# [Phrase-based & neural unsupervised machine translation](https://arxiv.org/abs/1804.07755)
Written in 2018

tl;dr: This work investigates how to learn to translate when having access to only large monolingual corpora in each language, using careful initialization, language modeling and back-translation.
#### Overall impression
The paper introduced a clever method to use unsupervised learning to tackle machine translation. This paper is one of the great breakthroughs of NLP in 2018.

#### Key ideas
1.	Initialization: the model first roughly aligns the two monolingual datasets by using crude approximate mappings such as a word-by-word translation using bilingual dictionary
2.	Language modeling: use the readily-available volume of text in each language individually to train a language model.
3.	Iterative back-translation: Translate sentence 1 in language A to language B. Let’s call the translated sentence as sentence 2. Then translate sentence 2 back to language A. Let’s call it sentence 1’. Comparing sentence 1 and 1’ will provide the error signal to train the B->A translation model. Vice versa for A->B model. 

- Model procedure:
![]( https://surafelml.github.io/assets/images/unsupervised-nmt-illustration.PNG)

#### Technical details
There are two versions of models. One neural translation model, and one n-gram based model.
#### Notes
The back-translation technique is frequently used by myself for data augmentation. 
