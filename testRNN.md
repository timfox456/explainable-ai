# TestRNN

Coverage Guided Testing of Long-Short-Term Memory (LSTM) networks


## About testRNN

This is an description of the [testRNN](https://github.com/TrustAI/testRNN) library, which is located at: https://github.com/TrustAI/testRNN . 
We will examine its use cases and why it is useful. 

The authors appear to have forked the repo from another framework called [testingRNN](https://github.com/xiaoweih/testingRNN) which is located
here: https://github.com/xiaoweih/testingRNN .


## Problem

The code here seeks to test LSTM models against adversarial examples.   

Here are the test metrics that are used:

 * Neuron Coverage (NC),
 * Cell Coverage (CC),
 * Gate Coverage (GC),
 * Sequence Coverage (SQ)


## Approach

The author provides three models provided (and pretrained):
1. MNIST
2. Movie Review Sentiment Analysis
3. Lipophilicity Prediction (chemistry) -- this requires an additional library to handle the science aspect of the data

The models are trained by keras and serialized (`.h5` file) and put in the `models/' folder. 


## Library

The github is not so much a library but more of a demonstration. The library relies on keras with a tensorflow backend.



## Conclusion

testRNN is able to implement the four test metrics over a the three use cases. Of the three, the lipophilicity example
is interesting as it relies on observations and measurements as our use case is likely to do as well.

