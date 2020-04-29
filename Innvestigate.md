# iNNvestigate


## About This

This is an description of the [iNNvestigate](https://github.com/albermax/innvestigate) library, which is located at: https://github.com/albermax/innvestigate . 
We will examine its use cases and why it is useful. The [whitepaper](https://arxiv.org/pdf/1808.04260.pdf) is located here: https://arxiv.org/pdf/1808.04260.pdf.


## Problem

Neural networks are treated as black boxes.  The desire to have "explainable" AI has triggered a large number of 
efforts to make explainable Machine Learning (XML). The way to describe this problem is attribution.  How can we attribute  There are a number of ways to do that. The two
most common classes of techniques are Gradient Attribution and Sensitivity.   Most of which compute the gradients
on the original image in terms of the prediction.  Often, this designed to create a sensitivity mask which will show
which pixels in the original image prove most predictive.

There are two desirable properties for Explainable Machine Learning: Sensitivity and Implementation Invariance.

Sensitivity means that if we change the inputs (i.e., the pixels on an image), and the output classification changes as a result, those same pixels
that changed should be attributed.  

Implementation Invariance means that even for different neural networks, the attributions should be the same for the same outputs and inputs.

## Solution

The need is there to make a common interface and standard for various implementations of explainable methods, and bring them together in a common
interface.  iNNvestigate provides a common python library to perform this.


## Implemented Methods

**Gradient Saliency Map**:  This method allows for inputs on the image with high gradients (i.e., more predictive) to
be illustrated and highlighted to the user. For example, an image identifying a truck in a neural network classifier 
would presumably have pixels that clearly illustrate the truck highlighted to explain exactly what pixels were used to make the truck.

**SmoothGrad**:  [SmoothGrad](https://arxiv.org/pdf/1706.03825.pdf) is a denoising technique for image prediction tasks that removes noise from the Gaussian gradient map. The problem
is that vanilla gradients are noisy and the sensitivity map is that there is so much noise that often it's not very meaningful.  SmoothGrad
combines a Gaussian noise and then averages the pixels to denoise the image. Please see the whitepaper: https://arxiv.org/pdf/1706.03825.pdf

**IntegratedGradients**: [IntegratedGradients](https://arxiv.org/abs/1703.01365) is another image related attribution methods. It is designed
to combined the Implementation Invariance of backprogagation methods with the Sensitivity of LRMs,etc

**DeConvNet**: [DeConvNet](https://arxiv.org/pdf/1505.04366.pdf) is a network that provides a *deconvolutional* behavior for CNNs, also 
in order to provide for attribution. 

**GuidedBackprop**: [GuidedBackprop]is a network that provides attribution 

**PatternNet/PatternAttribtution**: [PatternNet](https://arxiv.org/pdf/1705.05598.pdf) is a network yield a back-projection of the output image into the original image space.

**LRP**:  LRP is Layer-wise Relevance Propagation.    It means that gradients are backpropogated back to the input layer to display the contribution on a per-pixel
basis as relevant to the input. 

**DeepTaylor** [DeepTaylor](https://www.sciencedirect.com/science/article/pii/S0031320316303582), or Deep Taylor Composition is an extension of LRP using Taylor Series
expansion.



## Library

`innvestigate` is a python module that can be installed with `pip` or `conda`, or other similar package managements.  It is
used along with `keras.io` (not `tf.keras`) 

```bash
pip install innvestigate
```

iNNvestigate can the  be called in the following way.

Python Code:

```python
analyzer = innvestigate.create_analyzer("deep_taylor", model)  # create a deep_taylor

# Add batch axis and preprocess
x = preprocess(image[None])
# Apply analyzer w.r.t. maximum activated output-neuron
a = analyzer.analyze(x)

```

## Conclusion

iNNvestigate provides a standard interface and python framework to implement a number of different analyzers for showing attribution of the results of 
neural network predictions. By using iNNvestigate, one can quickly run a number of different approaches for explainable AI (XML).
