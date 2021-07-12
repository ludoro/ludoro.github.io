@def date = Dates.today()

# Statistics problems preview


## 1. Unbiased and consistent estimators (trick: study theory)

Give the definition of unbiased and consistent estimator. Give an example of an unbiased but not consistent estimar and an example of a biased but consistent estimator.

**Solution**

Unbiased: expected value is equal to the true value.
consistent: as sample size increases, sampling distribution becomes more centered to the mean.
Let $x_1,\dots,x_n \sim \mathcal{N}(\mu,\sigma^2)$

Unbiased but not consistent: $x_1$.

Biased but consistent: $S_n^2 = \frac{1}{n}\sum_{i=1}^n(x_i - \overline{x})$

## 2. Drawing normally
We have $X \sim \mathcal{N}(0,1)$. What is the expected number of draws until
we get a value greater or equal to two?

**Solution**

Let G be the event "sampled a value greater than two."
We know that:

$\mathcal{P}(X >= 2) = 1 - \mathcal{P}(X < 2) = 1 - \Phi(2)$

Then, as the draws are independent, this can be seen as a Geometric distribution with probability of success $p = 1 - \Phi(2)$, which happens after $\frac{1}{p}$ draws.


## 3. Picking between two dice games.

First game: you roll two dies at once and win the product of the rolls.
Second game: you roll one die and get the square of the dice.

Which game do you pick and why?

**Solution**

Let $X$ be the value of the dice rolled. First game has expected value:
$\mathbb{E}[X]*\mathbb{E}[X]$. The second game has expected value: $\mathbb{E}[X^2]$
We know that $Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 \geq 0$, so we prefer the second game.
