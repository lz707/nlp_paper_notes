# [QANet: Combining Local Convolution with Global Self-Attention for Reading Comprehension](https://arxiv.org/abs/1804.09541)
Written in 2016

tl;dr: QAnet uses convolution and self-attention. Much faster than RNN models, while achieved equivalent accuracy.

#### Overall impression
QAnet has a much simpler structure than BiDAF, yet the thinking behind the design is similar. Trains 5x faster and accuracy is comparable. The authors also used back-translation technique to augment training data. 

#### Key ideas
-	The high level structure of model is exactly the same as BiDAF. Contains five major components: an embedding layer, an embedding encoder layer, a context-query attention layer, a model encoder layer and an output layer

-	The difference is that for both the embedding and modeling encoders, QAnet only use convolutional and self-attention mechanism, discarding RNNs, which are used by BiDAF. As a result, QAnet is much faster, as it can process the input tokens in parallel. The basic building block is [convolution-layer × # + self-attention-layer + feed-forward-layer]

#### Technical details
- Model procedure:

![]( https://miro.medium.com/max/1608/1*AJZICMvoPbn-x_dTIy2L4A.png)

#### Notes
The combination of convolution and self-attention is different from most transformer designs which only uses self-attention. It seems not very necessary to add convolution layer considering models using pure self-attention achieved better performance later. 
