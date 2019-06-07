# Image-Super-Resolution
SRCNN
SRCNNs have a number of important characteristics. The most significant attributes are listed
below:
1. SRCNNs are fully convolutional (which is not to be confused with fully-connected). We
can input any image size (provided the width and height will tile) and run the SRCNN on it.
This makes SRCNNs very fast.
2. We train for filters, not for accuracy. Before we have been primarily concerned
with training our CNNs to achieve as high accuracy as possible on a given dataset. In
this context we’re concerned with the actual filters learned by the SRCNN which will enable
us to upscale an image—the actual accuracy obtained on the training dataset to learn these
filters is inconsequential.
3. They do not require solving an optimization on usage. After an SRCNN has learned a set
of filters, it can apply a simple forward pass to obtain the output super resolution image. We
do not have to optimize a loss function on a per-image basis to obtain the output.
4. They are totally end-to-end. Again, SRCNNs are totally end-to-end: input an image to
the network and obtain the higher resolution output. There are no intermediary steps. Once
training is complete we are ready to apply super resolution.
As mentioned above, the goal of our SRCNN is to learn a set of filters that allow us to map
low resolution inputs to a higher resolution output. Therefore, instead of actual full-resolution
images, we are going to construct two sets of image patches:
1. A low resolution patch that will be the input to the network
2. A high resolution patch that will be the target for the network to predict/reconstruct
In this way our SRCNN will learn how to reconstruct high resolution patches from low
resolution input ones. In practice, this means that we:
1. First need to build a dataset of low and high resolution input patches
2. Train a network to learn to map the low resolution patches to their high resolution counterparts
3. Create a script that utilizes loops over the input patches of a low resolution images, passes
them through the network, and then creates the output high resolution image from the
predicted patches.
