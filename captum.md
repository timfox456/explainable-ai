# Captum

Captum is a a model interpretability framework for pytorch. 

The [github repo](https://github.com/pytorch/captum) can be found here: https://github.com/pytorch/captum .

Captum is part of the pytorch project.  And so it is very actively developed and able to 


## Problem

Captum is an attribution libarary focused on visualization techniques for pytorch.   


## Attribution Methods

Captum Comes weith a wide Variety of attribution methods available:

 * Primary Attribution: Evaluates contribution of each input feature to the output of a model.
 * Layer Attribution: Evaluates contribution of each neuron in a given layer to the output of the model.
 * Neuron Attribution: Evaluates contribution of each input feature on the activation of a particular hidden neuron.


Here is a list of the specific algorithms available:

### Primary Attribution
 * Integrated Gradients
 * Gradient SHAP
 * DeepLIFT
 * DeepLIFT SHAP
 * Saliency
 * Input X Gradient
 * Guided Backpropagation and Deconvolution
 * Salient Deconvolutional Networks
 * Guided GradCAM
 * Feature Ablation
 * Feature Permutation
 * Occlusion
 * Shapley Value Sampling

### Layer Attribution
 * Layer Conductance
 * Internal Influence
 * Layer Activation
 * Layer Gradient X Activation
 * GradCAM
 * Layer Integrated Gradients
 * Layer DeepLIFT
 * Layer DeepLIFT SHAP
 * Layer Feature Ablation

###  Neuron Attribution
 * Neuron Conductance
 * Neuron Gradient
 * Neuron Integrated Gradients
 * Neuron GradientSHAP
 * Neuron DeepLIFT SHAP
 * Neuron Feature Ablation
 * Noise Tunnel
 * Smoothgrad: The mean of the sampled attributions is returned. This approximates smoothing the given attribution method with a Gaussian Kernel.
 * Smoothgrad Squared: The mean of the squared sample attributions is returned.
 * Vargrad: The variance of the sample attributions is returned.


## Captum Analysis

Captum has a very extensive set of attribution algorithms and is built-into pytorch. It also appears to be very actively developed.

Captum also includes a visualization capability called Captum Insights, which helps visualize the attribution,

![](



## Using Captum

Captum is a python library and can be installed along with its dependencies using conda or pip. `conda install captum -c pytorch` will do it. Once installed Captum can certify robustness of trained model.


There are some examples in the [Github repo](https://github.com/pytorch/cptum)



## Conclusion


Captum has a wide variety of attribution algorth

