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

There is a problem here: in a bayes nash equilibrium problem, there could be more than one equilibrium. Which one should I expect agents to play? Agents could mis-coordinate and play none of the equilibria. We can require that the desired outcome arises in the only equilibrium, in every equilibrium, or in at least one equilibrium.

There are two forms of implementation: Direct and Indirect. Direct implementation implies agents each simultaneously sending a single message (their type) to the center. Indirect implies agents send a sequence of messages; information may be partially revealed about the messages that were previously sent.

## Mechanism Design: Examples

- N = {1,2,...,n} is a committee of voters
- O = {a,b,c} are candidates who could be elected

Remember theta_i describes the type of agent i. We could have a type theta_tilde_i with utility 3 for a, 2 for b, and 1 for c. The value of u(o,theta_i) depends only on theta_i. u(a,theta_tilde_i) = 3. In this example there are three theta_is with different hats. Instead of being verbose, I refer to them as tilde hat and bar. 

| Type  | a   | b   | c   | pref  | prob |
| ----- | --- | --- | --- | ----- | ---- |
| tilde | 3   | 2   | 1   | a>b>c | .49  |
| hat   | 2   | 3   | 1   | b>a>c | .49  |
| bar   | 2   | 1   | 3   | c>a>b | .02  |

Types are independent across agents. We have a common prior on the types of agents. .49 for tilde, .49 for hat, and .02 for bar.

What would a plurality voting mechanism look like here? Remember the mechanism is a pair (A,M).

- A = A1 ... An where Ai = {a,b,c}
- M maps the A to an outcome. In the case of plurality, the mechanism picks the candidate named by the most agents. If there is a tie it randomly selects one of the tied candidates.

How do we design our mechanism?

First note there are no dominant strategies. The optimal action depends on what you think the other agents will do (will you be breaking some tie? fundamental problem with plurality). 

There are many Bayes-Nash equilibrium for this, for instance if everyone votes for the same candidate, nobody can improve their utility by divering (assuming n>5 agents). Tilde and bar voting for a and hat voting for b is an equilibrium because c is best off voting for the candidate which gives them 2 utility when a vote for their favorite is not sensical (Duverger's Law).

Lets look at a direct mechanism for this. Direct mechanism means the action set is the type set of the agents, we are not asking the agents what canidate they want but rather what type they are, and we can infer what they want from the utility that type derives from each candidate.

One possible direct mechanism would translate each type to that type's most preferred candidate and then plurality voting takes place. M(tilde,hat,bar) = (a,b,c). This is a manipulable mechanism because bar type voters might want to self report as tilde type.

## Revelation Principle

Any social choice function that can be implemented at all by any mechanism can be implemented by a truthful, direct mechanism. 

- A mechanism is direct if the input to the mechanism from each agent is just one single input. A simulatenous move bayesian game.
- A direct mechanism is truthful if the equilibrium strategy for all agents is to be completely truthful, to simply reveal their type.

Surprisingly, every mechanism can be converted to one of these. The brief explanation is that we can take any indirect mecahnism and imbed it in a new direct mechanism. We ask for agent's types and then convert those into what that type of agent would have reported in the equilibrium of the indirect game. The players dont need to lie because the mechanism is doing that for them!

## Revelation Principle Examples

This example uses the same scenario from the mechanism design example. The indirect mechanism was the plurality vote mechanism. Instead of agents giving their type, they chose a candidate, so that was an indirect mechanism. The revelation principle tells us that for any equilibrium of that mechanism there exists an equivalent direct truthful mechanism with the same equilibrium.

Direct mechanism - voter states their type {tilde,hat,bar}. To match the equilibria in the indirect mechanism where everyone voted for the same candidate, we can make a mechanism where all types are mapped to votes for a or all votes for b or all votes for c. To match the Duvergets Law equilibrium in indirect mechanism where everyone voted a or b, we can translate all tilde and bar to votes for a and all hats to votes for b.

## Impossibility of General, Dominant-Strategy Implementation

Theorem (Gibbard-Satterthwaite):

Consider a social choice function C: Mapping linear orderings Ln to outcomes in O. Suppose that 

- there are at least three outcomes so that |O| >= 3, and
- C is onto; that is, for every o in O there is a preference profile [>] in Ln such that C([>]) = o. (for every outcome there is some set of votes that would produce that outcome ie no outcomes are impossible to achieve. This is easy, for instance if every voter chooses preference  j, the outcome should be j. Now every outcome j is achievable.)

- Truthful reporting of preferences is a dominant strategy for each agent iff C is dictatorial: there exists some agent i for whom 

<a href="https://www.codecogs.com/eqnedit.php?latex=C([\succ])&space;=&space;\textrm{argmax}_O\succ_i&space;\forall&space;[\succ]\in&space;L^n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?C([\succ])&space;=&space;\textrm{argmax}_O\succ_i&space;\forall&space;[\succ]\in&space;L^n" title="C([\succ]) = \textrm{argmax}_O\succ_i \forall [\succ]\in L^n" /></a>

ie there is a some agent for whome the choice function maximizes their preferences.

In practice we can circumvent the Gibbard-Satterthwaite theorem in various ways:
 
- Use a weaker form of implementation. The result holds for dominant strategy implementation only, does not apply to Bayes-Nash implementation.

- Relax the asusmption that people are allowed to have arbitrary total orderings, limit the size of the action space. One example we've already seen is single-peaked voting.

- Trade. Have a fixed price in advance for an indivisible good, the only actions are yes or no.

## Transferable Utility




















