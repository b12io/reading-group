# Reading
Normally we read papers, but we wanted a more accessible introduction to neural networks, so we read
* [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
* [Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/#fn1)

# Questions I have going in
* What is an RNN
* What is an LSTM network
* What does it mean to 

## What is an RNN
* Most classifiers take a fixed-size input vector X and output a fixed-size output vector Y. This works well for, say, taking a fixed-size image and classifying it, or for taking a bunch of features and building a regression on them.
* But some inputs (e.g., a variable-length string of text) or outputs (e.g., a caption for an image) are not fixed in length.
* An RNN accepts a sequence element *x_t*, and in each of its layers, keeps around a hidden state vector *h* that it updates each time it reads in a sequence element. When deciding what to output for each sequence element, it combines not only the input *x_t*, but also its state vector *h*, updating *h* internally for future decisions while outputting some matrix operation on *h*. To make this happen, there are three matrices: *M_h, M_x, and M_y*. When deciding on *x_t*, it computes a new hidden state vector *h_t = tanh(M_x×x + M_h×h_t-1)*, and outputs *y=M_y×h_t*. [× is matrix multiplication, and tanh is a way to turn a float into -1/1].
* To make this a "deep learning" problem, you can imagine several layers of these RNNs, each one's *y* feeding in as the next one's *x*.

# 3 Takeaways


# Questions for B12 to ponder
* How can we use this to classify text/imagery?
* Can we use this to generate filler copy based on a customer's old data?

# Other references
* [The code behind the RNN post](https://github.com/karpathy/char-rnn)
* [The char-rnn repository referenced a paper on dropout, and I didn't know what that was](https://www.cs.toronto.edu/~hinton/absps/JMLRdropout.pdf). The short story: If you're training a network with lots of units will require lots of parameters to tune, which, if you don't have enough data, could result in overfitting. Dropout randomly removes units during training steps.
