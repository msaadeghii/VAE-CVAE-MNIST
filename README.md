# Variational Autoencoder & Conditional Variational Autoenoder on MNIST


This is a forked version of the VAE-CVAE-MNIST provided by Tim Baumgärtner (https://github.com/timbmg/VAE-CVAE-MNIST). I just made several modifications which are summarized below:

1. I modified "train.py" to include the case corresponding to using a Gaussian MLP for the decoder. In this case, the reconstruction term of the loss is no longer BCE. In fact, I assumed a Gaussian observation model in which the covariance matrix is unknown. As opposed to the mean, which is modelled via a neural network (i.e., the decoder), in each epoch, the covariance matrix is updated using the learned decoder, and it admits a closed-form solution.

2. ...

*******************************************************************************

VAE paper: [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114)

CVAE paper: [Learning Structured Output Representation using Deep Conditional Generative Models](https://papers.nips.cc/paper/5775-learning-structured-output-representation-using-deep-conditional-generative-models)

---
In order to run _conditional_ variational autoencoder, add `--conditional` to the the command. Check out the other commandline options in the code for hyperparameter settings (like learning rate, batch size, encoder/decoder layer depth and size).

---

## Results

All plots obtained after 10 epochs of training. Hyperparameters accordning to default settings in the code; not tuned.

### z ~ q(z|x) and q(z|x,c)
The modeled latent distribution after 10 epochs and 100 samples per digit.

VAE | CVAE
--- | --- 
<img src="https://github.com/timbmg/VAE-CVAE-MNIST/blob/master/figs/1519649452.702026/E9-Dist.png" width="400"> | <img src="https://github.com/timbmg/VAE-CVAE-MNIST/blob/master/figs/1519649461.195146/E9-Dist.png" width="400">

### p(x|z) and p(x|z,c)
Randonly sampled z, and their output. For CVAE, each c has been given as input once.

VAE | CVAE
--- | --- 
<img src="https://github.com/timbmg/VAE-CVAE-MNIST/blob/master/figs/1519649452.702026/E9I937.png" width="400"> | <img src="https://github.com/timbmg/VAE-CVAE-MNIST/blob/master/figs/1519649461.195146/E9I937.png" width="400">
