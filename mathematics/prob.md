@def title = "Probability problems"
@def date = Dates.today()

# Probability problems



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


## 4. Triangle forming (trick: logic)

You have a stick of length $1$. You cut it uniformly at point X, Y.
What is the probability that the three parts form a triangle?

**Solution**

The key is to remember that three segments form a triangle if every segment is less than the sum of the other two.
It's clear to see that if the two points are on the same side of the middle
point $M = 0.5$, then it's not possible to form a triangle.
This happens with probability $\frac{1}{2}$. Now, say the two points are on
different sides, without losing generality $X < Y$.
In this case, Y cannot be too far off, otherwise the middle stick will be too big.
More precisely, if $Y > X + M$ then the point is too far off. This happens with
probability $\frac{1}{2}$.
I internalize this with the following reasoning. Imagine this setting:
if point X is uniform betweeen 0 and 0.5, the probability that Y uniform between 0 and 0.5
is less than X is indeed $\frac{1}{2}$, because It  is like asking $\mathbb{P}(Y < X)$.


## 5. Flip until two heads in a row.

Suppose you are given a coin. What is the expected number of flips needed to get
two heads in a row?

**Solution**

Suppose $\mathbb{P}(H) = p$ and $\mathbb{P}(T) = q$. Let $A$ be the number of
flips needed to get two heads in a row.

Then, we can write:

$$\mathbb{E}[A] = p\times(1 + \mathbb{E}[A\vert H]) + q\times(1 + \mathbb{E}[A\vert T])$$
This is because with probability $p$ we do one flip with head,
and then we need to add the expected number of flips until we get two heads
in a row given we just got head. Same reasoning for tail.

We know that: $\mathbb{E}[A\vert T] = \mathbb{E}[A]$. Moreover:
$\mathbb{E}[A\vert H] = p \times ( 1 + \mathbb{E}[A \vert HH]) + q \times (1 + \mathbb{E}[A\vert HT]) $
But: $\mathbb{E}[A \vert HH] = 0$ and $\mathbb{E}[A\vert HT] = \mathbb{E}[A]$.
Putting everything into equation (3) and solving for $\mathbb{E}[A]$, we get:
$\mathbb{E}[A] = 6$.

## 6. Fair odds from unfair coin
You are given an unfair coin. Create a fair game.

**Solution**

Flip the coin two times, the possible outcomes are: TT, HH, TH, HT.
Discard TT and HH and only consider HT and TH which have
the same probability due to independence.

## 7. Ant collision

Three ants sitting at corners of equilateral triangle. Each picks a random direction.
What is the probability that none of them collide? Genralize to $k$ polygon.

**Solution**

Simply, $\mathbb{P}("\text{no collision}") = (\frac{1}{2})^{3} + (\frac{1}{2})^{3}$
This translates to: all ants decide right or all ants decide left.
If the polygon has $k$ sizes, then it is just: $\mathbb{P}("\text{no collision}") = (\frac{1}{2})^{k} + (\frac{1}{2})^{k}$


## 8. Number of cards before an ace

How many cars would you expect to draw from a standard deck (52 cards) before
seeing the first ace?

**Solution**

We just need to ask ourself: how many cards on average are
there before the first ace? There are 4 aces in a deck. Suppose C is a group of
cards withouth the ace, possibly of length $0$, the deck can be represented as follows:
C A C A C A C.
On average, C contains 48/5 cards. So, the expected value of cards needed to draw an ace is:
48/5 + 1.

## 9. First to roll side k

Suppose A and B are playing a game. The first that rolls with a dice the number k, wins 100€.
How much should A pay to go first?


**Solution**

Suppose $A$ is going first.

$P(A) = \frac 1 6  + \frac 5 6 (1-P(B))$

However, the probability of B winning when in the situation where A went first and failed, is exactly equal to P(A).

