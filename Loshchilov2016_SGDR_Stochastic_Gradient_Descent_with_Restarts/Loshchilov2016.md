## Résumé

State of the art on Cifar10 and Cifar100 with Wild Residual Network and SGDR (to be 0.5-1% more accurate). 

**SGDR principles** : Decaying the learning rate from $\eta_{max}$ to $\eta_{min}$ every $T_i$ epoch. $T_i$ can increase along the training process, and $\eta^i_{max}$ can decrease. However, the latter is fixed to reduce the number of hyperparameters to tune.

$$ \eta_t  = \eta^i_{min} + \frac{1}{2} ( \eta^i_{min} -  \eta^i_{max}) (1 + cos(\frac{T_{cur}}{T_i} \pi )) $$
