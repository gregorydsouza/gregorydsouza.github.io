---
layout: post
title: The Laplace Transform
tags: [Math, Linear Algebra, Calculus]
---

The Laplace transform has many uses. We will discuss how it can be used to reduce a differential equation into a simple algebra problem that is usually easier to solve.

Once we are able to solve the algebra problem, we invert the Laplace transform using an "inverse" Laplace transform that will return to us the solution to the original equation.

## Definition of the Laplace Transform

When we apply the Laplace transform to a function $f(t)$, it creates a whole new function with a different independent variable $F(s)$.

The Laplace transform is defined as the integral:

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st}f(t)\hspace{0.5em}dt
$$

Provided that this integral exists of course. If the integral is divergent, then we do not have a Laplace transform for that function.

You can see it takes the function $f(t)$ as an input and produces a new function $F(s)$ as its output.

You may also be wondering how we actually calculate the answer to an integral with infinite bounds. We do it my taking the limit of the integral as the upper bound approaches infinity. Here is an example of how you calculate the Laplace transform of the function $f(t) = e^{t}$

$$
f(t)=e^{t}
$$

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st}f(t)\hspace{0.5em}dt
$$

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st} e^{t}\hspace{0.5em}dt
$$

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st + t} \hspace{0.5em}dt
$$

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{t(1-s)} \hspace{0.5em}dt
$$

Before we evaluate the definite integral, let us first calculate the indefinite integral $\int e^{t(1-s)} \hspace{0.5em}dt$:

$$
\text{Take } u=t(1-s)\text{, then }\frac{du}{dt}=1-s, dt = \frac{1}{1-s}du
$$

$$
-\frac{1}{s-1}\int e^{u}\hspace{0.5em}du
$$

$$
-\frac{e^{u}}{s-1}\hspace{0.5em}
$$

$$
\text{Undo the substitution }u=t(1-s)
$$

$$
-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em} + C
$$

Now, let us calculate the definite integral

$$
\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{t(1-s)} \hspace{0.5em}dt = \left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]_{0}^{\infty}
$$

$$
\left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]^{\infty} - \left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]_{0}
$$

$$
\left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]^{\infty} - \left[-\frac{1}{s-1}\hspace{0.5em}\right]
$$

$$
\left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]^{\infty} + \frac{1}{s-1}\hspace{0.5em}
$$

Now, we just need to find the limit:

$$
\lim_{a\rightarrow \infty}\left[-\frac{e^{t(1-s)}}{s-1}\hspace{0.5em}\right]^{a} + \frac{1}{s-1}\hspace{0.5em}
$$

Looking at these two terms, we'll notice that if $s-1>0\rightarrow s>1$, then the first term will converge to zero. Therefore:

$$
F(s)=\frac{1}{s-1}\text{, assuming that }s>1
$$

An important note is that Laplace transforms are linear. The same function will always have the same Laplace transform. Also, you can construct new Laplace transforms from the Laplace transforms you already know.

This also means that each function input to the Laplace transform is its own inverse to the Laplace transform produced. That is to say:

$$
\mathcal{L}\{f(t)\} = F(s)
$$

$$
\mathcal{L}^{-1}\{F(s)\} = f(t)
$$

For this reason, we often keep handy a table of common Laplace transforms when calculating Laplace transforms by hand.

## Transforming a Differential Equation

Suppose we need to solve the following differential equation:

$$
x^{\prime\prime}(t) + x(t) = \cos(t)
$$

Or more simply written as:

$$
x^{\prime\prime} + x = \cos(t)
$$

We can solve it using the Laplace transform. Earlier we mentioned that the Laplace transform reduces the differential equation to an algebra problem. To apply the Laplace transform to an equation, we just need to find the Laplace transform of every term in the equation:

$$
\mathcal{L}\left[x^{\prime\prime}\right](s) + \mathcal{L}\left[x\right](s) = \mathcal{L}\left[\cos(t)\right](s)
$$

I have used a different notation here. Instead of $\mathcal{L}\{f(t)\}$, I'm using $\mathcal{L} [f(t)] (s)$. This notation also shows the independent variable of the new function produced by the Laplace transform.

