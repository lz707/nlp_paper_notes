# [ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators](https://openreview.net/forum?id=r1xMH1BtvB)
Written in 2020

tl;dr: ELECTRA uses a GAN-like structure – replacing tokens and let the discriminator to identify the corrupted tokens. This change resulted a more efficient training with a performance comparable to BERT of similar size.

#### Overall impression
How to apply GAN in NLP has been a hot topic. ELECTRA proposed a very innovative way utilizing the idea of GAN and indeed gained efficiency during training.

#### Key ideas
There are two main drawbacks of the Masked LM task used by BERT/RoBERTa:
1.	[MASK] token does not exist during inference, therefore causing a discrepancy between training and inference.
2.	Only 15% of tokens are masked, therefore learning only happens on 15% of the data for a given training example.

ELECTRA purposed a different way to pretrain, in order to solve the two problems above. 
1.	For a given input sequence, randomly replace some tokens with a [MASK] token.
2.	Use a small MLM model as generator, and predict the original tokens for all masked tokens.
3.	Replace [MASK] with the predicted token, and ask the discriminator predicts whether it is an original or whether it has been replaced by the generator.

# [](https://miro.medium.com/max/1250/1*B5Bb8wvGSYCyIHwQQfs-lA.png)

The discriminator loss is calculated over the whole input sequence as it has to identify for EACH token that if it has been replaced. On the contrary, MLM only calculate loss on the masked tokens. This is the key difference where ELECTRA gains more efficiency over BERT.
The generator here is not trained to deceive the discriminator, which is one difference from GAN.

#### Notes
ELECTRA uses significant less resources to train, though you may experience a little performance drop. I  do applaud for the idea.
