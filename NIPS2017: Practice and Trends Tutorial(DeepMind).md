#### Link: https://www.facebook.com/nipsfoundation/videos/1552060484885185/

### Summary

#### Practice:
- The Deep learning toolbox
  - Zooming out
    - Platform (CPUs, GPUs, Cloud, ...)
    - Framework
    - Dataset
  - Zooming in
    - Non-Linearties
    - optimizers
    - Connectivity patterns
    - Losses
    - **Hyperparams**


- Building Blocks
1. Convolutions

  In deep learning we want less customized features but we have some inductive biases. The main advantage of convs compared         to fully connected layers is locality and translation invariance, which is extremely important for images and this is our inductive bias about using convs. Translation invariance is enforced by weight sharing, the same filter is applied to the whole input (image/feature map).

  Deep networks are very powerful. However training them is not easy, first computational complexity, we can parallelize convs (width), but depth has to be sequential. Secondly, optimization is very challenging.
  
  More recently, we moved to use smaller kernels (usually 3x3), mainly because it gives more depth with less params. Many tricks helped with training deeper nets (batchnorm, better weight intilization), adding residual connections and skip connections was surely very important.
  
2. Recurrence and sequence
  
  
### Trends 

1. Autoregressive models

We can break generative models in: latent variable models (VAEs), implicit (GANs). They gave an example with audio using causal convolution (a convolution with signal processing where the output only depeds on the previous time steps, it cannot use the future). Archs to be used with autoregressive models can be (recurrent, causal convs, causal convs+ attention, attention only). Loss functions can be (xentropy[Discrete], Gaussian likelihood [Continous]).

Causal archs work in O(n) time, we need to pass by all previous time steps to predict the next time step." Parallel wavenet: fast high fidelity speech system" paper fixes that, they use a Teacher/Student approach, the student network starts with noise similar to GANs, and it generates the whole waveform in parallel, while it get critsized by the teacher network. This generation works in O(1), this method can be called distillation. 

Causal convs can be faster than RNNs as they don't need to unroll and they can parallelize in previous time steps. Finally, they mentioned attention only models "Attention is all you need"

2. Domain Alignment

We have related data from multiple domains (cat images with photos and sketches). A paper called "Doman-adversarial train of neural networks" tackles this problem, they add another head to the network that predicts the domain, however, when backpropgating, they inverse the gradients, the goal is to make it harder for the network to distiguish domains while getting better at classification, encouraging learning domain invariant features.

Cycle consistency loss (CycleGAN), if we have two domains X, Y. We should be able to transfer from X to Y and then back to X to get the same thing and vice verse.

"Unsupervised image to image translation networks" uses encoder/decoder method, they have separate encoders/decoders for each domain, however they learn a shared latent space z. In test time, an image from domain X can be encoded to a latent variable z then decoded using domain Y decoder to get an image closer to domain Y.

3. Meta learning/ Learning to learn

While standard learning have a training data and testing data, it uses batches from training data to get a maxmize a probablity. Meta learning uses a whole learning cycle over training and testing data as only one instance.

Learning to learn can be broke down to:
  - Model based learning
  - Metric based
  - optimization based
  
4. Graph Networks

While spatial inductive bias for images (CNNs), sequence inductive bias for (RNNs). The inductive bias we have for graph networks is that if a node is renamed, the graph should be still the same. Firsly, we discuss Message passing neural networks (MPNN) 
