---
layout: post
title: Solving Systems of Linear Equations
tags: [Math, Linear Algebra]
style: border
color: success
---

You've probably come across and solved plenty of simultaneous equations in high school. However, you probably only dealt with two equations at most. Today we'll explore one of the basic concepts of linear algebra; using matrices to solve a system of linear equations.

## What is a Linear Equation?

Before we can start solving a linear equation, we'll first need to understand what they are.

A linear equation is simply an equation where the power (exponent) of all unknowns is 1. For example, the following equation is linear:

$$
3x + 4y = 1
$$

However, this equation is non-linear:

$$
2x^{2} + 3y = 8
$$

Because the exponent of one of the unknowns, $x$, is $2$.

A system of multiple linear equations is often called just a "system of equations".

## Solving a System of Equations

Let's deal with a simple example first. Suppose we have the following system of equations:

$$
8x_{1} - x_{2} = 9
$$

$$
4x_{1} + 9x_{2} = 7
$$

Notice that the equations have all the unknowns on the left side of the equation, with their coefficients, and all other constants simplified into a single expression on the right side of the equation.

Our first step is to construct a matrix from these equations. The specific matrix we are going to construct is called an "augmented coefficient matrix", but before that we'll first construct just a regular coefficient matrix.

A coefficient matrix is just a matrix that houses the coefficients of all the unknowns of the system. For the system of equations above, the coefficient matrix would be:

$$
\begin{bmatrix} 8 & -1 \\ 4 & 9 \end{bmatrix}
$$

You'll notice that this only includes the left side of the equation since all the unknowns were arranged there beforehand. So when we construct the coefficient matrix, we only consider half of the equations.

If we list out the constants on the other side of the equation, we'll get the following column vector:

$$
\begin{bmatrix} 9 \\ 7 \end{bmatrix}
$$

Simply inserting this vector to the right of the coefficient matrix forms the augmented coefficient matrix:

$$
\left[ \begin{array}{c c | c} 8 & -1 & 9 \\ 4 & 9 & 7 \end{array} \right]
$$

Although not necessary, we usually draw a dividing line between the coefficients and the constants when writing down the augmented coefficient matrix.

## Elementary Row Operations

Given any matrix, we have defined three operations that we can carry out on the rows of a matrix which keeps the old and new matrices equivalent. These operations are called _elementary row operations_ and are listed as follows:

-   Swap the positions of two rows
-   Multiply any one row by a non-zero number
-   Multiply a row by a number and add it to another row

## Row-Echelon Form

The following definition isn't very intuitive, so I'll explain further afterwards:

> A row-echelon matrix is a matrix where the first (leftmost) non-zero entry (called the _leading coefficient_) of every row is exactly one position to the right of the leading coefficient of the row above it.

All matrices of real numbers can be transformed into row-echelon form purely through elementary row operations.

### An intuitive understanding

I think the easiest way to get anyone to understand a row-echelon matrix is to just show them one:

$$
\begin{bmatrix} 0 & -1 & 9 & 3 \\ 0 & 0 & 7 & 1 \\ 0 & 0 & 0 & 5 \end{bmatrix}
$$

Perhaps the first thing you'll notice is that diagonal of leading coefficients going down, or the "staircase" of zeros in the matrix.

This is effectively all a row-echelon matrix is. For every row in the matrix, the first non-zero entry (called the _leading coefficient_) is one position to the right of the leading coefficient in the row above.

### Reduced Row-Echelon Form

A reduced row-echelon matrix is even simpler. It is just a row-echelon matrix with two extra rules:

-   All leading coefficients are exactly the number $1$.
-   For every column with a leading coefficient in it, all other entries are exactly zero.

Here's an example of a reduced row-echelon matrix:

$$
\begin{bmatrix} 1 & 0 & 0 & 7 \\ 0 & 1 & 0 & 3 \\ 0 & 0 & 1 & 9 \end{bmatrix}
$$

If we look at all the leading coefficients, we see that they're all exactly the number $1$. Also, if we split the matrix into its columns, every column that has a leading coefficient in it (basically meaning that we exclude the last column) has all other entries as exactly zero:

$$
\begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix} \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix} \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}
$$

Given any matrix of real numbers, there may be multiple row-echelon matrices that you can transform it into. This becomes a problem for computers to solve, however, there is **always only one reduced row-echelon matrix** for any given real number matrix.

## Gaussian Elimination

Gaussian Elimination is one of the algorithms we can use to solve a system of linear equations. It begins by first transforming the augmented coefficient matrix into row-echelon form. For our example above, this only requires one elementary row operation:

$$
\left[ \begin{array}{c c | c} 8 & -1 & 9 \\ 4 & 9 & 7 \end{array} \right] \xrightarrow{R_2 - \frac{1}{2}R_1 \rightarrow R_2} \begin{bmatrix} 8 & -1 & 9 \\ 0 & \frac{19}{2} & \frac{5}{2} \end{bmatrix}
$$

The two matrices are still equivalent because we have only used elementary row operations to transform one into the other. This means that the new matrix is also an augmented coefficient matrix!

The final step in Gaussian elimination after achieving row-echelon form is called "back substitution". This basically means we return from matrix form into equation form, and then solve the bottom most equation, _substitute_ its value _backwards_ into the equation above it, solve that equation, and repeat until all equations are solved.

