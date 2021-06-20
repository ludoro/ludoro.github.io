@def date = Dates.today()

# Statistics problems


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

## 4. Simulating standard normal distribution.
You are given a random Bernoulli generator.
How would you generate values from a standard normal distribution?

Follow up question: can you come up with another method in the case of a
Uniform random number generator?

**Solution**

Let's generate $N$ samples following Bernoulli(p). Then, thanks to the Central limit theorem,
we have that:
$ \frac{\sqrt{N} (\overline X_N - \mu)}{\sigma} \to \mathcal{N}(0,1) $
In this setting, $\mu = p$, $\sigma = \sqrt{p(1-p)}$ and $\overline X_N = \frac{x_1 + \dots + x_N}{N}$

Then, $\overline X_N \sim \mathcal{N}(p, \frac{p(1-p)}{N})$

To get a value normally distributed, we just take the Z-score value:
$z(\overline X_N) = \frac{\overline X_N - p}{\sqrt{\frac{p(1-p)}{N}}}$ which is
normally distributed.

Onto the follow up question.

Suppose $X \sim \mathcal{N}(0,1)$. Then, $Y = F_X(x)$ where $F$ is the cdf
of $X$ is uniformly distributed.
Then $X = F_X^{-1}(Y)$ is distributed as X and the sample can be calculated.
It might be expensive to calculate the inverse,
in the case of the normal distribution it can be approximated with the error function.

## 5. independent vs uncorrelated

$X$, $Y$ are two random variables. What does it mean for $X$ and $Y$ to be independent? Uncorrelated?
Give an example where $X$ and $Y$ are uncorrelated but not independent.

**Solution**

independent: $P(X,Y)=P(X)*P(Y)$
Uncorrelated: $Cov(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y] = 0$

The example is built using discrete stuff. Let $X$ take values 1,0,-1 with equal probabilities.
Let $Y=1$ if $X = 0$ and $Y=0$ otherwise. Clearly, X and Y are not independent.

Still:
$\mathbb{E}[X] = 0$ and $E[XY] = \frac{1}{3}(-1)(0) +
 \frac{1}{3}(0)(1) + \frac{1}{3}(1)(0) = 0$,
 so they are uncorrelated.

## 6. One extra coin toss

A and B are playing a game where A has $n+1$ coins and B has $n$ coins.
They each flip all the coins. What is the probability that A has more heads than B?

**Solution**

The answer is $\frac{1}{2}$. The first n of A "neutralize" all the B coins,
so just one coin is left.

## 7. Covariance of uniforms
Suppose we have $X \sim Unif(0,1)$ and $Y = X^2$. What is the covariance of X and Y?

**Solution**
$Cov(X,Y) = Cov(X,X^2) = \mathbb{E}[X*X^2] - \mathbb{E}[X]*\mathbb{E}[X^2] = 0$
The second term is $0$ because $\mathbb{E}[X] = 0$. The first term is $0$ because:
$ \int_{-1}^{+1} x^{3}*\frac{1}{1-(-1)}dx = 0$

## 8. Coin flips needed to detect bias

You have an unfair coin: $\mathbb{P}(H) = 0.6$ and $\mathbb{P}(T) = 0.4$.
How many coin flips are needed to detect that the coin is unfair?

**Solution**

There are two ways to go about this. They both rely on the Central limit theorem.

We know that $\sqrt{n} \frac{(\overline X_n - p)}{(\sqrt{p(1-p)})} \sim \mathcal{N}(0,1)$
Then, $\overline X_n \sim \mathcal{N}(p,p(1-p)/n)$
We can define the coin as unfair if the z-score for the empirical $X_n$ is above
say $2$:

$$ \frac{\overline X_n - p}{ \sqrt{\frac{p(1-p)}{n}} } > 2 $$
And we can just solve for $n$.

A second approach, is setting the lower bound of a 95% confidence interval to $0.5$:

$$ p - z \sqrt{\frac{p(1-p)}{n}} = 0.5 $$

And again solve for $n$.

## 9. Area of a circle

Say you pick the radius of a circle from a uniform distribution between 0 and 1.
What is the probability density of the area of the circle?

**Solution**

The density function of the radius $r$ is $f_R(r) = 1$ when $0 < r < 1$.
I want to find the cdf of the Area to describe the distribution:

$ F_A(a) = \mathbb{P}(A \leq a) = \mathbb{P}(\pi r^2 \leq a) =
\mathbb{P}(r \leq \sqrt{\frac{a}{\pi}}) = \int_{r=0}^{r=\sqrt{\frac{a}{\pi}}} dr = \sqrt{\frac{a}{\pi}}$

## 10. Serving wait time

Two servers: F and S. F is faster and S is slower.
Users are routed to a server randomly and wait time is exponentially distributed
with two different parameters. What is the pdf of a user waiting time?

**Solution**

It is just: $f(t) = p_1 * f_S(s) + p_2 * f_F(f)$.

## 11. Estimating $\pi$
How would you estimate $\pi$?

**Solution**

A classic. Suppose you have a square of size 1, with bottom left corner on the origin.
Draw $\frac{1}{4}$ of a circle inside it. Generate random values inside the circle, we have:

$$\frac{\text{number of points inside the circle}}{\text{total number of points}} = \frac{\frac{\pi R^2}{4}}{1} $$

From which we can get the $\pi$.

## 12. Uniform draws

