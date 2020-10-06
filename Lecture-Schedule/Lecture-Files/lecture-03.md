# Some notes from Lecture 03 of CPSC 515 2020W1

## Generic Bayes filter

* Data
  * States $x$, measurements $z$, actions $u$.
  * Assume you are given movement model $p(x_t|u_t,x_{t-1})$ and measurement model $p(z_t|x_t)$.
* Input: prior belief $b_{t-1}(x)$, measurement $z_t$, action $u_t$.
* Output: new belief $b_t(x)$.
* Movement update (convolution): Generates $\bar b_t(x)$ from $b_{t-1}(x)$ and $u_t$. 

  For all $x$:

    $$\bar b_t(x) = \sum_{x'} p(x|u_t,x') b_{t-1}(x')$$


* Measurement update (multiplication): Generates $b_t(x)$ from $\bar b_t(x)$ and $z_t$.

  Set $\eta = 0$

  For all $x$:

    $$\tilde b_t(x) = p(z_t|x) \bar b_t(x)$$
    $$\eta = \eta + \tilde b_t(x)$$

  For all $x$:

    $$ b_t(x) = \eta^{-1} \tilde b_t(x)$$

* Movement and measurement updates need not be strictly interleaved.
  * For example, if you move twice without receiving a sensor reading, you can just run the movement update twice.

* There are many ways of writing a Bayes Filter.  You should be able to spot them even when camoflaged by different notation or parametric representations.
  * Next week's localization algorithm (Kalman filters) uses a parameteric representation.

## Histogram Filter Implementation of Bayes Filter

* If your state space $x$ has $d$ dimensions with $n$ samples in each dimension, histogram representation of belief $b_t(x)$ is typically done with a $d$ dimensional array with a range of $n$ in each dimension; consequently it requires $O(n^d)$ storage.

* Movement update (convolution) cost $O(n^{2d})$ because you have to loop over both last state $x'$ and next state $x$.

* Measurement update cost $O(n^d)$ because you are looping only over current state $x$.

* These two calculations assume that the motion and movement models are $O(1)$ (constant time) to compute.