Since the Laplace transform creates a new function from its input, we defined that new function as $F(s)$. Following that convention, we could define $\mathcal{L} \left[ x(t) \right] (s) = X(s)$.

However, what does $\mathcal{L} \left[ x^{\prime\prime}(t) \right] (s)$ become then? Well, let us first look over the general Laplace transform for these functions.

Suppose $f(t)$ and all its derivatives $f^{\prime}(t),f^{\prime\prime}(t),f^{\prime\prime\prime}(t)\cdots$ are continuous functions, then the Laplace transform of the $\text{n}^{\text{th}}$ derivative is given by:

$$
\mathcal{L} \left\{ f^{(n)} \right\} = {s^n}F(s) - {s^{n - 1}}f \left( 0 \right) - {s^{n - 2}}f' \left( 0 \right) \; \cdots \; s{f^{ (n - 2) }} \left( 0 \right) - {f^{ \left( {n - 1} \right) }} \left( 0 \right)
$$

Therefore:

$$
\mathcal{L}\left[x^{\prime\prime}(t)\right](s)=s^{2}X(s)-s\cdot x(0) - x^{\prime}(0)
$$

Substituting this back into our original equation yields:

$$
\left(s^{2}X(s)-s\cdot x(0) - x^{\prime}(0)\right) + X(s) = \mathcal{L}\left[\cos(t)\right](s)
$$

Using a table of Laplace transforms or a computer algebra system, you can find the Laplace transform of the remaining terms:

$$
\left(s^{2}X(s)-s\cdot x(0) - x^{\prime}(0)\right) + X(s) = \frac{s}{s^{2} + 1}
$$

Now, simply rearrange the equation so that $X(s)$ is the subject and simplify as much as possible. I assume you are familiar enough with algebra and the examples provided earlier that this is something you can do yourself, so I will skip straight to the rearranged equation:

$$
X(s) = \frac{s}{(s^{2} + 1)^2} + \frac{s\cdot x(0)}{s^{2} + 1} + \frac{x^{\prime}(0)}{s^{2} + 1}
$$

If you know the initial conditions, you can substitute them here, otherwise we'll skip straight to inverting the Laplace transform term-by-term:

$$
x(t) = \mathcal{L}^{-1}\left[\frac{s}{(s^{2} + 1)^2}\right](t) + \mathcal{L}^{-1}\left[\frac{s\cdot x(0)}{s^{2} + 1}\right](t) + \mathcal{L}^{-1}\left[\frac{x^{\prime}(0)}{s^{2} + 1}\right](t)
$$

Since $x(0)$ and $x^{\prime}(0)$ are part of the initial value problem (IVP), we'll assume they are constants and can pull them out of the inverse transforms:

$$
x(t) = \mathcal{L}^{-1}\left[\frac{s}{(s^{2} + 1)^2}\right](t) + x(0)\cdot\mathcal{L}^{-1}\left[\frac{s}{s^{2} + 1}\right](t) + x^{\prime}(0)\cdot\mathcal{L}^{-1}\left[\frac{1}{s^{2} + 1}\right](t)
$$

Again, using a table of Laplace transforms or a computer algebra systems, you can find the inverse of the Laplace transforms and return to the original equation:

$$
x(t) = \frac{1}{2}t\sin{(t)}+x(0)\cos{(t)}+x^{\prime}(0)\sin{(t)}
$$

This is the solved IVP! If you're looking for a general solution to the equation, redefine $x(0)=c_1$ and $x^{\prime}(0)=c_2$

$$
x(t) = \frac{1}{2}t\sin{(t)}+c_{1}\cos{(t)}+c_{2}\sin{(t)}
$$

This is the general method to solving a differential equation using the Laplace transform. As a brief overview:

-   Take the Laplace transform of each term in the equation
-   Laplace transform reduces the differential equation into an algebra problem
-   Rearrange the equation to make the transformed function the subject
-   Simplify as much as possible
-   Undo the Laplace transform
