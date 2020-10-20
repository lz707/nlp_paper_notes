# [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473)

_May 2016_

tl;dr: Use attention mechanism to solve long distance dependency. Foundation of self-attention

#### Overall impression
The paper proposed using attention mechanism to enable output to have direct access to relevant input, which largely addressed the information loss from compressing all information into a fixed-length vector in the traditional encoder-decoder framework.

#### Key ideas
The attention layer is a simple feed-forward neural network, to calculate the dependency of output i on input j. The layer is jointly trained with the translation RNN. By having attention mechanism, the decoder can decide which part of the input it should focus on when making current decision. This alleviated the burden on encoder to capture all the information in a fixed-length vector.

#### Technical details
1.	Traditional RNN encoder-decoder framework:
    Encoder input: X1, X2, …, XT
    Hidden state at time t: Ht = f(Xt, Ht-1), where f could be LSTM or other RNN
    Then from the sequence of hidden states, generate context vector C = q({H1, …, Ht}). Often C = Ht 
    Decoder is trained to predict the next word Yt from C and all the previously predicted words {Y1,…Yt-1}:
    Prob(output word Yt) = Prob (Yt|{{Y1,…Yt-1}, C} = g(Yt-1, St, C), where g is output RNN with hidden state St. (Note: St depend on C    here)
2.	With attention, change the fixed vector C to a distinct context vector Ct for each time
    Decoder Prob(output word Yt) = Prob (Yt|{{Y1,…Yt-1}, X} = g(Yt-1, St, Ct). (Note: St depend on Ct here)
    Attention weight is decided by:
    eij = a(Si-1, Hj), a is a feed-forward network, this is the how relevant output i and input j is
    then take a softmax over all input positions so that the weights adds up to 1
    Ci  = sum of (softmax attention weights * Hj) at all input locations
    
    
    ![](https://swethatanamala.github.io/assets/Images/machine_translation/decoder.png)
    
#### Notes
- Questions and notes on how to improve/revise the current work  
