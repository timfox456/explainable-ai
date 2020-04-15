# DeepGame

[DeepGame](https://github.com/TrustAI/DeepGame) is a game-based verification of deep neural networks
specifically for image recognition, classification, and similar problems.


## Problem

THe observation is that adverserial examples tend fall along the boundary between the learned decision
boundary of the neural network and the human provided decision boundary

[DeepGame](./images/DeepGame1.png)

The DeepGame algorithm attempts to solve two problems:

1. **The Maximum Safe Radius Problem**.  This problem identifies the maximum distance between the the learned 
decision that is "safe" or not suceptible to adverserial attack.

[](./images/DeepGame2.png)


2. **The Feature Robustness Problem**. This problem attempts to find the features in an image most
robust against an adverserial training example.  For example, if in an image we saw a car, some trees,
and the sky, we would try to determine which of those identified features would be the most robust against
adverserial attack. 


## Criteria

DeepGame uses a rewards-based approach to optimize using the following criteria:

1. Monte-Carlo Tree Search
2. Alpha-Beta Pruning


[](./images/DeepGame-architecture.png)

## Solution

DeepGame employs an adverserial game-playing algorithm to optimize the two criteria.  One "player"
in the optimizer will attempt to optimize the feature selection, and the other player will attempt
to gneerate an adverserial example to defeat the newly feature selection.  THe 

[](./images/DeepGame3.png)

## Usage

DeepGame can be downloaded from Github.  (https://www.github.com/TrustAI/DeepGame/) It does not appear
to be available in PyPI or in Conda.  It can be run on trained models to get the results.

## Conclusion

DeepGame uses a game-based approach for verification of image recognition neural networks in order to
verify robustness against adverserial attack.


