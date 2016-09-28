## Problem

Why don't we use larger batch ? It could allow us to parallelize (speed up) the training process over a cluster.

## Observation

Drop in generalization between small batch (SB) ($\leq 512$) and large batch (LB) to be as high as 5% even for smaller networks.

## Explanation

1. **Large-batch methods tend to converge to sharp minimizers of the training function. In contrast, small-batch methods are able to escape basins (sharp minimizers) and thus converge to flat minimizers.**

2. Large-batch methods tend to converge to minimizers closed to the initialization, whereas small batch methods move away and locate minimizers that are farther away.

## Experimental proof

### Parametric plots

Exploring the area between the $x^*_{LB}$ and $x^*_{SB}$.

### Sharpness of minima

Metric of sharpness

## Attempts to Alleviate the Problem

### Data Augmentation

While the LB method achieves accuracy comparable to the SB method (also with training data augmented), the sharpness of the minima still exists.

### Conservative Training

In [30], the authors argue that the convergence rate of SGD for the large-batch setting cna be improved by optaining iterates through a specific proximal sub-problem. Again, there is a statistically significant improvement in the testing accuracy

### Robust Training (Adversarial training)

Using adversarial images to do Data Augmentation. **Despite its intuitive appeal, we found that this strategy did not improve generalization outcoms. It remains to be shown whether adversarial training (or any other form of robust training) can be leveraged to increase the viability of large-batch training.**

## Discussion and Conclusion

Another prospective remedy includes the use of dynamic sampling or switching-based strategy which leverages small batches in the first few epochs and either gradually, or abruptly, transitions into a large-batch method.

**In our experiment, both sharp and flat minimizers exist at the similar depth.** To the best of out knowledge, the relative sharpness and frequency of minimizers on the loss surface remains to be explored theoretically.

Open questions :

- can one prove/disprove convergence of large-batch methods to sharp minimizers?
- what is the relative density of the two kinds of minima?
- can one design neural netwoek architectures for various tasks that account for sensitivity of LB methods?
- can the networks be initialized in a way that enables LB methods to succeed?
- is it possible, through algorithmic or regulatory means to steer LB methods away from sharp minimizers?
