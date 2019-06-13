## #1

Find the strictly dominate strategies

|     | x   | y   | z   |
| --- | --- | --- | --- |
| a   | 2,5 | 2,1 | 0,1 |
| b   | 3,2 | 4,4 | 1,1 |
| c   | 1,0 | 1,1 | 1,2 |

- stricly dominate requires a strict greater than
- player 1 has no strictly dominate strategies
- player 2 has no strictly dominate strategies

## #2

Find the weakly dominated strategies

- b weakly dominates c and stricly dominates a

## #3

Which strategies survive the process of iterative removal of stricly dominated strategies?

- a is stricly dominated by b so it is removed

|     | x   | y   | z   |
| --- | --- | --- | --- |
| b   | 3,2 | 4,4 | 1,1 |
| c   | 1,0 | 1,1 | 1,2 |

- y strictly dominates x

|     | y   | z   |
| --- | --- | --- |
| b   | 4,4 | 1,1 |
| c   | 1,1 | 1,2 |

- b,c,y,and z survive

## #4

Find all strategy profiles that form pure strategy Nash equilibria.

We removed strictly dominated strategies in the previous question, leaving us with

|     | y   | z   |
| --- | --- | --- |
| b   | 4,4 | 1,1 |
| c   | 1,1 | 1,2 |

There are only 4 strategy profiles to consider

- (b,y) is Nash
- (b,z) is not, player 2 would rather play y and player 1 would deviate to c
- (c,y) has the same problem as (b,z)
- (c,z) is Nash

## #5

What are the mixed strategy Nash equilibrium? Note this is a different matrix even though it is very similar.

|     | y   | z   |
| --- | --- | --- |
| b   | 4,4 | 1,1 |
| c   | 1,1 | 2,2 |

p corresponds to the probability of p1=b and (p-1) corresponds to p1=c

q corresponds to the probability of p2=y and (p-1) corresponds to p2=z

What is the expected utility of y? 4p + 1(1-p)

What is the expected utility of z? 1p + 2(1-p)

```
4p + 1(1-p) = 1p + 2(1-p)
4p + 1 -p = 1p + 2 - 2p
3p + 1 = 2 - p
4p + 1 = 2
4p = 1
p = 1/4
```

p=q=1/4 because the game is symmetric.

## #6

One island is occupied by Army 2, and there is a bridge connecting the island to the mainland through which Army 2 could retreat.

Stage 1: Army 2 could choose to burn the bridge at the very beginning.

Stage 2: Army 1 then could choose to attack the island or not.

Stage 3: Army 2 could then choose to fight or retreat. They cannot retreat if they burned the bridge.

- (2=Burn,1=Attack,2=Fight) -> (-2,-2)
- (2=Burn,1=Not) -> (0,5)
- (2=NotBurn,1=Attach,2=Retreat) -> (5,0)
- (2=NotBurn,1=Attack,2=Fight) -> (-2,-2)
- (2=NotBurn,1=Not) -> (0,5)

First consider blue subgame (where player 2 did not burn the bridge), what is a subgame perfect equilibrium?

|        | Retreat | Fight |
| ------ | ------- | ----- |
| Attack | 5,0     | -2,-2 |
| Not    | 0,5     | 0,5   |

Nobody has any reason to deviate from (Not,Fight). If 1 deviates to Attack they go from 0 to -2 utility. If 2 deviates to retreat, they go from 0 to 0 utility.

### redo, apparently this is wrong

Attack, Retreat is also a nash equilibrium, and importantly it is subgame perfect while Not,Fight is not.

## #7 

What is a subgame perfect equilibrium of the whole game?

This must of course include (1=Not,2=Fight) as that was the only subgame equilibrium, so the choice is between (2=Burn,1=Not,2=Fight) and (2=NotBurn,1=Not,2=Fight). 2 has no reason to not burn the bridge?

Bridge is burned, 1 does not attack.

## #8

Consider an infinitely repeated game where the game in each perioid depicted in the picture.

|             | Trust | Dist |
| ----------- | ----- | ---- |
| Not, Steal  | 2,2   | 2,2  |
| Not, Share  | 2,2   | 2,2  |
| Play, Steal | 8,3   | 1,3  |
| Play, Share | 6,6   | 1,3  |

There is a probability p that the game continues next period and 1-p that it ends. What is the threshold p* such that when p>=p* (Play,Share,Trust) is sustainable as a subgame perfect equilibrium by a grim trigger strategy? The trigger is p1 playing Not and player 2 playing Dist forever after a deviation from (Play,Share,Trust).

- Cooperating Forever yields 6 + 6p + 6p^2 + 6p^3 ... = 6 * 1/(1-p) = 6/(1-p)
- P1 Defecing yields 8 + 2p + 2p^2 + 2p^3 ... = 8 + 2p * 1/(1-p) = 8 + 2p/(1-p)
- Cooperate - Defect is -2 + 4p + 4p^2 + 4p^3 ... = -2 + 4p * 1/(1-p) = -2 + 4p/(1-p)

```
-2+4p/(1-p) >= 0
4p/(1-p) >= 2
4p >= 2(1-p)
2p >= (1-p)
2p >= 1-p
3p >= 1
p >= 1/3
```

## #9

There are two players. Player 2 is either a friend (probability p) or foe (probability 1-p), she knows and player 1 does not (bayesian game). 

The payoffs are as follows:

| Friend | Left | Right |
| ------ | ---- | ----- |
| Left   | 3,1  | 0,0   |
| Right  | 2,1  | 1,0   |

| Foe    | Left | Right |
| ------ | ---- | ----- |
| Left   | 3,0  | 0,1   |
| Right  | 2,0  | 1,1   |

Note that Player 1's payoffs are not dependant on Player 2's type

If p = 1/4, what is a pure strategy Bayesian equilibrium?

Player 2 will always play Left when a friend and Right when a foe (dominating strategies).

If P1 plays Left, he gets (1/4)3 + (3/4)0 = 3/4 utility.

If P1 plays right he gets (1/4)2 + (3/4)1 = 1/2 + 3/4 = 3/2 utility.

Therefore the pure strategy equliibrium is (P1=Right,P2Friend=Left,P2Foe=Right).

## #10

Player 1 is a company choosing whether to enter a market or stay out. If they stay out the payoff vector is (0,3).

Player 2 is already in the markey and chooses simultaneously whether to fight play 1 if they join. The payoffs depend on whether P2 is aggresive (p) or normal (1-p).

| Aggresive | Fight | Not  |
| --------- | ----- | ---- |
| Enter     | -1,2  | 1,-2 |
| Out       | 0,3   | 0,3  |

| Normal    | Fight | Not  |
| --------- | ----- | ---- |
| Enter     | -1,0  | 1,2  |
| Out       | 0,3   | 0,3  |

What is true?

- When p=1/2, it is an equilibrium for 1 to stay out, 2 to fight when aggresive and not when normal.
- When p>1/2, it is an equilibrium for 1 to stay out, 2 to fight when aggresive and not when normal.
- When p=1/2, it is an equilibrium for 1 to enter, 2 to fight when aggresive and not when normal.
- When p<1/2, it is an equilibrium for 1 to enter, 2 to fight when aggresive and not when normal.


Let us consider 2's payoffs. If 2 is aggresive, it should always fight and if it is normal it should always not.

Let us consider 1's payoffs given what we learned about 2. 1's payoff when playing Enter is -1p + 1(1-p) = -1p + 1 - p = 1-2p. Their payout is worse if p is higher. If p is less than 1/2, they make a profit entering, if it is greater, they lose utility. Therefore all the options are true.












