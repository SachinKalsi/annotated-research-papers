# FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness

Original Paper link: https://arxiv.org/abs/2205.14135

# Take aways from the paper
1. The time & memory complexity of self-attention are quadratic since these algorithms are not IO-aware
2. Approximate attention methods have been developed to reduce the complexity, including sparse-approximation (Ex: Reformer), low-rank approximations (Ex: Performer). 
3. All the alternatives focus on FLOP reduction & ignore memory-access time and due to this wall-clock speed remains the same.
4. Most operations in Transformers are bottlenecked by memory accesses & GPUs compute speed has out-paced memory speed, recent times
5. The main goal of FlashAttention is to avoid reading and writing the attention matrix to and from HBM (GPU Memory)
6. FlashAttention requires many times fewer HBM accesses compared to standard attention.
7. FlashAttention speeds up model training and improves model quality by modeling longer context.
8. Kernel Fusion: Combining multiple operations & making it a single function. This avoids multiple memory-access to HBM
9. Flash Attention
    1. Uses 2 concepts Tiling & Recomputation
    2. Tiling: Split of N x N Attn metrics into blocks of lesser size
    3. Recomputation: Recompute attn scores during back-prob, instead of storing & reading from HBM
    4. Algorithm:
        1. Partition Q, K, and V into blocks based on the available SRAM size.
        2. Iterate through each loaded block of K and V, analyze all blocks of Q, calculate normalization statistics, and save them to HBM
10. Even though FlashAttention has higher FLOP count compared to standard attention (due to recomputation in the backward pass), it has much fewer HBM accesses, resulting in much faster runtime.
11. FlashAttention achieves 2.8x speedup, while performing on par with standard attention.
12. FlashAttention is up to 20x more memory efficient than exact attention baselines, and is more memory-efficient than the approximate attention baselines

