# Introduction to Game Theory

## Nash Equilibrium
A set of actions from all players in which no agent can improve their utility by deviating from their selected action.
#### Prisoner's Delima

| | C | D |
| --- | --- | --- |
| C |-1,-1 | -4,0 |
| D | 0,-4 | **-3,-3** |
- If I am A I always want to Defect. Defecting when the other person doesn't means I get 0 instead of -1. Defecting when the other person defects means I get -3 instead of -4.

#### Sidewalk problem. 
- If two people are walking towards each other on the sidewalk which side should they walk on? If they both walk on their respective rights or lefts they pass by each other, if they chose different sides they bump into each other.

| | Left | Right |
|--|--|--|
| Left  | **1,1** | 0,0 |
| Right | 0,0 | **1,1** |

#### Battle of the sexes
- A couple is going to the movies. One would like to go to movie B, the other F.
- They'd both rather go to the movie the other person wants than go to a movie without their partner.

| | B | F |
|--|--|--|
| B  | **2,1** | 0,0 |
| F | 0,0 | **1,2** |

#### Matching Pennies
- Two people flip coins. If they land on the same side (coin1 = coin2) player 1 wins. If they land on opposite sides (coin1 != coin2) player 2 wins.

| | H | T |
|--|--|--|
| H | 1,-1 | -1,1 |
| T | -1,1 | 1,-1 |

- There is **no** pure strategy nash equilibrium
