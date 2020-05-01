# TorchRay

TorchRay is a a visualization library aimed at the process of *attribution*, which is the problem of determining which part of the input images is responsibel for the value computed by a neural network.

The [original whitepaper](https://arxiv.org/abs/1910.08485) informs of the 

The [github repo](https://github.com/facebookresearch/TorchRay) can be found here: https://github.com/facebookresearch/TorchRay.

TorchRay is, as the name implies, designed to work with pytorch and related libraries like torchvision.   pytorch is one of the most popular deep learning frameworks and is sponsored by Facebook.


## Problem

TorchRay is an attribution libarary focused on visualization techniques for 


## TorchRay Analysis

TorchRay is really two things: 

1. It introduces some novel approaches.  

TorchRay combines the results of three robustness certifications:

**DeepZ** :  [DEEPZ](https://files.sri.inf.ethz.ch/website/papers/DeepZ.pdf) is a robustness certification that uses abstract Zonotope transformers to handle common activation functions in neural networks. This is an incomplete method that 
takes into account

**DeepPoly** : [DeepPoly](https://files.sri.inf.ethz.ch/website/papers/DeepPoly.pdf) is a based on a domain that combines floating point Polyhedra with Intervals.

**RefineZono** [RefineZono](https://files.sri.inf.ethz.ch/website/papers/RefineZono.pdf) combines incomplete DeepZ analysis with some complete methods (MILP and LP solvers) for more precision.


These three are combined together with TorchRay to make a composite certification of robustness.


We should note that the authors of TorchRay have made no contributions to their github repo in the last 7 months and that there appears to be only one contribution total (the inital one), which indicates the project may no longer be under active development.  In AI termms this is lengthy.


## Using TorchRay

TorchRay is a python library and can be installed along with its dependencies using pip. `pip install torchray` will do it. Once installed TorchRay can certify robustness of trained model.

There are some examples in the [Github repo](https://github.com/facebookresearch/TorchRay)



## Conclusion

TorchRay seems most useful for its visualizalization capabilities. However as the project does not appear to be developed one may need to be careful relying on it.

