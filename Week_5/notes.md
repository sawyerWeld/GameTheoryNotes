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

The problem is to pick a mechanism that will cause rational agents to behave in a desired way.

Definition of implementation in dominant strategies: Given a Bayesian game setting, a mechanism is an implementation in dominant strategies of a social choice function C (over N and O) if for any vector of utility functions u, the game has an equilibrium in dominant strategies, and in any such equlibrium a* we have M(a*) = C(u).

Definition (Bayes-Nash implementation): Given a Bayesian game setting, a mechanism is an implementation in Bayes-Nash equilibrium of a social choice function C (over N and O) if there exists a Bayes-Nash equilibrium of the game of incomplete information such that for every theta in Ө and every action profile a in A that can arise given type profile theta in this equilibrium, we have that M(a) = C(u(.,theta)). 

What that means is that for every type of agent and for every action profile that can arise in this equilibrium, it is the case that the outcome defined by that action profile is a social choice function of the agents given their times.

There is a problem here: in a bayes nash equilibrium problem, there could be more than one equilibrium. Which one should I expect agents to play? Agents could mis-coordinate and play none of the equilibria.




