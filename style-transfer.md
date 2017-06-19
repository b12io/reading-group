# Reading
[A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576) by
Leon A. Gatys, Alexander S. Ecker and Matthias Bethge

# Questions I had before reading the paper
* How did they model “style” of an image so that they can learn the style and
transfer it from one image to another?

# Takeaways
* Representations of content and style in the CNN are *separable*.
* To generate image A from content of one image B and style of another image C,
perform gradient descent on a white-noise image until content loss function
(using layer 4 of VGG) is minimized between A and B and style loss function
(using 5 layers of VGG) is minimized between A and C.

# Notes
* content reconstruction vs. style reconstruction
* results generated on the basis of the VGG-Network, didn’t use FC layers
* replacing max-pooling with average pooling gave slightly more appealing
results
* to perform content reconstruction, perform gradient descent on a white noise
image to find another image that matches the feature responses of the original
image

# Things that went unanswered
* Gram matrix and derivative notation was not fully defined, so I’m not sure
what i, j, k represent
* Is gradient 0 if value is negative because they use ReLU?
* Is the assumption (for the algorithm to work) that multiple images can
generate similar feature maps at higher levels of the CNN? And that multiple
images can generate similar style representations?

# Discussion Questions
* Did the algorithm differ from what you expected?
* Why are feature correlations representative of style?
* How might we improve on this alogrithm?
* Performance: how long would it take to compute style transfer?
* How can we appply style transfer at B12?
