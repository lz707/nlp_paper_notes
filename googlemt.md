# [Google's Neural Machine Translation System: Bridging the Gap between Human and Machine Translation]( https://arxiv.org/abs/1609.08144)
Written in 2016

tl;dr: This work introduced Google’s translation system which included a group of design choices that increase NMT model robustness and speed.

#### Overall impression
This is the original seq2seq model using LSTM. This model has been a long time standard choice before the invention of transformer for sequence modeling tasks.

#### Key ideas
-	The model consists of a deep LSTM network with 8 encoder and 8 decoder layers using residual connections as well as attention connections from the decoder network to the encoder.

-	To increase speed, they only use attention to connect the bottom layer of decoder to the top layer of encoder. Also to accelerate the final translation speed, they employ low-precision arithmetic during inference computations.

-	To increase robustness, they used sub-words instead of words.

#### Technical details
- Model procedure:
![](https://www.pinchofintelligence.com/wp-content/uploads/2016/11/2016-11-28-11_25_12-1611.04558v1.pdf.png)

#### Notes
Although this paper did not have any major development of mainstream model structures, it is a good practitioner guide with a group of tricks to improve speed and performance. 
