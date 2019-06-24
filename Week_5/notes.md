## Mechanism Design

Instead of taking a game as given and trying to analyze it, we're trying to design the games. We might for instance want to create games that reduce bargaining or reduce energy or resources wasted playing the game. When is it that we can get socially efficient outcomes?

## Mechanism Design: Implementation

Extend the social choice setting to a new setting where agents can't be relied upon to disclose their preferences honestly.

Definition: Bayesian game setting

A Bayesian game setting is a tuple (N,O,Ө,p,u) where

- N is a finite set of n agents
- O is a set of outcomes
- Ө = Ө1x...xӨn is a set of possible joint bayesian type vectors
- p is a common prior probability distribution on Ө
- u = (u1,...,un) where ui: O x Ө -> Real is the utility function for each player i (given an outcome of the game and the type of each player, what is the utility each player plays?)

This is all the setting that we as mechanism designers don't get to modify. 

A mechanism (for Bayesian game) is a pair (A,M) where

- A = A1x...xAn where Ai is the set of actions available to agent i in N
- M: A -> Prod(O) maps each action profile to a distribution over outcomes

As mechanism designers we get to specify the action set for the agents and the mapping from actions to outcomes, we cant change the possible outcome space, agent's preferences, or type spaces.





