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