Suppose you sample independently three values $X \sim Unif(0,1)$. What is the probability
that the first value will be larger than the sum of the other two?

**Solution**

Just need to solve:

$$P(X_1 > X_2 + X_3) = \int_0^1 \int_0^{x_1} \int_0^{x_2-x_1} dx_3 dx_2 dx_1 = 1/6$$

## 13. Max of two rolls

What is the expected value of the max of two dice rolls?

**Solution**
Let $X_1$ and $X_2$ be the values of the first and second roll respectively.
We are interested in finding the expected value of $Y = \max{(X_1,X_2)}$:

$ \mathbb{E}[Y] = \sum_{i=1}^6 i * \mathbb{P}(Y = i)$

There are three cases:
1. The max value is on the first roll
2. The max value is on the second roll
3. The two rolls are equal.

$\mathbb{P}(Y=i) = \mathbb{P}(X_1 = i, X_2 < i) + \mathbb{P}(X_2 = i, X_1 < i) + \mathbb{P}(X_1 = X_2 = i)$

Then:

$\mathbb{P}(Y=i) = 1/6*(i-1)/6 + 1/6*(i-1)/6 + \frac{1}{6}*\frac{1}{6}$

## 14. Increasing rolls
N-sided die. You keep rolling and sum values as long as the current roll is larger than the previous.

What is the expected value of the sum?

**Solution**

Let $\mathbb{E}[r]$ be the expectation of the sum given you first roll the value $r$.
Then, by definition:
$\mathbb{E}[r] = r + \frac{1}{n}\mathbb{E}[r] + \frac{1}{n}\mathbb{E}[r+1] +\dots + \frac{1}{n}\mathbb{E}[n]$
Given that $\mathbb{E}[n] = n$, it is possible to recursively solve it and find:
$\mathbb{E}[r] = n$ for every $r$.


## 15. Monotonically increasing

Assume you draw from Uniform (0,1) iid. Keep drawing as long as the sequence is
monotonically increasing. What is the expected length of draws?

**Solution**

Let $X_i = 1$ if draw $x_i$ is in the list.
To go up until $X_i$, we need: $x_1 < x_2 < \dots < x_i$, this happens with probability: $\frac{1}{i!}$
Then, we can write thanks to independence:
$ \mathbb{E}[X_1 + \dots] = 1 + \frac{1}{2!} + \frac{1}{3!} + \dots = e - 1$

## 16. Two fives

You are rolling  a fair six sided dice.
What is the expected number of rolls until you roll two consecutive 5s?

**Solution**
Let X be the event of getting two consecutive 5. Let Y be the event of getting a
five.
We can write:

$\mathbb{E}[X] = \frac{1}{6}(1 + \mathbb{E}[X\vert Y]) + \frac{5}{6}(1 + \mathbb{E}[X])$

Knowing that:
$\mathbb{E}[X\vert Y] = \frac{1}{6}(1 + 0) + \frac{5}{6}(1 +\mathbb{E}[X])$
We get the final answer: $\mathbb{E}[X] = 42$.

## 17. Uniform sum time

You keep sampling iid Uniform (0,1), until the sum exceeds $1$.
How many samples do you expect to take?

**Solution**

Let $N_t = \text{smalest t such that: } \sum_{i=1}^n U_i > t$.
We are interested generally in $m(t) = \mathbb{E}[N_t]$.
When sampling a value x, we can write the following recursive equation:
$ N_t = 1 + N_{t-x}$
Taking the expected value: $m(t) = 1 + \mathbb{E}[N_{t-x}] = 1 + \int_0^t m(t-x)dx$.

Solving, we find $m(t) = e^t$.

## 18. Connecting ends

100 noodles. At each step, select randomly two ends and tie them together.
What is the expected number of loops formed?

**Solution**


## 19. Noodles connection

Say you have $100$ noodles. At each step you pick randomly two ends and connect
them. What is the expected number of loops?

**Solution**

We can write the following recursive relation:

$\mathbb{E}[n] = \frac{n}{\binom{2n}{2}}*[1 + \mathbb{E}[n-1]] + (1 - \frac{n}{\binom{2n}{2}} )*(0 + E[n-1])$

Getting to:

$\mathbb{E}[n] = \frac{1}{2n-1} + \mathbb{E}[n-1]$

Observing trivially that $ \mathbb{E}[1] = 0$, it is possible to solve it.

## 20. Distinct draws

Say you have $n$ numbers $1 \dots n$ and you uniformly sample from this distribution with replacement $n$ times.

What is the expected number of distinct values you would draw?


**Solution**
Let $X_i = 1$ if draw $i$ is seen in $n$ draws.

We are interested in $\sum_{i=1}^n \mathbb{E}[X_i]$.

$\mathbb{E}[X_i] = (\frac{n-1}{n})^n*0 + (1-(\frac{n-1}{n})^n)*1$
So the final answer is just:

$\sum_{i=1}^n \mathbb{E}[X_i] = n*(1-(\frac{n-1}{n})^n)*1$

## Many tosses

Say you toss a coin $n$ times. With $n$ very large.
How many sequences of 5 heads followed by 5 tails do you expect to see?

**Solution**
$X_i = 1$ if $i$ is starting point of the sequence.

We want to find $\mathbb{E}[\sum_{i=1}^n X_i ] =  \sum_{i=1}^n\mathbb{E}[X_i]$

Where $\mathbb{E}[X_i] = (\frac{1}{2})^{10} * (n-10)$
