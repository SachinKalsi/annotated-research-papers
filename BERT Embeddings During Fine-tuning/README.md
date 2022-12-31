# What Happens To BERT Embeddings During Fine-tuning?

A study by Google on how model (BERT) changes when fine-tuned

## Annotation standards
🟡 - The important research or study with respect to the core concept explained in the paper are highlighted in yellow 🟡 color.

🟢 - The important takeways or learnings are highlighted in green 🟢 color

🔴 - Important takeaways

🔴 + Underline - mini conlusions or crisp summary found in the paper are underlined

## Major learnings from paper

1.  fine-tuning has a much greater impact on the token representations of in-domain data and it **_DOES NOT_** lead to catastrophic forgetting
2.  fine-tuning tends to affect only the top few layers of BERT, but it majorly depends on across variation tasks.
3.  **fine-tuning leads the BERT model to change its representations for the fine-tuning domain but to continue to behave more like the Base model otherwise**
4.  although fine-tuning has a significant affect on the representations of in-domain sentences, the representations of out-of-domain examples remain much closer to those of the pre-trained model
