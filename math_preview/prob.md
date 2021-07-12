@def title = "Probability problems"
@def date = Dates.today()

# Probability problems preview



## 1. Unfair coin (trick: bayes)

There are two coins: one is fair and the other has two tails.
You pick a coin at random, what is the probability that the coin you picked is
the unfair one given that you got 5 tails in a row?

**Solution**

Straightforward application of Bayes rule. Let A be the event that the coin
is unfair:
$$ \mathbb{P}(A \vert 5 T) = \frac{\mathbb{P}(A ∩ 5T)}{\mathbb{P}(5T)} =
\frac{\frac{1}{2}\times 1}{\frac{1}{2}\times 1 + \frac{1}{2}\frac{1}{2^5}}
= \frac{32}{33} $$

## 2. Expected value of minimum of two random variables (trick: logic)
Let $X \sim Uniform(0,1)$ and $Y \sim Uniform(0,1)$, find $\mathbb{E}[min(X,Y)]$.
X and Y are independent.

**Solution**

Let $Z = min(X,Y)$. $F_Z(z) = \mathbb{P}(Z \leq z) = \mathbb{P}(min(X,Y) \leq z)$

Working with inclusion exclusion is boring, so:
$F_Z(z) = 1 - \mathbb{P}(min(X,Y)>z)$
The minimum of two independent random variables is greater than a value iff they are both greater than that value:
$F_Z(z) = 1 - \mathbb{P}(X > z)\times \mathbb{P}(Y > z)$.

Here, we could use the fact that: $\mathbb{P}(X>z) = 1 - \mathbb{P}(X \leq z) =
1 - F_Z(z) = 1 - \frac{z - 0}{1 - 0} = 1 - z$.
Instead, we can also leverage the fact that for a uniform random variable $\mathbb{P}(X > z) = 1 - z$ thanks to symmetry.
All in all, we find that: $F_Z(z) = 1 - (1-z)^2$. Taking the derivative, we have: $f_Z(z) = 2(1-z)$. Finally, we can calculate the expected value using the definition:
$$ \mathbb{E}[Z] = \int_0^1 z \times 2(1-z)dz = \frac{1}{3}$$

## 3. Biased coin (trick: central limit theorem)

A coin is flipped 1000 times, it shows 600 times head. Is it biased?

**Solution**

When the number of trials is large, like in this case, the first thing that comes to mind is to use the Central limit theorem: we can approximate the total number of heads as normally distributed, with parameters:
Supposing the coin is not biased, we have that:
$\mu = np = 1000*0.5=500$, $\sigma = np(1-p) = \sqrt{250} ≈ 16$.
At this point, we can check with the z-score: $(600 - 500)/16 = 6.25$ This is 6 standard deviations above the mean: we can safely say that the coin is biased.
