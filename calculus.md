# Calculus

Here are my notes from calculus. I hope these help!

(section-label)=
## Calc 1
---
### Limits
In order to understand calculus, you first have to understand the limit. A limit is a somewhat complex way to simply just describe
the behavior of a function. Say you have a function, $f(x) = \frac{(x-2)}{(x-2)}$. Intuitively, you see the same thing on the top 
and bottom of a fraction, so you would think this function is equal to 1. But that is not entirely true.

Try plugging in $x = 2$. What value does $f(x)$ have? When you plug in 2 for x, you end up with $f(x) = \frac{0}{0}$, which does not
exist. The graph would look something like this:

```{figure} limit1.png
:height: 250px
:name: figure-example
```

There's a hole when $x = 2$. So you couldn't give an actual answer if asked what the value at $x = 2$ is. But what if you were asked
what the value of the graph is as x *approaches* 2? As x gets infinitely close to 2, what is the value of f(x)? From the left, when x
is 1.9, 1.99, 1.999, 1.9999, etc, $f(x) = 1$. From the right, when x is 2.01, 2.001, 2.0001, 2.00001, etc, $f(x) = 1$. This is where
limits come in. The limit, as x approaches 2, is equal to 1.

This is written like this: $\lim_{x\to2} \frac{(x-2)}{(x-2)}$

In this example, the limit as we approached 2 from the left and right were both 1 and they matched. However, this will not always be 
the case. Consider a piecewise function.

```{figure} limit2.png
:height: 350px
:name: figure-example
```
In this example, let's assess the limit as x approaches 2. From the left, as x = 1.9, 1.99, 1.999, etc gets infinitely close to 2, f(x)
gets closer and closer to 1. $\lim_{x\to2^{-}} f(x) = 1$

As we approach from the right however, as x = 2.1, 2.01, 2.001, 2.0001, etc gets infinitely close to 2, f(x) continues to increase and
approaches $+\infty$. $\lim_{x\to2^{+}} f(x) = \infty$

Becasue the limits taken from the left and the right do not match, we conclude that the limit of f(x) as x approaches 2 **does not exist**.
$\lim_{x\to2} f(x) = DNE$

However, sometimes we will have to calculate a limit instead of just looking at a graph. To do this, there a properties of a limit you must know.
Basically, the limit works the same as any other function would, and has these properties:

$\lim_{x\to n} cf(x) = c * \lim_{x\to n} f(x)$

$\lim_{x\to n} (f(x) + g(x)) = \lim_{x\to n} f(x) + \lim_{x\to n} g(x)$

$\lim_{x\to n} \frac{f(x)}{g(x)} = \frac{\lim_{x\to n} f(x)}{\lim_{x\to n} g(x)}$

For some limits, calculating the limit is as simple as plugging in the x value. However, in some cases, plugging in the x value will result in
either some constant c divided by 0 $\frac{c}{0}$ or infinity divided by infinity $\frac{\infty}{\infty}$. In either of these cases, we have 
to do more to tell if the limit exists. However, we may be able to simplify f(x) first and fint the limit easier.

Here is an example:

$ \lim_{x\to2} \frac{x^{2}-4x-4}{x-2} $

The function f(x) can be simplified by factoring the numerator. The numerator factors into $(x-2)(x-2)$, and one of those terms can cancel with
one on the bottom, which means f(x) is essentially equal to $(x-2)$. From there, we can plug 2 in and get that $ \lim_{x\to2} \frac{x^{2}-4x-4}{x-2} = 0$

Remember, if the limit as x approaches c from the left and the limit as x approaches c from the right **match**, then the limit as x approaches 
c will exist. So in order to determine if a limit exists and calculate it if it does, we should find the limit when x is just a very very small
number away from c.

Here is an example:

$ \lim_{x\to4} \frac{x}{x-4} $

So we split it into its left and right limit and take each one seperately.

From the left, it would look like this: 
$ \lim_{x\to4^{-}} \frac{x}{x-4} $
$ = \frac{3.999...9}{3.999...9-4} $
$ = \frac{3.999...9}{-.000...01} $
$ = -\infty $

From the right, it would look like this: 
$ \lim_{x\to4^{+}} \frac{x}{x-4} $
$ = \frac{4.000...01}{4.000...01-4} $
$ = \frac{4.000...01}{.000...01} $
$ = \infty $

$-\infty \neq \infty$, so the limits do not match and the limit **does not exist**.

Sometimes, we want to find the limit as x approaches +/- $\infty$. Now you might think, "Okay, let's just plug inifinity in for x". But what is $\infty + 5$?
There are some things to know in order to make finding the limit as x approaches infinity much easier:

If f(x) is a polynomial divided by another polynomial, then solving for the limit as x approaches infinity is very easy. The first step is to locate the highest
power in each polynomial. If the numerator has a higher power than the denominator, the limit goes to $\infty$. If the denominator has a higher power than the
numerator, the limit goes to 0. If they powers are equal, than the limit goes to the ratio of their coefficients. Let's look at an example:

$ \lim_{x\to\infty} \frac{3x^{5}-4}{2x^{5}-4x^{3}-4x+5} $

In this example, the highest power in the numerator is **5** and the highest power in the denominator is also **5**. Because the powers match, we can find the
limit as x approaches infinity by taking the ratio of the coefficients of those terms. In this case, that ratio is $\frac{3}{2}$.

However, this trick only works if both the numerator and denominator are polynomials. Otherwise, you have to use these logic rules to evaluate the limit:

$$ \frac{c}{\infty} = 0 $$
$$ c^{\infty} = \infty $$
$$ \infty + c = \infty $$

Limits for trig functions work the same way, but have some very important properties you have to memorize:

$$ \lim_{x\to0} \frac{\sin{x}}{x} = 1 $$
$$ \lim_{x\to0} \frac{1-\cos{x}}{x} = 0 $$


### Tangent Lines



### Derivatives

### Chain Rule

### Implicit Differentiation

### Related Rates

### Local Linear Aproximation

### L'Hopital's Rule

### Function Analysis

(section-label)=
## Calc 2

(section-label)=
## Calc 3

(section-label)=
## Multivariate Calc
