# Incredible claims:
- Train only using about 10% of imagenet-12, i.e. around 120k images (i.e. they use 6k images per arm) get to the same or better accuracy as the equivalent VGG net
- Training is not via backprop but more simpler PCA + Sparsity regime (see section 4.1), shouldn't take more than 10 hours just on CPU probably (I think, from what they described, haven't worked it out fully).

[Reddit thread](https://www.reddit.com/r/MachineLearning/comments/50tbjp/stacked_approximated_regression_machine_a_simple/)
