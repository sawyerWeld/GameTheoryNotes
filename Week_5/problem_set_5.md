## #1 
r,r

## #2

r,r both

## #3

- CCC = 5 + 5B + 5B^2 ...  = 5/(1-B)
- DDD = 6 + 2B + 2B^2 ...  = 6 + 2B/(1-B)
- C-D = -1 + 3B + 3B^2 ... = -1 + 3B/(1-B)
- Sustainable iff -1 + 3B/(1-B) is nonnegative
- -1 + 3B/(1-B) >= 0
- 3B/(1-B) >= 1
- 3B >= 1-B
- 4B >= 1
- B >= 1/4 wrong

### redo

that was wrong because the payout post trigger is 3,not 2
- CCC = 5 + 5B + 5B^2 ...  = 5/(1-B)
- DDD = 6 + 3B + 3B^2 ...  = 6 + 3B/(1-B)
- C-D = -1 + 2B + 2B^2 ... = -1 + 2B/(1-B)
- Sustainable iff -1 + 2B/(1-B) is nonnegative
- -1 + 2B/(1-B) >= 0
- 2B/(1-B) >= 1
- 2B >= 1-B
- 3B >= 1
- B >= 1/3

## #4

R,R is obvs an equilibrium
L,L is a prisoner's dillema of the top 2x2 sector


## #5

R,R and L,L are both equilibria of the stage game, so playing them repeatedly is a subgame perfect Nash equilibrium

The grim strategy is also correct

## #6

a and b are not true because the only pure strategy nash equilibrium is {(NotPlay,Steal),(Distrust)}->(1,1).

## #7

If player1 starts with a revenge status, they will play D this round and C the next, no mater what player2 plays. Therefore, player2 should play D in round 1. 

## #8

If player1 is playing tit-for-tat and player2 always cooperates, the payoffs will be 4,4 forever.

If player 2 plays defect forever, player1 will alternate between C and D, thus the payoff for player 2 is 5,1,5,1,5,1...

## #9

- CCC = 4 + 4B + 4B^2 + 4B^3 ... = 4 1/(B-1)
- DDD = 5 + 1B + 5B^2 + 1B^3 ... = what?

This is an infinite sum alternating between 5 and 1. We say that this is equal to the infinite sum alternating between -3 and 3 with 2 added at each term, because this is easier to compute. 
Wolfram: Sum[(-1)^t 2 B^t + 3 B^t, {t, 0, Infinity}] = 

- (-B-5)/(B-1)(B+1)
- 4/(B - 1) - (-B - 5)/((B - 1) (B + 1)) = (5 B + 9)/((B - 1) (B + 1))
- (5 B + 9)/(B^2 - 1) has roots its only root at -9/5, so ive dont something wrong

### redo

The difference is easier than I had it. The difference is -1 + 3B - 1B^2 + 3B^3...= (-3 - B)/((-1 + B) (1 + B)). Only solution to this is -3??\
not 1/2

### redo 2

sum of (2+(-1)^n)B^n is (B+3)/(1-B^2) is still -3 so im guessing 1/3
it was 1/3





