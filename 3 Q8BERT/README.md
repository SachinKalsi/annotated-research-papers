# Q8BERT

Q8BERT is all about performing `quantization-aware training` during the fine-tuning phase of BERT in order to compress BERT by 4× with minimal accuracy loss.


## Annotation standards

🟡 - The important research or study with respect to the core concept explained in the paper are highlighted in yellow 🟡 color.

🟢 - The important takeways or learnings are highlighted in green 🟢 color

`Underline` - mini conlusions or crisp summary found in the paper are underlined

## Major learnings from the paper

1. Quantization is mainly done on GEMM (General Matrix Multiply) operations in BERT Fully Connected (FC) and Embedding layers.
2. Symmetric linear quantization has been used for quantizing both weights and activations to 8bit Integers (Int8). Its all boils down to finding the `scaling-factor`
3. Quantization-aware training is a method of training Neural Networks (NN) to be quantized at the inference stage, as opposed to post-training quantization. To achieve this `fake quanitization` has been used.
4. Fake quantization is an operation that simulates the rounding effect in Floating Point values.
5. Quantized BERT: Replaced all the Embedding and FC layers in BERT to the quantized Embedding and FC layers & **Operations that require higher precision, such as Softmax, Layer Normalization and GELU, are kept in FP32.**
