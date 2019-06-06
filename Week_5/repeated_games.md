## Repeated Games

Repeated games are games that are played repeatedly over time. The example given is as follows:
Members of OPEC sell lots of oil for cheap. If they all agreed to pump less oil they could drive up the price. But, if one member cheated a bit and produced more than agreed upon, that member would make more money. If enough people do this, the alliance falls apart and everyone makes less money. This is much like a repeated prisoner's dilemma.

## Utility in Infinitely Repeated Games

The game that is being played repeatedly is called the 'stage game.' Each player gets a sequence of payoffs which are their utilities from each play of the stage game. We can't use extensive form or a sum because the extensive form would be inifinite (there would be no leaf nodes) and we cant use the sum because it would be unbounded. There are two ways utility gets defined in repeated play:

Averate reward. The limit as the number of games approaces inifinity of the sum of payoff from the stage game divided by the number of plays of the stage game.

<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{j=1}^k{\frac{r_j}{k}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{j=1}^k{\frac{r_j}{k}}" title="\sum_{j=1}^k{\frac{r_j}{k}}" /></a>

This is a bit counterintuitive. Consider the situation of getting -1000000 utility for the first 100 plays and getting a payoff of 1 each play thereafter. The limit as k->inf is 1. We might want to say that payoffs in the now are more important that payoffs in the future, which we can do mathematically with a discount factor. This is familiar from Q-Learning. We can provide the second definitiion which is

<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{j=1}^\infty{\beta^jr_j}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{j=1}^\infty{\beta^jr_j}" title="\sum_{j=1}^\infty{\beta^jr_j}" /></a>

There are two interpretations of this:
- The agent cares more about their well being in the near term than in the far term
- The agent feels that there is a chance the game will not be played in the far term. The chance of the game being played at iteration j is the discount factor beta to the jth power.

## Stochastic Games

The main idea is as follows: What if we don't always repeat the same stage game.
Stochastic games are a generalization of repeated games where the game we play is not necessarily the same game. How we play the stage games determines probabilistically which stage game we play next. 

Defined by a tuple (Q,N,A,P,R)

- Q is finite set of states
- N is a finite set of players
- A = A1...An where Ai is a finite set of actions available to player i.
- P : QxAxQ->[0,1] is the transition probability function. P(q,a,qhat) is the probability of transitioning from state q to state qhat after joint action a.
- R = r1...rn where ri : QxA->Real is a real valued payoff function for player i given a state and an action.

Markov Decision Processes (MDP) are single-agent stochastic games.

## Learning in Repeated Games

Two examples of learning in repeated games: Fictitious Play and No-regret Learning. Learning in game theory is a rich subject so this is a brief overview.

### Ficticious Play

Each turn play a best response to the assessed strategy of the opponent. Observe the opponent's actual play and update beliefs accordingly. We have a model of other agents play, where our model is just the counts of what actions the other agents played.

- for every a in A, let w(a) be the number of times the opponent has played a.
- asses the opponent's strategy using those counts

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma(a)=\frac{w(a)}{\sum_{a'\in&space;A}w(a')}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma(a)=\frac{w(a)}{\sum_{a'\in&space;A}w(a')}" title="\sigma(a)=\frac{w(a)}{\sum_{a'\in A}w(a')}" /></a>

- play a best response the the assesed strategy

Example: Matching pennies. Player 1 would like to match pennies, player 2 would like to mismatch pennies. Let player 1's initial beliefs about player 2 be (1.5,2) meaning he thinks player 2 will play H 1.5/3.5 percent of the time and T 2/3.5 percent of the time and he would like to match player 2, he plays T. Let player 2's initial beliefs about player 1 be (2,1.5) meaning he will play H 2/3.5 percent of the time and  T 1.5/3.5 percent of the time. He plays T because he would like to mismatch. Player 1 wins round one. Player 1's beliefs are now (1.5,3) and player 2's beliefs are now (2,2.5). Player 1 plays T and player 2 plays H. Repeat...

Note: Pure strategies here don't converge, but over time you'll see that each player plays Heads  half the time and Tails half the time. This is also the mixed strategy nash equilibrium of the matching pennies game.

*Theorem*: If the empirical distribution of each player's strategies converges in ficticious play, then it converges to a Nash equilibrium.

*Theorem*: Each of the following are sufficient conditions fo the empirical frequencies of play to converge in ficticious play:
- The game is zero sum
- The game is solvable by iterated elimination of stricly dominated strategies
- The game is a potential game (we'll get to this later)
- The game is 2 x n and has generic payoffs

### No-regret learning

The regret an agent experiences at time t for not having played s is R_t(s) = a_t - a_t(s).
A learning rule exhibits no regret if for any pure strategy of the agent s it holds that Pr([lim ing R_t(s)] <= 0) = 1. This means that at the limit, agents play with on regret. As you go to the limit, the probability with which your regret converges to 0 is 1.

Example learning rule that exhibits no regret: Regret Matching.
At each time step each action is chosen with probability proportional to its regret. That is,

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_i^{t&plus;1}&space;=&space;\frac{R^t(s)}{\sum_{s\in&space;S_i}R^t(s')}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_i^{t&plus;1}&space;=&space;\frac{R^t(s)}{\sum_{s\in&space;S_i}R^t(s')}" title="\sigma_i^{t+1} = \frac{R^t(s)}{\sum_{s\in S_i}R^t(s')}" /></a>

where the left side of the equation is the probability that agent i plays pure strategy s at time t + 1.

At least in finite games, regret matching converges to a correlated equilibrium.

## Equilibria of Infinitely Repeated Games

What is a pure strategy in an infinitely repeated game? A choice of action at every decision point, but there are infinite decision points because we play infinitely many stage games.

Some famous example strategies for the cooperation game: 
- Tit-for-tat: Start out cooperating, if your opponent defects, defect in the next round and then go back to cooperating.
- Trigger: Start out cooperating. If your opponent defects, defect forever.

We will now prove this theorem.
*Theorem*: We can characterize a set of payoffs that are achievable under equilibrium without having to enumerate the equilibria.

Consider any n-player game G = (N,A,u) and any payoff vector r = r1...rn which encodes the average utility a player recieves following a strategy at the infinite.

Let vi = min max (s_-i, si)

i's minmax value is the amount of utility i an get when -i play a minmax strategy against him. Meaning -i is unconcerned with their own utility and would instead like to punish i to the furthest extent possible. Players -i play the strategies from their mixed strategy spaces such that the best response to those strategies by i is minimized.

*Definition*: A payoff profile r is enforceable if ri >= vi. Agents should make at least their minmax value.

*Definition*: A payoff profile r is feasible if there exist rational, non-negative values a_a such that for all i we can express ri as
<a href="https://www.codecogs.com/eqnedit.php?latex=r_i&space;=&space;\sum_{a\in&space;A}\alpha_\alpha&space;u_i(a)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?r_i&space;=&space;\sum_{a\in&space;A}\alpha_\alpha&space;u_i(a)" title="r_i = \sum_{a\in A}\alpha_\alpha u_i(a)" /></a>
  with  
<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{a\in&space;A}\alpha_\alpha&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{a\in&space;A}\alpha_\alpha&space;=&space;1" title="\sum_{a\in A}\alpha_\alpha = 1" /></a>

Enforceability gives a lower bound and feasability provides an upper bound.


| 2,0 | 0,0 |
| --- | --- |
| 0,0 | 0,2 |


|<span style="font-weight:normal">heading</span>|
|:---------------------------------------------:|
|              content is king                  |











