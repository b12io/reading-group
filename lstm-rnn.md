# Reading
Normally we read papers, but we wanted a more accessible introduction to neural networks, so we read
* [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
* [Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)

# Questions I have going in
* What is an RNN
* What is an LSTM network

# 3 Takeaways
* RNNs are cool because you can take in a variable amount of sequenced input without feature engineering, and emit a variable amount of sequenced output.
* The core trick in RNNs is to combine the latest input with some state that they self-update, giving them a sense of history.
* LSTMs are RNNs with internal architectures that help them learn from sequences with longer history.

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

## What is an LSTM network (largely from the second post)
* LSTMs are the predominant form of RNNs. When people say they use RNNs, they are probably using LSTMs in practice.
* Through some smart internal architecture tricks, they effectively lengthen the sequences from which RNNs can learn.
* In the diagrams, of sigmas (sigmoid functions) as being vectors that are either 0 or 1. When you dot them with an input vector, you therefore either fully keep or fully discard that input vector.
* Note: this confused me for a while, but *h_t* in these diagrams is the previous output, and *C_t* is the internal state. This notation is confusingly different than the RNN notation above. For clarity, I'll try to stay consistent with the notation above.
* The first step/gate is the forget gate. Based on the previous output *y_t-1* and the input *x_t*, you (through a sigmoid) create a vector of 0's (forget) and 1's (keep) that you dot with the internal state *h_t*. This causes you to forget some of the elements in the state from last iteration.
* The next step/gate is the input or addition gate. It also is based on the previous output and new input. It first (through a sigmoid) decides which elements to forget/keep, and then applies a tanh layer to create a vector of elements we'd consider adding to the state. By dotting those two vectors, we now have the elements we'll add to the internal state *h_t*.
* We set the new internal state *h_t = not forgotten state h_t-1 + newly added input state*.
* Now that the internal state is updated, we pass it through a tanh and turn off any vector values we want through a sigmoid. We feed this output to both the next step in the process, as well as to whoever it was that wanted a classification of the input.


# Things that went unanswered
* What's the best way to learn about how training/forward/backpropagation works?
* In an RNN, it seems like you can either add more hidden state to one layer or add another layer. How do you decide which to do?  In the code linked below, it seems like large networks have around 3 layers and 700 units per layer. What does hyperparameter search look like in this world?
* When deciding on the output of an LSTM, why do you pass it through a sigmoid (lose information) on the way to the tanh? What additional decision-power do you gain there that wouldn't be better spent elsewhere parameter-wise?

# Questions for B12 to ponder
* How can we use this to classify text/imagery?
* Can we use this to generate filler copy based on a customer's old data?


# Other references
* [The code behind the RNN post](https://github.com/karpathy/char-rnn)
* [The char-rnn repository referenced a paper on dropout, and I didn't know what that was](https://www.cs.toronto.edu/~hinton/absps/JMLRdropout.pdf). The short story: If you're training a network with lots of units will require lots of parameters to tune, which, if you don't have enough data, could result in overfitting. Dropout randomly removes units during training steps.
* [Some information on why parts of the LSTM architecture use sigmoids and others use tanh](https://www.quora.com/Why-using-sigmoid-and-tanh-as-the-activation-functions-in-LSTM-or-RNN-is-not-problematic-but-this-is-not-the-case-in-other-neural-nets). While I didn't fully get it, the intuition is that you use sigmoid functions when you want to be able to forget (since the sigmoid has a minimum at 0) whereas the tanh can go to -1.
* Our glorious former intern [Peter](http://peterdowns.com/) read these notes and had some super-helpful pointers re: some of our questions.  First: "*[This](https://colah.github.io/posts/2015-08-Backprop/) is the best description of backprop / forward prop that I've seen.*" Second: "*Also might want to explore [rectified linear unit activation](https://stats.stackexchange.com/questions/126238/what-are-the-advantages-of-relu-over-sigmoid-function-in-deep-neural-networks), which is what I saw most commonly in my brief stint doing deep learning on images last fall.*"
