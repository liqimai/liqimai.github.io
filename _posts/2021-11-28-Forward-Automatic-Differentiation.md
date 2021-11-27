---
layout: post
title: Forward Automatic Differentiation
excerpt: "Is back-propagation our only choice?"
modified: 28/11/2021, 01:47:24
tags: [automatic differentiation, forward AD, back-propagation]
comments: true
category: blog
related_posts: true
timeinfo: true
---
$$\newcommand{\Jac}[2]{\cfrac{\partial #1}{\partial #2}}$$
$$\newcommand{\jac}[2]{ {\partial #1}/{\partial #2} }$$
$$\newcommand{\bf}[1]{\mathbf #1}$$
1. Toc
{:toc}

# Abstract
Automatic Differentiation (AD) is one of the driving forces behind the success story of Deep Learning. Always main stream ML platform performs automatic differentiation in back-propagation manner. However, back-propagation is not the only style and also not always the best one to perform automatic differentiation. This article introduce another auto differentiation style, the Forward Automatic Differentiation, and discuss when and how forward AD is more favorable than backward AD, in terms of computational cost and space cost. 

# Introductory Example

Considering a simple computational graph as follows: 

$$\begin{equation}
    l(x) = h(g(f(x)))
\end{equation}$$

where 

$$\begin{align}
    y &= f(x) = Ax \\
    z &= g(y) = By \\
    l &= h(z) = Cz \\
\end{align}$$

They have Jacobian matrix:

$$\begin{equation}
    \Jac yx = A \in \mathbb{R}^{n_y\times n_x}
\end{equation}$$

$$\begin{equation}
    \Jac zy = B \in \mathbb{R}^{n_z\times n_y}
\end{equation}$$

$$\begin{equation}
    \Jac lz = C \in \mathbb{R}^{n_l\times n_z}
\end{equation}$$

You may image \\(l\\) as some loss function we want to differentiate with respect to \\(x\\). i.e. we want to obtain \\(\Jac lx\\).

## Backward Automatic Differentiation 
Actually, by applying chain rule, we can easily obtain \\(\Jac lx\\):

- Step 1: \\(\Jac lz = C\\)

- Step 2: \\(\Jac ly = \Jac lz \Jac zy = CB\\)

- Step 3: \\(\Jac lx = \Jac ly \Jac zy = CBA\\)

We first obtain the differentiation of \\(l\\) with respect to \\(z\\), then \\(y\\), and finally \\(x\\), in an order of from output to input, so this is referred as back-propagation, or Backward Automatic Differentiation (Backward AD). 

In a line, the backward AD is calculated as 

$$\boxed{\Jac lz = \left(\Jac lz \Jac zy\right) \Jac yx = (CB)A}$$

## Forward Automatic Differentiation
However, back-propagation is not the only style and also not always the best one to perform automatic differentiation. There is another auto differentiation style, the Forward Automatic Differentiation (Forward AD):

- Step 1: \\(\Jac yx = A\\)

- Step 2: \\(\Jac zx = \Jac zy \Jac yx = BA\\)

- Step 3: \\(\Jac lx = \Jac lz \Jac zxs = CBA\\)

We always calculate the differentiation with respect ot \\(x\\). First, \\(y\\) with respect ot \\(x\\), then \\(z\\) with respect ot \\(x\\), finally \\(l\\) with respect ot \\(x\\). Since this is in the same order as the forward pass of evaluating the function \\(l(x) = h(g(f(x)))\\) itself, this differentiation mode is named as Forward Automatic Differentiation. 

In a line, the Forward AD is calculated as 

$$\boxed{\Jac lz = \Jac lz \left(\Jac zy \Jac yx\right) = C(BA)}$$

# A More Formal Compare
Now we consider the general case. Assume we want differentiate following function

$$l = f_k\left(\cdots f_3\left(f_2\left(f_1\left( X \right)\right)\right)\right).$$

Denote the Jacobian matrices of each single function by \\(\bf J_1, \bf J_2, \cdots, \bf J_k\\):

$$\begin{align}
\bf J_1 &= \jac {f_1} {x} \\
\bf J_2 &= \jac {f_2} {f_1} \\
\bf J_3 &= \jac {f_3} {f_2} \\
&\vdots \\
\bf J_{k-1} &= \jac {f_{k-1}} {f_{k-2}} \\
\bf J_k &= \jac {f_k} {f_{k-1}} \\
\end{align}$$

By chain rule, the final Jacobian matrix we want is 

$$\Jac lx = 
\bf {J_k} 
\bf {J_{k-1}} 
\cdots
\bf {J_{3}} 
\bf {J_{2}} 
\bf {J_{1}}.$$

__Backward AD computes above matrix product from left to right:__

$$\boxed{
\Jac lx = 
\left(
    \left(
        \left(
            \left(
                \bf {J_k} \bf {J_{k-1}} 
            \right)
            \cdots \bf {J_{3}} 
        \right)
    \bf {J_{2}} 
    \right)
    \bf {J_{1}}
\right)}$$

__Forward AD computes above matrix product from right to left.__

$$\boxed{
\Jac lx = 
\left(
    \bf {J_k}
    \left( 
        \bf {J_{k-1}}
        \cdots 
        \left( \bf {J_{3}}
            \left( 
                \bf {J_{2}} \bf {J_{1}}
            \right)
        \right)
    \right)
\right)}$$

## Computational Cost 

Although matrix multiplication is associative, the complexity is not associative. The computational complexity depend dramatically on this order. Denote dimension of \\(x, f_1, f_2 \dots f_k\\) by \\(N_0, N_1, \dots, N_k\\):

$$x\in \mathbb R^{N_0}, f_1\in\mathbb R^{N_1}, \dots, f_k\in\mathbb R^{N_k}.$$

Computational complexity of two methods are summarized below:

|           | Computational Complexity               | When it is faster?     |
|:--------- |:---------------------------------------| :---------------------:|
|Backward AD| \\(O(N_k \sum_{i=1}^{k-1} N_{i} N_{i-1})\\)| faster if \\(N_k > N_0\\)  |
|Forward  AD| \\(O(N_0 \sum_{i=1}^{k-1} N_{i} N_{i+1})\\)| faster if \\(N_k < N_0\\)  |

Check their difference:

$$\begin{align}
 \text{Backward} - \text{Forward}
% = & N_k \sum_{i=1}^{k-1} N_{i} N_{i-1} - N_0 \sum_{i=1}^{k-1} N_{i} N_{i+1}\\
% = & N_k \sum_{i=0}^{k-2} N_{i} N_{i+1} - N_0 \sum_{i=1}^{k-1} N_{i} N_{i+1}\\
= \left((N_k-N_0) \sum_{i=1}^{k-2} N_{i} N_{i+1}\right) + N_0 N_k \left(N_1 - N_{k-1}\right)
\end{align}$$

The difference is dominated by first term, so we conclude that

- __When \\(N_k > N_0\\), backward AD is fast.__
- __When \\(N_k < N_0\\), forward AD is fast.__
- Backward/Forward \\(\approx \cfrac{N_k}{N_0}\\).

__In machine learning scenario, the loss function \\(l\\) is a scalar in most case, i.e., \\(N_k = 1\\), so backward AD is more favorable__, which also explains the popularity of back-propagation among machine learning platforms.

__Note__: above discussion are made under assumption that all Jacobian matrix \\(\bf J_i\\) are ordinary dense matrix without any special structure, thus computational cost of the multiplication is cubic. Some operations, such as convolution, does not follow the assumption. The Jacobian matrix of convolution is super sparse. This assumption is also made in following discussion.

## Memory Cost
### General Discussion
However, forward AD cost less memory space sometime, because it only need to go through the computational graph for one pass. 

__Backward AD__ need to go through the whole computational graph for two passes.

- forward-pass: evaluating the function \\(l\\) it self.
- backward-pass: calculate \\(\Jac lx\\) as equation above.

In forward-pass, we need to store \\(\bf J_1, \bf J_2, \bf J_3, \dots, \bf J_k\\) all in the memory, because they are needed in the backward-pass. A good news is that during the back-propagation, we may gradually release space occupied by \\(\bf J_i\\) after \\(\bf J_i\\) being used. For example, we propagate back to \\(f_i\\), we only need \\(\bf J_1, \bf J_2, \dots, \bf J_i\\) and \\(\Jac {l}{f_i}\\) to finished remaining calculation. Matrices \\(\bf J_{i+1}, \dots, \bf J_k\\) are no longer needed anymore, thus can be freed and replaced by a single $\Jac {l}{f_i}$. However, in some case, a single \\(\Jac {l}{f_i}\\) may occupy even more space than \\(\bf J_{i+1}, \dots, \bf J_k\\) all together. In summary, the maximum space cost is 

$$\max_i(N_kN_i + \sum_{j=1}^i N_j N_{j-1})$$ 

Note: the total space cost is even larger, because temporary variables during back-propagation also cost space.

__Forward AD__, in contrast, only need to go through the computational graph for a single pass as following steps:

- Step 1: evaluate \\(f_1 = f_1(x)\\), and its differentiation \\(\Jac {f_1} {x} = \bf J_1\\).
- Step 2: evaluate \\(f_2 = f_2(f_1)\\), and its differentiation \\(\Jac {f_2} {x} = \bf J_2 \Jac {f_1}x\\).
- Step 3: evaluate \\(f_3 = f_3(f_2)\\), and its differentiation \\(\Jac {f_3} {x} = \bf J_3 \Jac {f_2} {x}\\).
- ...
- Step k: evaluate \\(f_k = f_k(f_{k-1})\\), and its differentiation \\(\Jac {f_1} {x} = \bf J_k \Jac {f_{k-1}} {x}\\).

Each step only relies on the \\(f_i\\) and \\(\Jac {f_i} x\\) obtained in last step, so we can drop \\(\bf J_i\\) immediately after use to save space. As a result, the space cost is only 

$$\max_{i} \left(N_0N_i + N_0N_{i+1} + N_iN_{i+1} \right).$$

Space cost of two methods are summarized below:

|           | Space Complexity                                                |
|:--------- |:----------------------------------------------------------------|
|Backward AD| \\(\max\limits_i(N_kN_i + \sum\limits_{j=1}^i N_j N_{j-1})\\)              |
|Forward  AD| \\(\max\limits_{i} \left(N_0N_i + N_0N_{i+1} + N_iN_{i+1} \right)\\)|

Their is no simple pattern to decide which one costs less space. Generally, if network is deep (large k), then backward AD need to store lots of Jacobian matrix \\(\bf J_i\\) and tend to consume more space than forward AD. If network input size is greatly larger than its output size (\\(N_0 \gg N_k\\)), then Forward AD tend consume more space than backward AD.

### A Special Case -- Trumpet-Like Network
For a special yet common family of networks -- the network with trumpet-like  architecture, forward AD do have spatial advantage. A networks is said to have trumpet-like architecture, if its width gradually decreases from input layer to output layer, like a trumpet. More formally, if \\(N_0 \ge N_1 \ge \dots \ge N_k\\), then the network is a trumpet-like network. 

|           | Space Complexity of Trumpet-Like Networks  |
|:--------- |:-------------------------------------------|
|Backward AD| \\(\sum\limits_{j=1}^k N_j N_{j-1}\\)          |
|Forward  AD| \\(N_0 N_1 + N_0 N_2 + N_1 N_2\\)|

If the network is deep (k>2), and first two hidden layer is as wide as input layer \\(x\\), then Forward AD consume less space than Backward AD. Especially when the network is super deep, forward AD consumes far less space than backward AD.


# Go Beyond Backward and Forward - Auto-Differentiation in Arbitrary Order

The difference of backward and forward AD in nature is the different order of calculating matrix chain:

$$\Jac lx = 
\bf {J_k} 
\bf {J_{k-1}} 
\cdots
\bf {J_{3}} 
\bf {J_{2}} 
\bf {J_{1}}.$$

One computes from left to right, another one computes from right to left. However, matrix chain actually can be calculated in arbitrary order, due to the associativity of multiplication. 

The best order may be neither left to right nor right to left. For example, consider a matrix \\(A\\) of size \\(N\times N\\) and a column vector \\(x\\) of size \\(N\times 1\\). Now we want to evaluate \\(Axx^\top A\\).

|             | Formula                                | Computational Cost |
|:-----------:|:--------------------------------------:|:------------------ |
|Left to right| \\(\left(\left(Ax\right)x^\top\right)A\\)  | \\(O(N^3)\\)           |
|Right to Left| \\(A\left(x\left(x^\top A\right)\right)\\) | \\(O(N^3)\\)           |
|Fastest One  | \\(\left(Ax\right)\left(x^\top A\right)\\) | \\(O(N^2)\\)           |

For the left to right one, intermediate result \\(\left(\left(Ax\right)x^\top\right)\\) produce a matrix of size \\(N\times N\\). When this intermediate result multiplies \\(A\\), the cost is \\(O(N^3)\\). Right to Left one is similar. For the fastest one, \\(Ax\\) and \\(\left(x^\top A\right)\\) produce a column vector and a row vector, and their multiplication only takes \\(O(N^2)\\).

If you are allowed to evaluating the matrix chain \\(\bf {J_k} \bf {J_{k-1}} \cdots\bf {J_{3}} \bf {J_{2}} \bf {J_{1}}\\) in arbitrary order, it is very likely we could find one faster much faster than the backward Ad and forward AD. The problem of finding the fastest order to evaluate a matrix chain is known as [__matrix chain ordering problem__](https://en.wikipedia.org/wiki/Matrix_chain_multiplication). According to Wikipedia, the faster algorithm to solve matrix chain ordering problem only takes \\(O(k\log(k))\\) time. This result sounds promising. In future, perhaps we may speed current machine learning platform by solving the matrix chain ordering problem before differentiation. 

The forward AD can also be performed with the help of dual numbers, which could result in a very tiny implementation and beautiful mathematical explanation. But in nature, it is nothing more than changing the differentiation into forward order. Interested reader may read Robert [Tjarko Lange's blog](https://roberttlange.github.io/posts/2019/08/blog-post-6/) for more information.