So: $P(A) = \frac 1 6  + \frac 5 6 (1-P(A))$ and $P(A) = \frac{6}{11}$,
$P(B) = \frac {5}{11} $
Then, A should simply pay the difference in expected value of going first vs going second:
$ \frac{6}{11}*100 - \frac{5}{11}*100 \sim 9.1$

## 10. Flipping game
A, B playing a game. Toss coin until HH or TH shows up. HH shows up first, A wins.
TH shows up first, B wins.
What is the probability of $A$ winning?

**Solution**

If a T is flipped, A has no chance of winning: the first head that comes after the T makes player B win.
So, we win with probability $\frac{1}{4}$, that is if we flip HH immediately.

## 11. Maximum dice roll

A fair die is rolled $n$ times. What is the probability that the largest number rolled is $r$, for each $r \in [1,6]$?

**Solution**

Let $L_r$ be the event of all rolls less or equal to $r$.
Then, the probability that the largest number rolled is $r$ is:
$$ P(L_r) - P(L_{r-1}) = (\frac{r}{6})^n - (\frac{r-1}{6})^n $$

## 12. Increasing Dice Order
Say you roll three dices one by one. What is the probability that you obtain 3
numbers in a strictly increasing order?

**Solution**
To be strictly increasing, first they need to be different. This happens with probability:
$1 * \frac{5}{6} * \frac{4}{6} = \frac{5}{9}$.
Conditioned on the fact that they are different, there is $\frac{1}{3!}$ chance that they are increasing.
So, final probability asked is: $\frac{5}{9} * \frac{1}{3!} = \frac{5}{54} $.

## 13. First toss

A fair coin is tossed $n$ times. Given that there were $k$ heads in the $n$ tosses, what is the probability that the first toss was heads?

**Solution**
It is simply $\frac{k}{n}$ thanks to Bayesian thinking.
Let $A$ be the event that there were $k$ heads in $n$ tosses. Let $B$ the event that the first toss was heads.
We are looking for:
$$ P(B \vert A) = \frac{P(A\vert B)*P(B)}{P(A)} $$

We know that $P(B) = \frac{1}{2}$. Moreover, $P(A) = \frac{\binom{n}{k}}{2^n}$. On the numerator all the possible ways to choose k heads, and in the denominator all the possible way to choose n tosses.
Finally $P(A \vert B) = \frac{\binom{n-1}{k-1}}{2^{n-1}}$.


## 14. Unfair coin recursion

A biased coin has probability $p$ of landing head. It is tossed $n$ times.
Write a recurrence relation for the probability that the total number of heads
after $n$ tosses is even.

**Solution**

Let $P(n)$ be the probability of having an even number of heads after $n$ tosses.
Then:

$$ P(n) = p(1 - P(n-1)) + q(P(n-1))$$

## 15. Random testing

A new feature $X$ is out. $1000$ uses: either fan or not fan at random.
50 users out of 1000 do not like X. You sample 5 users. If they all like it, you ship.

What's the probability that all the 5 users like it?

**Solution**

You want the users you pick to like $X$, so do not want to draw from the "bad" 50 users:

$$ 950/1000 * 949/999 * 948/998 * 947/997 * 946/996 $$

## 16. User virality

An app has one user. With $p_0$ it will have 0 users, with $p_1$ it will have one user and with probability $p_2$ it will have two users.

What is the probability of the app touching 0 users?

**Solution**

It is a branching process, the required probability is: $e = p_0 + p_1*e + p_2*e^2$


## 17. Different dice rolls

You roll three dices and observe the sum of the three rolls. What is the
probability that the sum of the outcomes is $12$, given that the three rolls are different?


**Solution**

A = sum is 12. B = number of rolls is different.

$P(A\vert B) = \frac{P(A \cap B)}{P(B)} = \frac{3}{20}$

We have that: $P(B) = 1 * 5/6 * 4/6$. Moreover, there are three possible combinations
that sum to $12$ and have different values, taking into account their permutations we have:
$P(A\cap B) = \frac{3*3!}{6*5*4}$

