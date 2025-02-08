---
layout: post
title: "Tutorial: Fundamentals of transformers"
date: 2023-10-27 00:00:00 +0000
type: unlisted
description:
img:
---
#### Contents

1. [Vision Transformer high level](#1-vision-transformer-high-level)
2. [Results](#2-results)
3. Components  
    a. [Self attention](#3-self-attention)  
    b. [Positional encoding](#4-positional-encodings)  
4. Modern transformers  
    a. [Group equivariant transformers](#5-group-equivariant-transformers)  
    b. [Shifted window vision transformers](#6-swin)  


### 1. Vision Transformer high level

> transformer = tokenisation + embedding + transformer encoder + task-specific "head"

**For now, ignore details about the encoder and positional encoding.**

![]({{site.baseurl}}/assets/img/transformers/overview.png)

_From_ [_The Illustrated Transformer_](https://jalammar.github.io/illustrated-transformer/)

Vision transformer: **only the tokeniser changes**: patch-based tokenisation. Everything else equivalent.

![]({{site.baseurl}}/assets/img/transformers/ViT.png)  

_From [Dosovitsky et al. An image is worth 16x16 words: transformers for image recognition at scale.](https://arxiv.org/abs/2010.11929 "https://arxiv.org/abs/2010.11929")_

Transformer encoder = **self-attention** + MLP (+ layernorm + skip connections)

![]({{site.baseurl}}/assets/img/transformers/encoder.png)  

_From [Vaswani et al. Attention is all you need](https://arxiv.org/abs/1706.03762 )_

Task specific head can be...

- Classification: MLP
- Image reconstruction: convolutional layer (e.g. swinIR, swinMR)
- Autoregressive tasks: transformer decoder with masked self-attention and cross-attention
    - Autoregressive machine translation better than non-autoregressive
    - Questionable with images: [_Cao et al. The Image Local Autoregressive Transformer_](https://arxiv.org/pdf/2106.02514.pdf)

## 2. Results

Example application: [_Lin et al. ViT enable fast and robust accelerated MRI_](https://proceedings.mlr.press/v172/lin22a/lin22a.pdf)

![]({{site.baseurl}}/assets/img/transformers/results.png)  

Compare performances wrt. pretraining performance, distribution shift.

## 3a. Self attention 

_Skip to 3:29: Attention_

<iframe width="560" height="315" src="https://www.youtube.com/embed/XSSTuhyAmnI?feature=oembed" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Self-attention matrix equations - taken from _[Romero et al. Group equivariant stand-alone self-attention for vision](https://arxiv.org/abs/2010.00977)_

>  Let rows of \\(\mathbf{X}\\) be vectors representing patch embeddings.  
> \\(\text{SA}(X)=\text{softmax}(\mathbf{Q}\mathbf{K}^T)\mathbf{V}=\text{softmax}(\mathbf{X}\mathbf{W}_Q(\mathbf{X}\mathbf{W}_K)^T)\mathbf{X}\mathbf{W}_V\\)  

+ dimensional normalising terms; where \\(\mathbf{W}_{\{Q,K,V\}}\\) learnable.

**Multi-head self-attention**: self-attention performed \\(h\\) times with \\(h\\) different \\(\mathbf{W}_{\{Q,K,V\}}\\) matrices, output concatenated and passed through one FC layer.

Advantages over convolution operation

- Convolution kernel constant across image, whereas now both “kernel” and impact of self-attention depends on the patch.
- Now each layer _can_ model long-range dependencies

## 3b. Positional encodings

_See above video. Skip to 7:55_

Summary:

- Positional encoder takes patch position \\(i\\) e.g. \\(i=\{1..9\}\\) and outputs a vector to be summed to embedding vector.
- Positional encoder can either be fixed (according to a complicated scheme) or learned.

> _Dosovitsky et al. -_ Position embeddings are added to the patch embeddings to retain positional information. We use standard learnable 1D position embeddings, since we have not observed significant performance gains from using more advanced 2D-aware position embeddings

**Absolute** positional encoding (taken from _Romero et al.)_

> \\(\text{SA}(x)=\text{softmax}(\mathbf{A})\mathbf{X}\mathbf{W}_V;\quad\mathbf{A}= (\mathbf{X}+\mathbf{P})\mathbf{W}_Q((\mathbf{X}+\mathbf{P})\mathbf{W}_K)^T\\)

**"Relative"** positional encoding

> Introduced by Shaw et al. (2018), relative encodings consider the _relative distance_ between the query token \\(i\\) (the token we compute the representation of), and the key token \\(j\\) (the token we attend to). The calculation of the attention scores then becomes:  
> 
> \\(\mathbf{A}_{i,j}=\mathbf{X}_i\mathbf{W}_Q((\mathbf{X}_j+\mathbf{P}_{x(j)-x(i)})\mathbf{W}_K)^T\\)


**Aside**: learned positional encodings experiments

> _Dosovitsky et al. -_ As we can see, while there is a large gap between the performances of the model with no positional embedding and models with positional embedding, there is little to no difference between different ways of encoding positional information. We speculate that since our Transformer encoder operates on patch-level inputs, as opposed to pixel-level, the differences in how to encode spatial information is less important. More precisely, in patch-level inputs, the spatial dimensions are much smaller than the original pixel-level inputs, e.g., 14 × 14 as opposed to 224 × 224, and learning to represent the spatial relations in this resolution is equally easy for these different positional encoding strategies.

![]({{site.baseurl}}/assets/img/transformers/posenc.png)



**Inductive bias:** _Dosovitsky et al._ - We note that Vision Transformer has much less image-specific inductive bias than CNNs. In CNNs, locality, two-dimensional neighborhood structure, and translation equivariance are baked into each layer throughout the whole model. In ViT, only MLP layers are local and translationally equivariant, while the self-attention layers are global. The two-dimensional neighborhood structure is used very sparingly: in the beginning of the model by cutting the image into patches and at fine-tuning time for adjusting the position embeddings for images of different resolution (as described below). Other than that, the position embeddings at initialization time carry no information about the 2D positions of the patches and all spatial relations between the patches have to be learned from scratch.


## 4a. Group equivariant transformers

_[Romero et al. Group equivariant stand-alone self-attention for vision](https://arxiv.org/abs/2010.00977):_

- Positional encodings that are G-equivariant impose G-equivariance of the whole transformer
- Self-attention without positional encodings is permutation invariant
- To more specifically impose other equivariances:
    - Translation: use relative positional encoding
    - Rotation: impose that positional encoding equal for all rotations
- Don’t perform as well as G-CNNs...


Question: can group equivariance properties of positional encoding be framed in the context of EI?

Probably not - since positional encoding acts on input images \\(A^\dagger x\\) rather than the actual images \\(x\\)?

## 4b. Swin

> _Liang et al. (swinIR paper)_ - Recently, Swin Transformer has shown great promise as it integrates the advantages of both CNN and Transformer. On the one hand, it has the advantage of CNN to process image with large size due to the local attention mechanism. On the other hand, it has the advantage of Transformer to model long-range dependency with the shifted window scheme.

[_Liu et al. Swin Transformer: Hierarchical Vision Transformer using Shifted Windows_](https://arxiv.org/pdf/2103.14030.pdf)

_Skip to 6:51 Swin Transformer Block_

<iframe width="560" height="315" src="https://www.youtube.com/embed/tFYxJZBAbE8?feature=oembed" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Applications:

[_Liang et al. SwinIR: Image restoration using Swin transformer_](https://arxiv.org/abs/2108.10257 "https://arxiv.org/abs/2108.10257")  

![]({{site.baseurl}}/assets/img/transformers/swin.png)