@def title = "Brainteasers"
@def date = Dates.today()

# Brainteasers problems preview

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