## 18. First to pick

Two people are picking random numbers among a set of M odd numbers and N even numbers withouth replacement.
The first person who picks an even number wins.

What is the probability that the first person who picks win?

**Solution**

Recursive solution on $n$ and $m$:


$$ P(n,m) = \frac{n}{n+m} + \frac{m}{n+m}*(1 - P(n,m-1))$$


## 19. Card colors

50 cards. 5 different colors, 10 cards of each color with different numbers.

What is the probability that two cards you pick at random do not have the same color and also not have the same number?

**Solution**
The answer is: $1 * \frac{40}{49} * \frac{36}{40}$.

## 20. Back and forth

A, B playing a game. $P(H) = p$. The first who gets head wins. A starts.

Probability of A winning?

**Solution**

$P(A) = p + (1-p)(1 - P(A))$

Which gives $P(A) = \frac{1}{2-p}$.

## 21. More likely outcome

A fair coin is tossed twice, you have to decide wheter it is more likely that two heads
showed up given that: 1) at least one toss is head, 2) the second toss was head.

**Solution**

Let $A$ be the event "the first toss is head" and let $B$ be
the event "the second toss is head".

For case 1, we are looking at calculating:
$$ P(A \cap B \vert A \cup B) = \frac{P(A \cap B \cap (A \cup B))}{P(A \cup B)} = \frac{P(A\cap B)}{P(A) + P(B) - P(A \cap B)} = \frac{1/4}{3/4} = 1/3$$

For case 2, we are looking at calculating:

$$ P(A \cap B \vert B) = \frac{P(A\cap B)}{P(B)} = \frac{1/4}{1/2} = \frac{1}{2}$$

## 22. Dice Re-roll

You roll a 6-sided dice up to two times. You can choose to stop at the end of the first
roll if you wish. You will get a dollar amount equal to the final rolled amount.

How much are you willing to pay to play this game?

**Solution**


The expected value of the game G is:
$\mathbb{E}[G] = \frac{1}{2}*(5) + \frac{1}{2}*(3.5)$
With probability $\frac{1}{2}$ we stop because we got a value in the range
$4-5-6$: on average $5$. If not, then we re-roll and the average value is $3.5$.

## 23. Gender guess

You call a random person and ask if they have two children. The person says that they have two children and one of them is a boy (B).

What is the probability that the other child is also a boy?

**Solution**

G = Girl

The outcome space is: GG BB GB BG.
We know that one is a boy, so this becomes: BB GB BG. So the final answer is $\frac{1}{3}$.

## 24. Rain Probability
Three friends have told you that it's rainy. They lie with probability $\frac{1}{3}$.
The chance of raining is $\frac{1}{4}$

What is the probability that rains?

**Solution**

We are interested in finding:

$\mathbb{P}(R\vert YYY) = \frac{\mathbb{P}(YYY\vert R)*\mathbb{P}(R)}{\mathbb{P}(YYY)}$

We know that:

$\mathbb{P}(R) = \frac{1}{4}$ and $\mathbb{P}(YYY\vert R) = (\frac{2}{3})^3$

Also,

$\mathbb{P}(YYY) = \mathbb{P}(YYY\vert R)*\mathbb{P}(R) + \mathbb{P}(YYY\vert \overline R)*\mathbb{P}(\overline R) =
(\frac{2}{3})^3 * \frac{1}{4} + (\frac{1}{3})^3 * \frac{3}{4}$

## 25. Counting paths

Suppose you are in 3D space. From (0,0,0) to (3,3,3) how many paths are there if
you can only move up right and forward?

**Solution**

$9$ moves are required, 3 moves for each direction. $9!$ ways to order 9 moves, but we need to divide by $3!$ for each direction to avoid overcounting.
$\frac{9!}{3! 3! 3!}$

## 26. Amoeba survival

A single amoeba in the beginning. With equal probability:
1. dies
2. do nothing
3. split into two
4. split into three

