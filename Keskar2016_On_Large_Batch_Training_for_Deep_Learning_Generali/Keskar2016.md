## Observation

Drop in generalization between small batch (SB) ($\leq 512$) and large batch (LB) to be as high as 5% even for smaller networks.

## Explanation

1. Large-batch methods tend to converge to sharp minimizers of the training function. In contrast, small-batch methods are able to escape basins (sharp minimizers) and thus converge to flat minimizers.

2. Large-batch methods tend to converge to minimizers closed to the initialization.


## Experimental proof

### Parametric plots

Exploring the area between the $x_{LB}*$ and $x_{SB}*$.

### Sharpness of minima

Metric of sharpness
