# 1. Resumé

AdaNet is an algorithme that optimize the architecture and the weights of the network (DNN, CNN, RNN) after each "step". It is also effective as a regularization technique. They also described a large-scale implementation of the ADANET optimization problem using state-of-the-art
techniques from stochastic optimization.

AdaNet aims to reduce the large-scale hyperparameters tuning step (to reduce cross validation and grid search).

## 1.1 A framework for training neural networks that:
1. uses a stable and robust algorithm with a unique solution.
2. can produce much sparser and/or shallower networks compared to existing methods.
3. adapts the structure and complexity of the network to the difficulty of the particular problem
at hand, with no pre-defined architecture.
4. is accompanied and in fact motivated by strong data-dependent generalization bounds,
validating their adaptivity and statistical efficacy.
5. is intuitive from the cognitive standpoint that originally motivated neural network architectures.

## 1.2 Given Proofs
1. any intermediate layer k in the network is bounded by the empirical Rademacher complexity of its
input times a term that depends on a power of the size of the layer.
2. a bound on the complexity of every
layer in closed form without the need for any recurrence relation
3. the generalization bound that informs us that the complexity of the neural network returned is a
weighted combination of the complexities of each node in the neural network

(Work only with any 1-Lipschitz ($C=1$) activation function.)

## 1.3 AdaNet principle
At each round, it either augments the network with a new node (it is chosen with links only
to existing nodes in the network in the layer below plus a connection to the output unit) or updates the weights.

There is also the possibility to add a link between a new node one or several inputs. Thus, the family of DNN searched over can be larger than an classical feed-forward DNN.

## 1.4 Optimization
There algorithm can be viewed as an instance of the DeepBoost algorithm of Cortes et al. [2014]. However, unlike DeepBoost, which combines decision trees, ADANET algorithm learns a deep
neural network, which requires both deep learning-specific theoretical analysis as well as an online
method for constructing and searching new nodes.

## 1.5 Convergence
Remarkably, the neural network that ADANET outputs is competitive against the optimal weights for
any sub-network that it sees during training. Moreover, it achieves this guarantee in linear time


# 2. Personal questions
Not a single experimental results is given in this paper. Is it really better (in term of time) to use AdaNet to find the appropriate architecture ?

# 3. Useful concepts

## 3.1 Definition of C-Lipschitz function
A function $f$ such that 
$$| f(x) - f(y) | \leq C | x - y |$$
for all $x$ and $y$, where $C$ is a constant independent of $x$ and $y$.

## 3.2 Understanding Rademacher complexity:
https://www.cs.princeton.edu/courses/archive/spring13/cos511/scribe_notes/0305.pdf

## 3.3 VC-dimension

## 3.4 Covering number
