## Nazar's crappy notes:

* CNNs are designed to recognize images (whereas RNNs are designed for sequences), but can be used for other data types
* Basic unit of CNN is a feature - small chunk of image data
* CNN efficiency depends on num. of features, their size, weights of layers
* speed depends on input size, scales linearly
* Layers:
	* convolution (multiplying feature to the part of the image)
	* relu: Rectified Linear Units
	* pooling (resizing)
* Backpropagation to assign weights to layers

## Adam questions
* I'd like to understand depth more. Is it just stacking all of the different filters together?
  * Lydia explained it: The input has a depth of 3 for the color channel. For the convolutional layers, the depth is the number of filters.
* What's the relationship between depth and interconnectedness?
  * You're connected to the folks in your neighborhood, e.g., you are connected to your northwest/northeast/southwest/southeast/south/nort/east/west neighbors, but not all of the other pixels.
* Are filters that different from features in traditional ML?
  * Lydia explained it: You don't pre-decide what the filters are going to be! The network learns that.
* What is the difference between stride and pooling? Both seem to shrink the image. (Reading farther down in [Getting rid of pooling](http://cs231n.github.io/convolutional-networks/), the authors make a similar suggestion.
* I didn't get any of the fully-connected/conv layer conversion stuff.
* Not a question, but this was heartening: `Instead of rolling your own architecture for a problem, you should look at whatever architecture currently works best on ImageNet, download a pretrained model and finetune it on your data`
