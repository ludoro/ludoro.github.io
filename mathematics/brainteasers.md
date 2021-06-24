@def title = "Brainteasers"
@def date = Dates.today()

# Brainteasers problems

## 1. Screwy pirates

5 pirates looted a chest full of 100 gold coins. The most senior pirate proposes a distribution of coins.
All pirates, including the most senior one, will vote. If at least 50% of pirates accept the proposal, the gold is divided. If not, the most senior pirate is fed to the shark and the process starts over.

**Solution**

To reason about this, let's start by simplying the problem: just one pirate. In this case, all 100 coins to him: not much to reason about.

In the case of $2$ pirates, the senior pirate proposes 100 coins to him as well: a tie still means that he wins.

Let's now go to $3$ pirates: A,B and C.
If the senior pirate gives just one coin to C, then this makes C vote for him.
If C has 0 coins, he will vote no alongside B to kill $A$. So the split in this case is:
A -> 99
B -> 0
C -> 1

Moving to $4$ pirates: reasoning similarly:
A -> 99
B -> 0
C -> 1
D -> 0

We start seeing a pattern:
A -> 99
B -> 0
C -> 1
D -> 0
E -> 1

## 2. Tiger and sheep

100 tigers and one sheep. Tigers can eat grass, but they'd rather eat sheep. If tiger eats the sheep, then he will become a sheep.
Will the sheep be eaten?

**Solution**

Again, start with 1 tiger. In this case, the tiger just eats the sheep.
With 2 tigers, no tiger will eat the sheep because he will get eaten.
With 3 tigers, the sheep will be eaten because then there is an even number of sheeps and no tiger will eat again.
By induction, we conclude that given $n=100$ is even, the first sheep will not be eaten.

## 3. Card game

Standard deck of $52$ cards. Turn two cards at each time. For each pair: if both black they go to the dealer pile, if both are red they go to your pile and if they are different they are discarded. You win if there are more red cards than black cards, you lose if it's a tie or more black cards.
How much do you pay to play the game?

**Solution**
You never play this game: it's always going to be a tie.


## 4. Burning ropes
Two ropes, each of which takes 1 hour to burn. Either rope is different so there is no consistency.

How do you use two ropes to measure 45 minutes?

**Solution**

Classic. You light the first rope on both end and the second rope on one end.
When the first rope burns out, you light out the second end of the second rope.
This will make the total time of $45$ minutes.

## 5. Defective ball

You have $12$ identical balls. One of the balls is heavier OR lighter than the
rest. Using a balance that only shows which side of the tray is heavier,
can you determine which ball is the defective one with $3$ measurements?

**Solution**
Split the balls into three groups: (1,2,3,4),(5,6,7,8) and (9,10,11,12). Compare the first two groups, they are either equal or lighter.
If heavier, just swap numbering so it becomes lower again.

Then use some balls from the group where we know that the ball are standard to draw conclusions.

## 6. Trailing zeros

How many trailing zeros are there in $100!$?

**Solution**

The number trailing zeros of a x is just the number of 5s matched with the number of 2s.
Take 100 as an example: $100 = 10*10 = 5*2*5*2$, two trailing zeros.
In the case of $100!$, the number of 5s in it is: $100/5 + 100/25 = 20 + 4 = 24$
The number of 2s is: $100/2 + 100/4 = 50 + 25 = 75$
So the max number of matches is $24$, thus we have $24$ leading zeros.

## 7, Infinite sequence
If $x^{x^{^\dots}} = 2$, what is x?

**Solution**

We notice this is equal to $x^2 = 2$ so $x=\sqrt{2}$

## 8. Last ball

A bag has 20 blue balls and 14 red balls. Each time you randomly take two balls out withouth replacement.

If both balls have same color, add a blue ball.
If they have a different color, add a red ball.

What will be the color of the last ball left in the bag?

Bonus: what happens in the case B=20 and R=13?

**Solution**

There are three cases:
- (B,R) -> (B-1,R)
- (B,R) -> (B+1,R-2)
- (B,R) -> (B-1,R)

For the case B=20 and R = 14, the last ball must be blue because it is not possible to have an odd number of red balls.
For the case B=20 and R = 13, similarly the final ball must be red because the number always stays odd.

## 9. Coin piles

$N=1000$ coins on the floor. $980$ tails and $20$ heads.
You are blindfolded. Can you separate the coins in two groups such that they
have an equal number of heads?

**Solution**

Group A has $n$ coin, while groub B has $1000-n$ coins.

Group A has m heads and n - m tails, while groupB has 20 - m heads.
Flip all coins in group A: m tails and n - m heads.
Setting $n - m = 20 - m$ gives $n=20$ for size of group $A$.

## 10. Counterfeit coins

10 bags with 100 identical coins. In all bags but one, each coin weighs 10 grams.
However, all coins in the counterfeit weigh either 9 or 11.
Can you find the counterfeit bag with only one weighing using a digital scale
that tells the exact weight?

**Solution**
Pick $i$ coins for each bag. In total we have $\sum_{i=1}^n i = 55$ coins.
If all of them weighted the same, we would have 550 as weight. However, the weight would be
$550 \pm i$

## 11. Coin split problem

$n$ coins. Split into two piles. Multiply and add to the total final.
Expression for the final value?

**Solution**

Example: n split into x and y. x split into $x_1,x_2$ and y split into $y_1,y_2$.
The final answer is: $x*y + x_1*x_2 + y_1*y_2$
In general, for a split of size $x$ and $n-x$:

$f(n) = f(x) + f(n-x) + x(n-x)$

## 12. Drunk passenger
A line of 100 airline passengers are waiting to board a plane. The first passenger in line
is drunk and picks a random seat. After that, a passenger either goes to his seat, or picks one randomly.

What's the probability that you end up in your seat?

**Solution**

With this setup, the secnd to last passenger has get his own seat or not, with probability $\frac{1}{2}$ given that there are two seats left.

## 13. Hopping rabbit

A rabbit is at the bottom of a staircase. The rabbit can only go up one or  two stairs at
the time.
How many different ways are there to ascend?

**Solution**

$f(n) = f(n-1) + f(n-2)$

## 14. 100 light bulbs

100 bulbs in a room are off. Person #1 touches every switch. Person #2 touches every even switch.
Person #3 touches every switch that is multiple of 3 and so on.
At the end of the process, will bulb number $64$ be on?

**Solution**

You touched bulb $64$ an odd number of times: 1,2,4,8,16,32. It was off at the beginning so it must be on now.

## 15. N people at a conference

There are $N$ at a convention. Everyone one of them goes randomly in a room.
What is the probability that at least one of them goes to the right room?

**Solution**

The probability that at least one of them goes to the right room is equal to 1 - the
probability that no one goes to the right room.
Then, we have: $1 - \frac{n-1}{n}*\frac{n-2}{n-1}*\dots = 1 - \frac{(n-1)!}{n!}$
