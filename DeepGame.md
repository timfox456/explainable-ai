# DeepGame

[DeepGame](https://github.com/TrustAI/DeepGame) is a game-based verification of deep neural networks
specifically for image recognition, classification, and similar problems.


## Problem

The observation is that adversarial examples tend fall along the boundary between the learned decision
boundary of the neural network and the human provided decision boundary.   In other words, these are
the "boundary" cases.  Cases far from the decision boundary are clear-cut, and likely to be classified
at a high rate of accuracy and thus resistant to adverserial attack.  However, cases close to the boundary
are more "iffy" and therefore likely to have lower rates of classification accuracy and far more
suceptible to adversierial attack.

[DeepGame](./images/DeepGame1.png)

The DeepGame algorithm attempts to solve two problems:

1. **The Maximum Safe Radius Problem**.  This problem identifies the maximum distance between the the learned 
decision that is "safe" or not susceptible to adversarial attack.

[](./images/DeepGame2.png)


The observation that cases far from the learned decision boundary are resistant to adverserial attack.


2. **The Feature Robustness Problem**. This problem attempts to find the features in an image most
robust against an adversarial training example.  For example, if in an image we saw a car, some trees,
and the sky, we would try to determine which of those identified features would be the most robust against
adversarial attack. 


## Criteria

DeepGame uses a rewards-based approach to optimize using the following criteria:

1. Monte-Carlo Tree Search
2. Alpha-Beta Pruning


[](./images/DeepGame-architecture.png)

## Solution

DeepGame employs an adversarial game-playing algorithm to optimize the two criteria.  One "player"
in the optimizer will attempt to optimize the feature selection, and the other player will attempt
to generate an adversarial example to defeat the newly feature selection.  The 

[](./images/DeepGame3.png)

## Usage

DeepGame can be downloaded from Github.  (https://www.github.com/TrustAI/DeepGame/) It does not appear
to be available in PyPI or in conda.  It can be run on trained models to get the results.

## Conclusion

DeepGame uses a game-based approach for verification of image recognition neural networks in order to
verify robustness against adversarial attack.