First, let's return back into equation form. There is a simpler way to do this, but I'll first explain the formal method.

-   Split the augmented coefficient matrix back into the regular coefficient matrix and column vector of constants:
    $$
    \begin{bmatrix} 8 & -1 & 9 \\ 0 & \frac{19}{2} & \frac{5}{2} \end{bmatrix} \rightarrow \begin{bmatrix} 8 & -1 \\ 0 & \frac{19}{2} \end{bmatrix} \text{and} \begin{bmatrix} 9 \\ \frac{5}{2} \end{bmatrix}
    $$
-   Multiply the coefficient matrix by the column vector of unknowns
    $$
    \begin{bmatrix} 8 & -1 \\ 0 & \frac{19}{2} \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix} \rightarrow \begin{bmatrix} 8x_{1} - 1x_{2} \\ \frac{19}{2}x_{2} \end{bmatrix}
    $$
-   Equate it to the column vector of constants
    $$
    \begin{bmatrix} 8x_{1} - 1x_{2} \\ \frac{19}{2}x_{2} \end{bmatrix} = \begin{bmatrix} 9 \\ \frac{5}{2} \end{bmatrix}
    $$
-   Split them back into equations
    $$
    8x_{1} - x_{2} = 9
    $$
    $$
    \frac{19}{2}x_{2} = \frac{5}{2}
    $$
    Of course, reading through this you probably noticed that all we did was stick an equals sign between the last column and the rest of the matrix, shove the unknowns back in, and remove the square brackets. I've made a small animation to showcase this:

<center>
    <video align="center" width="640" height="480" style="pointer-events: none;" autoplay loop muted>
        <source src="/videos/SolvingSystemOfEquations/Manim_MatrixToEquations.mp4" type="video/mp4">
    </video>
</center>

Now of course, back substitution just tells us to solve these equations from bottom to top, and substitute the value of each unknown that we get from the previous equation into the one above it.

Doing this allows us to solve a system of equations pretty quickly and systematically. However, as I mentioned before, there is a minor problem.

Gaussian Elimination only specifies that the matrix should be in row-echelon form before we start our back substitution. However, as previously mentioned, there may be multiple row-echelon matrices that can be derived from an augmented coefficient matrix.

This makes it a little difficult for computers to solve since there are many ways to arrive at the same answer. The next section describes how we can fix this issue.

## Gauss-Jordan Elimination

The only difference between Gaussian Elimination and Gauss-Jordan elimination is the matrix we achieve before we carry out our back substitution.

Instead of just any row-echelon matrix, we specifically transform the augmented coefficient matrix into a reduced row-echelon matrix before we do the back substitution. As I mentioned earlier, there is only one reduced row-echelon matrix that you can derive from an augmented coefficient matrix, making it easier to program an algorithm for solving a system of equations.

Keep in mind that sometimes the additional computations required to achieve reduced row-echelon form may slow down how quickly we are able to solve the system of equations. Sometimes it may be beneficial to stop at an unreduced row-echelon form and just perform the back substitution to save time.

Using the same example from earlier, you'll see we need to do a few more elementary row operations to achieve reduced row-echelon form:

$$
\left[ \begin{array}{c c | c} 8 & -1 & 9 \\ 4 & 9 & 7 \end{array} \right] \xrightarrow{\frac{1}{8}R_1 \rightarrow R_1} \left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 4 & 9 & 7 \end{array} \right]
$$

$$
\left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 4 & 9 & 7 \end{array} \right] \xrightarrow{R_2 - 4R_1 \rightarrow R_2} \left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 0 & \frac{19}{2} & \frac{5}{2} \end{array} \right]
$$

$$
\left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 0 & \frac{19}{2} & \frac{5}{2} \end{array} \right] \xrightarrow{\frac{2}{19}R_2 \rightarrow R_2} \left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 0 & 1 & \frac{5}{19} \end{array} \right]
$$

$$
\left[ \begin{array}{c c | c} 1 & -\frac{1}{8} & \frac{9}{8} \\ 0 & 1 & \frac{5}{19} \end{array} \right] \xrightarrow{R_1 + \frac{1}{8}R_2 \rightarrow R_1} \left[ \begin{array}{c c | c} 1 & 0 & \frac{22}{19} \\ 0 & 1 & \frac{5}{19} \end{array} \right]
$$

Our next step is to convert the augmented matrix back into equations:

$$
1x_{1} + 0x_{2} = \frac{22}{19} \rightarrow x_{1} = \frac{22}{19}
$$

$$
0x_{1} + 1x_{2} = \frac{5}{19} \rightarrow x_{2} = \frac{5}{19}
$$

You'll notice however that, we don't need to back substitute anything! This is the beauty of reduced row-echelon matrices. We achieve a matrix with only a single unknown and a constant in each row, and all the coefficients of the unknowns are $1$.

So, when we return to equation form, we're left with equations that are already solved!

## Where do we use this?

You might think that solving a system of equations where the exponent of all unknowns is 1 isn't very useful. However, we deal with a lot of linear equations when solving both differential equations and systems of differential equations.

Linear algebra is also used extensively in rendering computer graphics, especially for 3-dimensional space. Solving systems of linear equations is one of the most basic and important tools Linear Algebra offers us.
