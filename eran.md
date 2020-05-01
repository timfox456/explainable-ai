# ERAN

ETH Robustness Analyzer for Neural Networks (ERAN) is analyzer to verify the resilience of a neural network against attacks.
The [original whitepaper](https://files.sri.inf.ethz.ch/website/papers/DeepZ.pdf) is here: https://files.sri.inf.ethz.ch/website/papers/DeepZ.pdf .
The GitHub repo for ERAN can be found at : https://github.com/eth-sri/eran

ERAN has been tested on CNN networks trained for CIFAR10 and MNIST datasets.


## Problem

Adversarial attacks can allow a neural network to incorrectly predict its outputs based on small changes to the inputs.
Networks should be protected against such attacks in training. 

Robustness verifies are classified as complete or incomplete.  Complete robustness verification is computation expensive but allows
verification without false positives.  Incomplete robustness allows false positives but are more scalable. 

ERAN measures robustness against adversarial attack.  ERAN's contribution is providing a common framework for running several 
different robustness metrics which take into account both complete and incomplete robustness verification.


## ERAN Analysis

ERAN combines the results of three robustness certifications:

**DeepZ** :  [DEEPZ](https://files.sri.inf.ethz.ch/website/papers/DeepZ.pdf) is a robustness certification that uses abstract Zonotope transformers to handle common activation functions in neural networks. This is an incomplete method that 
takes into account

**DeepPoly** : [DeepPoly](https://files.sri.inf.ethz.ch/website/papers/DeepPoly.pdf) is a based on a domain that combines floating point Polyhedra with Intervals.

**RefineZono** [RefineZono](https://files.sri.inf.ethz.ch/website/papers/RefineZono.pdf) combines incomplete DeepZ analysis with some complete methods (MILP and LP solvers) for more precision.


These three are combined together with ERAN to make a composite certification of robustness.


## Using ERAN

ERAN is a python library and can be installed along with its dependencies. Once installed ERAN can certify robustness of trained model.


Here is an example of running ERAN on the MNIST dataset:


```python
python3 . --netname ../nets/pytorch/mnist/convBig__DiffAI.pyt \ 
   --epsilon 0.1 --domain deepzono --dataset mnist

```

## Conclusion

ERAN is effective at providing an aggregated metric for robustness against adversarial attack by combining both complete and incomplete verification. It provides a 
python library to perform the robustness analysis.

