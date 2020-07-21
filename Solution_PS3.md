---
layout: default
title: "PS3 Solution"
---

# Solution to Continuous Probability Problem Set


#### 1. Question 3 from Grinstead and Snell, Section 2.2
Suppose you choose a real number $X$ from the interval $[2,10]$ with a probability density function of the form
$$
f(x)=\frac{C}{x}.
$$

1. What is the value of $C$?
We know that the density must integrate to $1$ over the sample space $\Omega_x = [2,10]$.  Thus,

$$
\begin{eqnarray}
\int_2^{10} \frac{C}{x} dx &=& \left. C\log(x)\right|_2^{10}\\
& = & C\left[\log(10)-\log(2)\right] \\
\Rightarrow C & = & \frac{1}{\log(10)-\log(2)} \approx 0.6213
\end{eqnarray}
$$


2. Find $P(E)$, where $E=[a,b]$ is a subinterval of $[2,10]$.

$$
\begin{eqnarray}
P(E) &=& \int_a^b f(x) dx\\
& = & C\left[\log(b) - \log(a)\right] \\
& = & \frac{\log(b) - \log(a)}{\log(10)-\log(2)}
& = & \frac{\log(b/a)}{\log(5)}\\
&=& \log_5 (b/a)
\end{eqnarray}
$$

3. Find $P(X>5)$, $P(X<7)$, and $P(X^2-12X+35>0)$.

$$
P(X>5) = \int_5^{10} \frac{C}{x} dx = \frac{\log(2)}{\log(5)} \approx 0.431
$$

$$
P(X<7) = \int_2^7 \frac{C}{x} dx = \frac{\log(7/2)}{\log(5)} \approx 0.778
$$

First, we can factor $g(X) = X^2-12X+35=(X-5)(X-7)$.  So  $g(X)=0$ when $X=5$ and $X=7$.  In between these two points, the quadratic $g(X)<0$.  Thus,
$$
\begin{eqnarray}
P(X^2-12X+35>0) &=& \int_2^5 \frac{C}{x}dx + \int_{7}^{10} \frac{C}{x} dx\\
& =& \frac{\log(5/2) + \log(10/7)}{\log(5)}\\
&\approx& 0.791
\end{eqnarray}
$$


#### 2. Question 2 from Grinstead and Snell, Section 4.2
A radioactive material emits $\alpha-$ particles at a rate described by the density function
$$
f(t) = 0.1\exp[-0.1t].
$$
Find the probability that a particle is emitted in the first 10 seconds, given that:
#####1. no particle is emitted in the first second.

First, note that the cumulative distribution function for this density is given by

$$
F(t) = 1 - \text{exp}(-0.1t)
$$

Now, let $E_{t<10}$ denote the event that a particle is emitted in the first 10 seconds and let $E_{t>1}$ denote the event that no particle is emitted in the first second.   We are interested in the conditional probability $\mathbb{P}(E_{t<10} | E_{t>1})$.  From the product rule, we have

$$
\begin{eqnarray}
\mathbb{P}(E_{t<10} | E_{t>1}) &=& \frac{\mathbb{P}(E_{t<10},  E_{t>1})}{\mathbb{P}(E_{t>1})}\\
&=& \frac{F(10)-F(1)}{1.0-F(1)}\\
& = &\frac{\text{exp}(-0.1)-\text{exp}(-1.0)}{\text{exp}(-0.1)}\\
& \approx & 0.593
\end{eqnarray}
$$

##### 2. no particle is emitted in the first 5 seconds.

Similar to above,

$$
\begin{eqnarray}
\mathbb{P}(E_{t<10} | E_{t>5}) &=& \frac{\mathbb{P}(E_{t<10},  E_{t>5})}{\mathbb{P}(E_{t>5})}\\
&=& \frac{F(10)-F(5)}{1.0-F(5)}\\
& = &\frac{\text{exp}(-0.5)-\text{exp}(-1.0)}{\text{exp}(-0.5)}\\
& \approx & 0.393
\end{eqnarray}
$$

##### 3. a particle is emitted in the first 3 seconds.

The probability of a particle being emitted in the first ten seconds given that a particle is emitted in the first 3 seconds is just $1$.

##### 4. a particle is emitted in the first 20 seconds.

Using Bayes' rule, we have
$$
\begin{eqnarray}
\mathbb{P}(E_{t<10} | E_{t<20}) &=& \frac{\mathbb{P}(E_{t<20} | E_{t<10}) \mathbb{P}(E_{t<10})}{\mathbb{P}(E_{t<20})}\\
& = & \frac{\mathbb{P}(E_{t<10})}{\mathbb{P}(E_{t<20})}\\
& = & \frac{ F(10)}{F(20)} \\
& = & \frac{1.0 - \text{exp}(-1)}{1.0 - \text{exp}(-2)}\\
& \approx &0.731
\end{eqnarray}
$$

#### 3. Laplace and Birth Rates
In the 1700s, scientists observed that there seemed to be more male births than female births.  But what was the real ratio of male to female births?  In the late 1700s, Laplace used this question to help form his statistical theories, including his refinement of Bayes' rule.  From birth records in Paris between 1745–1770, Laplace had access to the following data:

| Gender | Live Births |
|--------|-------------|
| female | 241,945     |
| male   | 251,527     |

