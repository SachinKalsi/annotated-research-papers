# Understanding the Disharmony between Dropout and Batch Normalization by Variance Shift

This paper was suggested in [Andrej Karpathy's](https://karpathy.ai/) one of the best blog [A Recipe for Training Neural Networks](https://karpathy.github.io/2019/04/25/recipe/)

## Annotation standards


🟡 - The important teaching or studying with respect to the paper are highlighted in yellow 🟡 color

🟢 - The important takeways or learnings are highlighted in green 🟢 color

`Underline` - mini conlusions or crisp summary found in the paper are underlined

## Major learnings from the paper
1. Dropout layer would shift the variance of a specific neural unit when the state of that network transfered from train to test.
2. When Dropout layer applied before Batch Normalisation (BN) layer and when the state changes from train to test, Dropout would scale the response by its Dropout retain ratio (i.e. p) that actually changes the neural variance as in learning, yet BN still maintains its statistical moving variance of X. This mismatch of variance could lead to a numerical instability which leads to erroneous predictions
3. There are 2 Solutions to solve the problem
   1. Apply Dropout **AFTER ALL BN LAYERS**
   2. Modify the formula of Dropout and made it less sensitive to variance.
4. The “Uout” (i.e., modified formula of Dropout) would be less affected by the insufficient training data than applying the last-layer Dropout


🔴🟠🟡🟢🔵🟣🟤⚫⚪🔘🛑⭕
