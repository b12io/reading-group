# Reading
Normally we read papers, but we wanted a more accessible introduction to neural networks, so we read
* [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
* [Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/#fn1)

# Questions I have going in
* What is an RNN
* What is an LSTM network

## What is an RNN (largely from the first post)
* Most classifiers take a fixed-size input vector X and output a fixed-size output vector Y. This works well for, say, taking a fixed-size image and classifying it, or for taking a bunch of features and building a regression on them.
* But some inputs (e.g., a variable-length string of text) or outputs (e.g., a caption for an image) are not fixed in length.
* An RNN accepts a sequence element *x_t*, and in each of its layers, keeps around a hidden state vector *h* that it updates each time it reads in a sequence element. When deciding what to output for each sequence element, it combines not only the input *x_t*, but also its state vector *h*, updating *h* internally for future decisions while outputting some matrix operation on *h*. To make this happen, there are three matrices: *M_h, M_x, and M_y*. When deciding on *x_t*, it computes a new hidden state vector *h_t = tanh(M_x×x + M_h×h_t-1)*, and outputs *y=M_y×h_t*. [× is matrix multiplication, and tanh is a way to turn a float into -1/1].
* To make this a "deep learning" problem, you can imagine several layers of these RNNs, each one's *y* feeding in as the next one's *x*.
* Apparently LSTM (Long Short-Term Memory) is just a different way of computing *h_t* from *h_t-1*.
* To apply them to character generation/prediction, the input and output vectors are the length of your alphabet, with all 0's and a single 1 in the *i'th* vector location representing the *i'th* character in the alphabet. When looking at the output predictions, you pick the character with the highest output value of all of the vector indices. You then do standard neural network forward/backpropagation to slowly modify the values of the matrix parameters.
* How do you generate text from this learned model? Pick a seed letter and put it into the first layer. Look at the distribution of possible next letters and sample from them (weighing more likely next letters more). Now you've got two letters, and can sample a third, etc., until every layer's letter is selected.
* When trained on 5 different datasets, the post shows that you can learn the structure of everything from engish prose to Shakespeare (including calling out actors' parts) to the linux kernel (including c-like syntax).
* While these large neural networks are very hard to understand, the post tries to visualize individual neurons to see when they fire (I think this means: when do they make they "activate" the *tanh*). Some neurons activate based on depth of indentation for code, others based on pieces of syntax for code (e.g., "I'm in an `if` statement).


# 3 Takeaways


# Things that went unanswered
* What's the best way to learn about how training/forward/backpropagation works?


# Questions for B12 to ponder
* How can we use this to classify text/imagery?
* Can we use this to generate filler copy based on a customer's old data?


# Other references
* [The code behind the RNN post](https://github.com/karpathy/char-rnn)
* [The char-rnn repository referenced a paper on dropout, and I didn't know what that was](https://www.cs.toronto.edu/~hinton/absps/JMLRdropout.pdf). The short story: If you're training a network with lots of units will require lots of parameters to tune, which, if you don't have enough data, could result in overfitting. Dropout randomly removes units during training steps.
