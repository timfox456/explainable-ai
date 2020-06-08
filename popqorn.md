# POPQORN

Propagated output Quantified Robustness for RNNs


## About This

This is an description of the [POPQORN](https://github.com/albermax/innvestigate) library, which is located at: https://github.com/ZhaoyangLyu/POPQORN . 
We will examine its use cases and why it is useful. The [whitepaper](https://arxiv.org/pdf/1905.07387.pdf) is located here:  https://arxiv.org/pdf/1905.07387.pdf .

The author appears to have been influenced by another framework called CLEVER, though POPQORN is significantly expanded.


## Problem

LSTMs and GRUs are significantly harder to verify robustness against adversarial attack than conventional Neural Networks or even Convolutional
Neural Networks.  The authors identify the following problems:

First, they rely on hidden state (one state in the case of GRU, two in the case of LSTM), determined by three to four gates.  This 
complicates the result as the output is a function not only of the input but also of of 2-3 additional gate inputs: for example, in the case
of the LSTM a cell is determined by the input, short-term state, long-term state, and forget gate. 

Second, RNNs are applied to sequential data, such as time series data, whereas conventional examples assume that inputs are in the bottom layer.

Third, as adversarial examples can be generated with very minor changes in the sequence, one must evaluate the robustness to changes in just
one element of the sequence.

There is a need to come up with a mechanism for quantifying robustness against adversarial attack that takes into account these issues. At a
high-level, we want to quantify input features as a robustness to adversarial attack.  A high robustness for a feature, means that feature
can vary greatly and yet have little impact on the final result.  A low robustness means that even tiny changes in the input feature
can lead to large changes in the output, meaning that this feature is not robust to adversarial attacks.


## Approach

LSTMs and GRUs typically use nonlinear activation functions, namely sigmoid and tanh functions.  The POPQORN approach is to use replace
the activation functions with linear functions, lines for vanilla RNNs, and planes for LSTMs.  The first linear function becomes the lower 
bound, and the second linear function becomes the upper bound for robustness.  

The POPQORN approach then forward propagates inputs based on the upper and lower bound functions.  The output of the forward propagation is then 
calculated for both the high and the low bounds.  The robustness is simply a function off the difference between the forward propagated of the
upper and lower bound.

Of course, the coefficients of the linear functions are not chosen arbitrarily, but rather learned in a session of training. 

Once we have a trained model, we can use it to predict the robustness of each item in the sequence of the training example.  The authors give
an example of a natural language classifier.  The text input "What is the name of Roy Roger's dog?" is trained to be classified as an "entity."
"Entity" is the label, and the text is a sequential input.  For each of the items in the sequence there is a trained robustness.  In this case
the output is `[0.34, 0.50, 0.53, 0.27, 0.39, 0.19, 0.32, 1.02, 0.67, 0.93]`.  The *least* robust tokens in the input would in this case be "name",
"Roy" and "Roger", whereas the most robust tokens are the question-mark token and the ``s`.  

`What is   the   name  of   Roy  Roger 's   dog   ?`  

`0.34 0.50 0.53  0.53  0.27 0.19 0.32  1.02 0.67 0.93`



## Library

The POPQORN module appears to entirely be the work of the author and does not appear to have significant updates since June 2019.  It does not
appear to be in active development.  The library has a dependency on pytorch.

The examples included appear to include the following:

1. MNIST  (image)
2. News Classification (LSTM)  (text)


## Conclusion

POPQORN has some interesting ideas and its idea for calculating robustness using upper and lower bounds of linear functions is a fairly
simple one, and seems effective for the text classification problems defined (MNIST is not really a very relevant use case for RNNs).
It remains to be seen if POPQORN can be effective for time-series data. 

