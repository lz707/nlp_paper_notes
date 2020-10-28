# [Sequence to Sequence Learning with Neural Networks]( https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf)
Written in 2014

tl;dr: Seq2seq modeling using LSTM.

#### Overall impression
This is the original seq2seq model using LSTM. This model has been a long time standard choice before the invention of transformer for sequence modeling tasks.

#### Key ideas
The author used a straightforward application of the Long Short-Term Memory (LSTM) architecture -  one LSTM to read the input sequence, one timestep at a time, to obtain large fixed dimensional vector representation, and then use another LSTM to extract the output sequence from that vector. The second LSTM is essentially a recurrent neural network language model except that it is conditioned on the input sequence. The LSTM’s ability to successfully learn on data with long range temporal dependencies makes it a natural choice for this application due to the considerable time lag between the inputs and their corresponding outputs.

#### Technical details
- Model procedure:

![](https://miro.medium.com/max/3560/1*6_4ScA13Zn8vIQ4ryuwZ8A.png)

#### Notes
Using LSTM for sequence modeling introduced human-like behavior in terms of considering previous contexts. The drawback is that when the sequence is long, all the information still gets compressed into a fixed-length vector, causing the long-distance dependency to get lost. Attention later solved this problem by allowing the output directly access the relevant input.
