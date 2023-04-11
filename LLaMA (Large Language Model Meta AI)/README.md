#  LLaMA (Large Language Model Meta AI)

Original Paper link: https://arxiv.org/abs/2302.13971

Meta has released & open-sourced LLaMA, a collection of foundation large language models ranging from 7B to 65B parameters.

# Take aways from the paper

1. The paper has placed greater emphasis on the compute budget required for inference rather than the compute budget required for training, which is not typically observed.
2. LLaMA has used only publicly available data for the training
3. Significant importance has been given to  data cleaning process.
   1. Used [language-detection, a fastText linear classifier](https://fasttext.cc/docs/en/language-identification.html) model to remove non-english text. The library used is very good, accurate & faster in detecting non-english text
   2. Data deduplication for different datasets and removal of html tags, comments etc.
   3. Used 7 different datasets for training & overall the training data size is `~1.45TB`
4. Used BPE (bytepair encoding) tokenizer & entire training dataset containes `1.4T` tokens!
5. Architecture
   1. Bases on transformer architecture (Vasvawni) & leverages various improvements used in different models
   2. Pre-normalization (`GPT3`): normalize the input of each transformer sub-layer using  RMSNorm normalizer, instead of normalizing the output
   3. SwiGLU activation function (`PaLM`): Used __*`SwiGLU`*__ activation function instead of `ReLU`
   4. Rotary Embeddings (`GPTNeo`): Rotary positional embeddings (RoPE) were used instead of absolute positional embeddings
   5. Optimizer: `AdamW` with cosine learning rate scheduler.
   6. Memory optimisation techniques:
       1.  not `storing` the attention weights and not `computing` the key/query scores that are masked due to the causal nature of the language modeling task.
       2.  Save the activation which are computationally expensive: Manually implemented backward function instead of using PyTorch autograd
6. Used 2048 A100 GPU (80GB) for training 1.4T tokens for ~21 days
7. LLaMA authors also found that finetuning these LMs on instructions lead to promising results & the investigation is in progress

Detailed explanation: https://youtu.be/HhBbuV5LBqo
