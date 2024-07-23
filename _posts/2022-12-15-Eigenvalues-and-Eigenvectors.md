---
layout: post
title: Eigenvalues and Eigenvectors?
tags: [Math, Linear Algebra]
style: border
color: info
---

Eigenvalues and Eigenvectors are extremely useful tools that have a variety of uses including image processing, vibration analysis, stress tensor, and even the basic reproduction number used in the study of how diseases are spread.

## What are Eigenvalues and Eigenvectors?

Suppose the matrix $\textbf{A}$ represents a transformation. An eigenvector is a vector such that, after the transformation $\textbf{A}$ is applied to it, its direction does not change.

However, the scale / length of the vector may change. That specific factor by which the eigenvector is scaled after the transformation is applied to it is called its corresponding eigenvalue (often denoted by $\lambda$)

### Formal Definition

What we just defined above can be written formally as:

$$
\textbf{Av}=\lambda\textbf{v}
$$

Where $\textbf{A}$ is the matrix, $\textbf{v}$ is the eigenvector, and $\lambda$ is its corresponding eigenvalue.

## Calculating the Eigenvalues

Let's find the eigen values of a matrix $\textbf{A}$:

$$
\textbf{A}=\begin{bmatrix} -36 & 6 \\ 6 & -1 \end{bmatrix}
$$

We first subtract $\lambda$ across the diagonal of the matrix:

$$
\begin{bmatrix} -36 - \lambda & 6 \\ 6 & -1 - \lambda \end{bmatrix}
$$

Then take the determinant of this new matrix, which gives us a polynomial:

$$
\begin{vmatrix} -36 - \lambda & 6 \\ 6 & -1 - \lambda \end{vmatrix} = \lambda (\lambda + 37)
$$

If we equate this polynomial to zero and solve it, we get our eigenvalues:

$$
\lambda (\lambda + 37)=0\rightarrow\lambda_{1}=-37,\lambda_{2}=0
$$

Note that the eigenvalues may not always be real numbers, and they may also be repeated. If an eigenvalue is repeated, we say that its "multiplicity" is the number of times it is repeated.

The process we just did is written mathematically as $\text{det}(\textbf{A} - \lambda\textbf{I})$. The inner expression is explained further in the next section.

## Calculating Eigenvectors from Eigenvalues

Using the same matrix and eigen values from before:

$$
\textbf{A}=\begin{bmatrix} -36 & 6 \\ 6 & -1 \end{bmatrix}
$$

$$
\lambda_{1}=-37,\lambda_{2}=0
$$

Let us find the corresponding eigenvectors. To do this, we will solve the following equation:

$$
(\textbf{A}-\lambda\textbf{I})\textbf{v}=0
$$

Where $\textbf{A}$ is the matrix, $\textbf{v}$ is the eigenvector, $\lambda$ is its corresponding eigenvalue, and $\textbf{I}$ is the [identity matrix](https://en.wikipedia.org/wiki/Identity_matrix) with same dimensions as $\textbf{A}$.

For example, let's find the eigenvector corresponding to $\lambda_{1}$. First, we'll calculate the value of $\textbf{A}-\lambda\textbf{I}$:

$$
\textbf{A}-\lambda\textbf{I}=\begin{bmatrix} -36 - \lambda_1 & 6 \\ 6 & -1 - \lambda_1 \end{bmatrix}
$$

$$
\textbf{A}-\lambda\textbf{I}=\begin{bmatrix} -36 - (-37) & 6 \\ 6 & -1 - (-37) \end{bmatrix}
$$

$$
\textbf{A}-\lambda\textbf{I}=\begin{bmatrix} 1 & 6 \\ 6 & 36 \end{bmatrix}
$$

Suppose $\textbf{v}$ is the vector:

$$
\textbf{v}=\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
$$

Then our whole equation becomes a simple linear algebra problem:

$$
\begin{bmatrix} 1 & 6 \\ 6 & 36 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

We can write the augmented coefficient matrix for this equation:

$$
\left[\begin{array}{c c | c} 1 & 6 & 0 \\ 6 & 36 & 0 \\ \end{array}\right]
$$

Which can be solved by various methods such as [Gaussian Elimination]({{ site.baseurl }}{% post_url 2022-12-16-Solving-a-System-of-Linear-Equations %}#gaussian-elimination) or [Gauss-Jordan Elimination]({{ site.baseurl }}{% post_url 2022-12-16-Solving-a-System-of-Linear-Equations %}#gauss-jordan-elimination). You will find the values of the two unknowns $x_1$ and $x_2$, which are your components for the eigenvector, because we defined:

$$
\textbf{v}=\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
$$

Doing the same for the other eigenvalue will give you its corresponding eigenvector.
