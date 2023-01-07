# CRAMMING: TRAINING A LANGUAGE MODEL ON A SINGLE GPU IN ONE DAY

*University of Maryland* investigated the downstream performance achievable with a transformer-based language model trained completely from scratch with MLM for a single day on a single consumer GPU. The paper addressed the question "How far can we get with a single GPU in just one day?"

## Annotation standards
🟡 - The important research or study with respect to the core concept explained in the paper are highlighted in yellow 🟡 color.

🟢 - The important summary are highlighted in green 🟢 color

🔴 - very important takeaways

🔴 + Underline - mini conlusions/study topics or crisp summary found in the paper are underlined

## Paper Summary
1. A transformer-based language model is trained with MLM, completely from scratch. Training on a single GPU for 24 hours.
2. Improvements done through better data curation & quality on top of the data, used to train BERT
3. **Implementation Details**: Implemented everything in _PyTorch_
   1. Data Setup:
      1. lower-cased, strip accents and non-ascii characters removal
      2. WordPiece English tokenizer with 32K tokens (2^15). Vocab size lesser than 32K yields bad performance & greater than 32K wasn't better
      3. tokenized into 128 sequence length & `<sep>` token was used to separate the fragments
   2. Architecture Modifications
      1. Disabled all QKV biases and linear layer biases
      2. Implemented scaled sinusoidal positional embeddings over learned or unscaled sinusoidal embeddings and found incremental benefits
      3. Found that pre-normalization with Layer Norms is beneficial over post Layer Norms.
   4. Training Setup
      1. Used MLM with 15% tokens masked & found no improvements from masking more tokens
      2. Mean-squared error OR L1 loss didn't yield any benefits, so log-loss was chosen
      3. Adam optimiser & gradient clipping of value 0.5
      4. one-cycle learning rate lead to minimal training loss
   6. Dropping `Dropout` to maximise number of parameter updates & re-enabled during fine-tuning taks with a value of 0.1
4. `ELECTRA` could be more beneficial for crammed models
    
## Major learnings from paper

1. Found no significant change in performance with BPE or SentencePiece tokenizers with Unigrams
2. The performance impact from dropping `<sep>` was minimal and No impact was observed from including a `<cls>` token in pretraining. 
3. Models with more parameters learn more efficiently, as their MLM loss decreases faster on a per-gradient basis.
4. Reducing the amount of heads decreases finetuning performance, though it decreases gradient costs, so better keep `12 heads`
5. NO benefits from changing to another activation than GELU
6. The key effect of pre-normalization is to stabilize training & enable larger learning rates and reduced warmup.
7. `Dropout` prevents overfitting when training data is small relative to total compute budget & dropout effectively reduces the number of gradient
updates seen by each parameter.

## Study Topics: Relevant topics mentioned in the paper
`funnel-transformer architecture`, `FLASH mechanism`, `Fourier attention`, `rotary embedding`, `scaled sinusoidal positional embeddings`, `learned or unscaled sinusoidal embeddings`, `one-cycle learning rate`, `averaged micro-batches`

P.S: 70+ research papers was referred and `Scaling Laws for Neural Language Models` (Kaplan) was referred several times in the paper

