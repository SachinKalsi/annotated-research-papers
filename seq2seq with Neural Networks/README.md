# Sequence to Sequence Learning with Neural Networks

A study by Google (2014) - Ilya Sutskever and team. 

Original Paper link: https://arxiv.org/abs/1409.3215

## Annotation standards
🟡 - The important research or study with respect to the core concept explained in the paper are highlighted in yellow 🟡 color.

🟢 - The important takeways or learnings are highlighted in green 🟢 color

🔴 - Important takeaways

🔴 + Underline - mini conlusions or crisp summary found in the paper are underlined

## Major learnings from paper

1. The **_ATTENTION MECHANISM_** was also studied in 2013-2014 allows neural networks to focus on different parts of their input
2. OVerall the idea is to use one LSTM to read the input sequence, one timestep at a time, to obtain large fixeddimensional vector representation & then use another LSTM to extract the output sequence from that vector
3. **The simple trick of reversing the words in the source sentence (but not the target sentences in the training and test set) is one of the key technical contributions of this work**. The first few words in the source language are now very close to the first few words in the target language, so the problem’s minimal time lag is greatly reduced
4. Deep LSTMs significantly _outperformed_ shallow LSTMs, so an LSTM with four layer was chosen.
5. Smart batching was used, yielding _2x_ speed
6. LSTMs tend to not suffer from the vanishing gradient problem, they can have exploding gradients 