What is the probability of exctintion?

$p = \frac{1}{4}(1 + p + p^2 + p^3)$

## 26. Subsequence chance

In a random sequence of H and T, what is the probability that HHT shows up before HTT?

**Solution**

We only care at the point where we find the first $H$. If we are at that point,
then with probability $1/2$ HHT show up first, because I only need the H.
With probability $1/4$ I get HTT because I need both Ts.

Then, given $p$ the probability of HHT showing up before HTT, we can write:
$ p + p/2 = 1$

## 27. Double draw

Deck of $100$ cards with values from $1$ to $100$. You draw two cards at random without replacement.
What is the probability that one card is exactly double the other?

**Solution**

There are $\binom{100}{2}$ to choose two cards from a deck of $100$. There are $50$ possible choices, and the order does not matter,
so in total we have:
$ \frac{50*2}{\binom{100}{2}}$

## 28. Consecutive sixes

You roll a dice three times. What is the probability of getting two sizes in a row?

**Solution**
We either have: X 6 6 or 6 6 X. The probability of that happening is:
$ 5/6*1/6*1/6 + 1/6*1/6*5/6$

## 29. Random Drawer

8 drawers. With probability 1/2, somebody put a letter in one of the drawers. With probability 1/2 somebody did not put any letter in the drawer. You open the first 7 drawer, and they are empty. What is the probability that 8th drawer has letter in it?

**Solution**

A = letter in 8th drawer

B = no letter in first seven drawers.

$P(A\vert B) = \frac{P(A \cap B)}{P(B)}$

Where $P(A\cap B) = \frac{1}{2}*\frac{1}{8}$
$P(B) = \frac{1}{2}*1 + \frac{1}{2}*\frac{1}{8}$


##  30. Random Triangle
You pick three points on the unit circle and form a triangle with them. What is the probability that
the triangle includes the center of the unit circle?

**Solution**
Very intutive explanation: pick two points A and B at random.
Draw lines from the points to other side passing through the center.
The third point can only be in one quarter to satisfy the question:
this happens with probability $\frac{1}{4}$

## 31. Dice divisibility

Ten fair dices. Randomly throw these dies at once. What is the probability that
the sum of all the top faces is divisible by 6?


**Solution**
Consider the sum of the first $9$ numbers.
If we want to add a 10th value, there is just one out of 6 values that makes
the total sum divisible by 6.
Hence, the probability is $\frac{1}{6}$.

## 32. Equal rolls

You roll a die $6n$ times. What is the probability that each side shows up $n$
times exactly?

**Solution**

For a $1$ showing up, it must appear $n$ times out of $6n$ possible rolls.
For a $2$ showing up, it must appeaer $n$ times out of $5n$ possible rolls.
And similarly for the remaining rolls.
In total, there $6^{6n}$ possible rolls one can get, so:

$\frac{\prod_{i=1}^6 \binom{i*n}{n}}{6^{6n}}$

In the numerator, the total number of ways of splitting each side such that every side has exactly $n$ rolls.
In the denominator, the total number of possible rolls: imagine for $n=1$, every number can be in every position of the rolled dice.


## 33. Drawing colors
R red bals, W white balls. You keep drawing balls out of the bag until the bag only contains balls of single color.
What is the probability that you run out of white balls first?

**Solution**
Imagine the draws a sequence. We only care about "red is last ball". Fix the color of the last ball at the beginning: it's red with probability $\frac{r}{r+w}$.

## 34. Chord intersection
Say you draw a circle and draw two random chords. What is the probability that they intersect?

**Solution**
Fix the first chord by setting (randomly) two points $A$ and $B$.
Let $x$ the probability that point C falls between A and B.
Then, the solution is:
$ 2 \int_0^1 x(1-x)dx = \frac{1}{3}$

Inside the integral, we have: C between A and B and D not between A and B. Times two because we could also use D instead of C.