Let $\rho$ denote the probability that a newborn (in Laplace's time) is male.   Assume a [binomial likelihood](https://en.wikipedia.org/wiki/Binomial_distribution) function for the data in the table above with parameter $\rho$ and a uniform prior density.

##### 1. Write out the mathematical form of the prior and likelihood.

The prior density is uniform, which means that it is proportional to $1$ over the  sample space.  Here, the sample space is just the interval $\Omega_\rho = [0,1]$.  Thus, the prior density function is given by
$$
f(\rho) = \left\{\begin{array}{cc} 1 & \rho\in[0,1]\\ 0 & \text{otherwise} \end{array}\right.
$$

Let $f$ be the number of female births and $m$ the number of male births.  Since $\rho$ is the probability of a male birth, the binomial likelihood function is given by
$$
f(L| \rho) = \left(\begin{array}{c}m+f\\ m \end{array}\right)\rho^m (1-\rho)^f.
$$
This can also be written in terms of $n=f+m$ the total number of births
$$
f(L| \rho) = \left(\begin{array}{c}n\\ m \end{array}\right)\rho^m (1-\rho)^{(n-m)}.
$$


##### 2. Write out the form of the posterior density.   

Using Bayes' rule, we have
$$
\begin{eqnarray}
f(\rho | L) &=& \frac{f(L| \rho) f(\rho)}{\int_0^1 f(L| \rho) f(\rho) d\rho} \\
&=& C_1 \left(\begin{array}{c}n\\ m \end{array}\right) \rho^m (1-\rho)^{(n-m)},
\end{eqnarray}
$$
where the normalizing constant $C_1$ is given by
$$
\begin{eqnarray}
\frac{1}{C_1} &=& \left(\begin{array}{c}n\\ m \end{array}\right) \int_0^1  \rho^m (1-\rho)^{(n-m)} d\rho\\
\end{eqnarray}
$$

Note that

$$
\begin{eqnarray}
\left(\begin{array}{c}n\\ m \end{array}\right) &=& \frac{n!}{m!(n-m)!} \\
&=& \frac{\Gamma(n+1)}{\Gamma(m+1)\Gamma(n-m+1)}.
\end{eqnarray}
$$

Thus, the normalizing constant can be expressed as
$$
\begin{eqnarray}
\frac{1}{C_1} &=& \frac{\Gamma(n+1)}{\Gamma(m+1)\Gamma(n-m+1)}\int_0^1  \rho^m (1-\rho)^{(n-m)} d\rho\\
\end{eqnarray}
$$
The integral itself has a similar form in terms of Gamma functions, so we obtain
$$
\begin{eqnarray}
\frac{1}{C_1} &=& \left[\frac{\Gamma(n+1)}{\Gamma(m+1)\Gamma(n-m+1)}\right] \frac{\Gamma(m+1)\Gamma(n-m+1)}{\Gamma(n+2)}\\
&=& \frac{\Gamma(n+1)}{\Gamma(n+2)}\\
&=& \frac{n!}{(n+1)!}\\
\Rightarrow C_1 & = & n+1.
\end{eqnarray}
$$


##### 3. Can the prior and posterior be written in the same form?  *Hint:* Try to write them both as $C\rho^{a-1}(1-\rho)^{b-1}$ but with different parameters C, $a$, and $b$.

First, note that the uniform prior can be written in this form when $a=1$ and $b=1$, thus
$$
f(\rho) = \rho^{1-1}(1-\rho)^{1-1}.
$$

The posterior is given by
$$
f(\rho | m, f) = \frac{\Gamma(n+2)}{\Gamma(m+1)\Gamma(n-m+1)} \rho^{m}(1-\rho)^{(n-m)}
$$
The posterior given above clearly has the form specified in the question when $a^\ast = m+1$ and $b^\ast = n-m+1$.   In general, both the prior and posterior densities are specific cases of the general Beta family probability density function, which take the form
$$
f(x) = \frac{x^{a-1}(1-x)^{b-1}}{B(a,b)},
$$
where
$$
B(a,b) = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}.
$$

#### 4. Birth Rate Simulation
Complete the coding exercise in [BirthSimulation.ipynb](BirthSimulation.ipynb).  

##### Solution:
See the [solution repository](https://github.com/dartmouth-math76/continuous-probability-solution).

#### C1. Challenge Question 1: Uninformative Priors
*This question is ungraded.*

The uniform prior distribution is commonly used to model situations where we have a "lack of information" about a random variable.   However, a uniform distribution is not always an "uninformative" choice.

Consider two random variables $\theta \sim U[0,2\pi]$ and $\psi\sim U\left[-\frac{\pi}{2},\frac{\pi}{2} \right]$ used to describe the position (in spherical coordinates) on a unit sphere ($r=1$).   Do you think this uniform distribution is non-informative?   If not, can you derive a different density on $\theta$ and $\psi$ that produces a less informative prior?

**Hint:** Consider two patches $A$ and $B$ of equal area anywhere on the surface of the sphere.   Does the uniform distribution on $\theta$ and $\psi$ result in $P(A)=P(B)$ for any $A$ and $B$?

##### Solution:
For a direct solution to this problem, [check out this blog post](http://corysimon.github.io/articles/uniformdistn-on-sphere/).  While not exactly the same, this ide is related to the concept of the Jeffreys prior, which depends on the form of the likelihood function (but not the observations) and defines a prior that is invariant to changes in coordinates.
