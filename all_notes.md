All the notes from all the weeks concatinated. Note that the early weeks have much worse notes than the later ones, when I realized I really needed to take notes.

# Introduction to Game Theory

## Nash Equilibrium
A set of actions from all players in which no agent can improve their utility by deviating from their selected action.
### Prisoner's Delima

| | C | D |
| --- | --- | --- |
| C |-1,-1 | -4,0 |
| D | 0,-4 | **-3,-3** |
- If I am A I always want to Defect. Defecting when the other person doesn't means I get 0 instead of -1. Defecting when the other person defects means I get -3 instead of -4.

### Sidewalk problem. 
- If two people are walking towards each other on the sidewalk which side should they walk on? If they both walk on their respective rights or lefts they pass by each other, if they chose different sides they bump into each other.

| | Left | Right |
|--|--|--|
| Left  | **1,1** | 0,0 |
| Right | 0,0 | **1,1** |

### Battle of the sexes
- A couple is going to the movies. One would like to go to movie B, the other F.
- They'd both rather go to the movie the other person wants than go to a movie without their partner.

| | B | F |
|--|--|--|
| B  | **2,1** | 0,0 |
| F | 0,0 | **1,2** |

### Matching Pennies
- Two people flip coins. If they land on the same side (coin1 = coin2) player 1 wins. If they land on opposite sides (coin1 != coin2) player 2 wins.

| | H | T |
|--|--|--|
| H | 1,-1 | -1,1 |
| T | -1,1 | 1,-1 |

- There is **no** pure strategy nash equilibrium

# Repeated Games

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

We can actually characterize a set of payoffs that are achievable under equilibrium without having to enumerate the equilibria.

Consider any n-player game G = (N,A,u) and any payoff vector r = r1...rn which encodes the average utility a player recieves following a strategy at the infinite.

Let vi = min max (s_-i, si)

i's minmax value is the amount of utility i an get when -i play a minmax strategy against him. Meaning -i is unconcerned with their own utility and would instead like to punish i to the furthest extent possible. Players -i play the strategies from their mixed strategy spaces such that the best response to those strategies by i is minimized.

*Definition*: A payoff profile r is enforceable if ri >= vi. Agents should make at least their minmax value.

*Definition*: A payoff profile r is feasible if there exist rational, non-negative values a_a such that for all i we can express ri as
<a href="https://www.codecogs.com/eqnedit.php?latex=r_i&space;=&space;\sum_{a\in&space;A}\alpha_\alpha&space;u_i(a)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?r_i&space;=&space;\sum_{a\in&space;A}\alpha_\alpha&space;u_i(a)" title="r_i = \sum_{a\in A}\alpha_\alpha u_i(a)" /></a>
  with  
<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{a\in&space;A}\alpha_\alpha&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{a\in&space;A}\alpha_\alpha&space;=&space;1" title="\sum_{a\in A}\alpha_\alpha = 1" /></a>

Enforceability gives a lower bound and feasability provides an upper bound.
Consider the follwing game:

|     |     |
| --- | --- |
| 2,0 | 0,0 |
| 0,0 | 0,2 |

The payoff vector (1,1) is enforceable because we can put a weight of .5 on the (0,2) and (2,0) cells. Each player's payoff is .5\*2 + 0\*0. The .5 weights are the alpha values in the above equations. The payoff vector (2,2) is unenforceable. For both players to recieve a payoff of 2, (0,2) and (2,0) both need a weight of one, which means the sum of weights is not equal to 1, the second equation is violated.

*Theorem*: Consider any n-player game G and payoff vector r1...rn.
- If r is the payoff in any Nash equilibrium of the infinitely repeated G with average rewards, then for each player i, ri is enforceable.
- If r is both feasible and enforceable, then r is the payoff in some Nash equilibrium of the infinitely repeated G with average rewards.

Basically, if youre getting as much as much as you could if everyone were punishing you as much as possible, and the reward vector is mathematically feasible, then that reward vector is the reward vector of some Nash equilibrium. This theorem doesn't tell us what that nash equilibrium is, only that it exists.


## Discounted Repeated Games

The future is uncertain, we are often motivated more by what we can get today than what we can get in the future. Additionally, we must think about if people will punish me if I misbehave today.

- Stage game (N,A,u)
- Discount factors: Beta_i,...,Beta_n, Beta_i in [0,1]
- Payoff from a play of actions a1,...,at
<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_t&space;\beta_i^tu_i(a^t)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_t&space;\beta_i^tu_i(a^t)" title="\sum_t \beta_i^tu_i(a^t)" /></a>

A strategy in a repeated game is a set of actions to take given a history of a given length.

Repetedly playing a Nash equilibrium of the stage game is always a subgame perfect equilibrium of the repeated game.

Say we would like to convince two players of the repeated prisoner's dillema to cooperate. 

|     | C   | D   |
| --- | --- | --- |
| C   | 3,3 | 0,5 |
| D   | 5,0 | 1,1 |

The players are playing the 'Grim Trigger' strategy, in which if their opponent ever defects, they will defect forever. What discount factor is necesssary to keep players from triggering this defection?

Notes: Let Beta = B here. Sum of a^n as n->inf = 1/(1-a).

Cooperate forever yields 3 + 3B + 3B^2 + 3B^3... = 3 * 1/(1-B) = 3/(1-B)

Defect immediately yields 5 + 1B + 1B^2 + 1B^3... = 5 + B/(1-B)

Cooperate - Defect = -2 + 2B + 2B^2 + 2B^3... = -2 + 2B/(1-B)

The difference is nonnegative if -2 + 2B/(1-B) >= 0. 

The difference is nonnegative if 2B/(1-B) >= 2. 

The difference is nonnegative if B >= 1/2.

If people care about tomorrow half as much as today, they are incentivized to cooperate!

If we increase the yield from defecting when your opponent cooperates from 5 to 10, people must care about tomorrow at least 7/9 as much as today, B >= 7/9.

## A Folk Theorem for Dicounted Repeated Games

- Consider a finite normal form game G = (N,A,u)
- Let a = (a1...an) be a Nash equilibrium of the stage game G
- If a' = (a'1...a'n) is such that ui(a') > ui(a) for all i, then there exists a discount factor B<1, such that if Bi>B for all i, then there exists a subgame perfect equilibrium of the infinite repetition of G that has a' played in every period on the equilibrium path.

What this means: take any game and find an equilibrium on it. find a payout vector that is better for all parties, and there is some B value that would sustain that as an infinitely repeated discounted game. In the case of the previous section, the game was the prisoner's dillema, the equilibrium was (D,D)->(1,1), and the better state was (C,C)->(3,3).

# Introduction to social choice

Sometimes vote aggregation is not so simple, as can be seen with the presedential election in which Ralph Nader caused the race between Al Gore and George Bush to go awry.

## Voting Schemes

- There are a set of outcomes or 'alternatives'
- agents have 'preferences' over them
- the goal of the 'social choice function' is a mapping from profiles of preferences to a particular outcome

We would like people to vote for what they like best, not change their vote because of the social choice function. US elections fail at this, if you would vote third party it is often best to alter your vote because third parties have no chance of winning.

Note: using > in place of /succ here

Linear orders: binary relations > that are total and transitive. Every pair of alternatives a,b has either a>b or b>a. This is a top ordering.

Non-strict preferences: binary relationship >= that are total and tranisitive. 

- Social choice function is a function that maps a set of preferences to a single alternative outcome.
- Social welfare function is a function that maps a set of preference to a ranking of alternatives.

- Plurality: pick the outcome which is most preferred by most people
- Cumulative voting: Distribute multiple votes to each agent
- Approval voting: vote yes or no to any outcomes you like
- Plurality with elimination: if someone has a majority of 1st place votes, they win. otherwise, the outcome with the fewest cotes is eliminated and the process repeated.
- Borda Rule: Last place gets 0 points, first place gets n-1, second n-2 etc. Count up how many points were assigned across all agents, rank descending.
- Successive elimination: In advance an ordering of alternatives is decided. Consider the ordering ABC... . The election A vs B is held, and then the winner goes to the election vs C, which then goes to the election vs D. 

Condorcet Consistency: If there is a candidate that is preferred to every other candidate by majority, that candidate should be chosen.

## Paradoxical Outcomes

Consider the following election 
```
499 agents: A>B>C
  3 agents: B>C>A
498 agents: C>B>A
```
The condorcet winner here is B, even though it only got 3/1000 of first place votes. Plurality voting would have A being the winner and C being second. Plurality with elmination would have C as the winner, lets look at why. In the first round B is eliminated because it has the fewest first place votes:
```
499 agents: A>C
  3 agents: C>A
498 agents: C>A
```
In total C beats A 501 to 499. Here we have two voting schemes that seem reasonable which give different votes and neither are condorcet consistent.

## Impossibility of Non-Paradoxical Social Welfare Functions

Pareto Effeciency (PE): W is pareto efficient if whenever all agents agree on the ordering of two outcomes, the social welfare function should also select that ordering.

Independance of Irrelevant Alternatives (IIA): W is IIA if the selected ordering between two outcomes depends only on the relative orderings they are given by the agents.

Dictatorship: W has a dictator if there is any single agent such that the social welfare function only uses that agent's preferences. Dictatorship satistfies both PE and IIA.

Arrow 1951: Any social welfare function over 3 or more outcomes that is PE and IIA must be dictatorial.

The next video proves Arrow's theorem. It is very good and recommended.

## Impossibility of Non-Paradoxical Social Welfare 2

Social choice functions have the same problems as social welfare functions. PE and IIA have to be redefined to the scope of a single winner election. IIA is replaced with monotonicity.

Monotonicity: An outcome o must remain the winner whenever it was already winning and the support for it is increased.

Muller-Satterthwaite 1977: Any social choice function that is weakly PE and monotonic is dictatorial.

## Single-Peaked Preferences

Sometime's votes preferences have nice properties. One example is when alternatives can be ordered left to right. In this special case agents have a most preferred candidate and the support for other alternatives fall off as you go left or right. If you graph how much they like the candidates on the y axis and the alternatives on the x axis, there will be a single peak at their most preferred candidate.

Median voting: With an odd number of voters in a single peaked environment, the median candidate is always the condorcet winner.


# Mechanism Design

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

Agents have quasilinear preferences with transferable utility in an n-player bayesian game when the set of outcomes is O = X x Rn(real numbers) for a set X, if the utility of an agent i given joint type θ can be written 

<a href="https://www.codecogs.com/eqnedit.php?latex=u_i(o,\theta)&space;=&space;u_i(x,\theta)&space;-&space;p_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?u_i(o,\theta)&space;=&space;u_i(x,\theta)&space;-&space;p_i" title="u_i(o,\theta) = u_i(x,\theta) - p_i" /></a>

where o = (x,p) is an element of O (an outcome) and ui : X x Θ -> R. 

What does this mean? Agents are playing a bayesian game, but the set of outputs now includes a set of transfers (for instance maybe we play a game, we recieve utility for how we played, and also i payed you some amount of money or other transferable utility). pi can be thought of as 'payment' i where a negative payment means the agent is gaining utility.

We can split the mechanism into a choice rule and a payment rule (or transfer rule). x in X is a 'nonmonetary' outcome and pi in Reals is a 'monetary' payment that agent i makes to the mechanism.

There are a couple of implications. ui(x,θ) is not influenced by the amount of money/wealth an agent has, and agents don't care how much others are made to pay (though they can care about how the choice affects others.)

A direct mecahnism in a quasilinear setting is a pair (x,p) specifying a basic outcome x(θ) and a profile of payments or transfers p(θ) = p1(θ),...,pn(θ). 

Preferences have private values, or satisfy conditional utility independence, if each agent i's utility function can be written as ui(o,θi), it does not depend on other agents' types.

An agent's type becomes their valuation function: i's value for choice x is vi(x) = ui(x,θi), the maximum amount i would be willing to pay to get x.

## Transferable Utility Example

A group of citizens are voting on if their city should undertake a project.

N = {1,...n,} is a set of citizens, n is odd

O = {0,1}: 0 = do nothing, 1 = undertake the project

θi is now a valuation function, the utilities for outcomes 0,1 are vi(0),vi(1). A person's type is represented by a vector expressing their valuations. vi = (0,4) means the agent gains 0 from the status quo and 4 from undertaking the project.

Example direct mechanism: agents announce either type (0,4) or type (0,-2) if the majority are (0,4) the project is accepted and no compensation is given, otherwise it is rejected and no compensation is given. This mechanism doesn't account for the fact that total utility is not maximized (type (0,4) gets twice as much util as (0,-2) loses) (not necesarrily a bad thing).

Consider this mechanism: if m = n/3 of agents announce type (0,4) then: the project is accepted, pi = (n-m / m) 2 if vi = (0,4) and pi = -2 if vi = (0,-2), otherwise the project is rejected and pi = 0 for all vi. In this mechanism, the people who are for the project get a stronger vote but we compensate the people negatively affected by the decision. This mechanism maximizes total utility, however truth may no longer be an equilibrium! If you are a (0,4), you may purposely misreport as (0,2) if you think the project will certainly pass, in which case you get the util from the project and you receive compensation.

## Mechanism Design as an Optimization Problem

We can understand mechanism design as the problem of finding the 'best' possible mechanism, given constraints about how it operates.

### Constraints

Definition: Truthfulness. A transferrable utility mechanism is truthful if it is direct and for all i, for all vi, agent i's equilibrium strategy is to adopt the strategy vhat_i = vi.

Definition: Efficiency. A transferrable utility mechanism is strictly Pareto efficient, or just 'efficient', if in equilibrium it selects a choice x such that 

<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;v&space;\forall&space;x^',&space;\sum_i&space;v_i(x)&space;\geq&space;\sum_i&space;v_i(x')" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;v&space;\forall&space;x^',&space;\sum_i&space;v_i(x)&space;\geq&space;\sum_i&space;v_i(x')" title="\forall v \forall x^', \sum_i v_i(x) \geq \sum_i v_i(x')" /></a>

In other words, an mechanism is efficient if it selects the choice that maximizes the sums of the agents' actual valuations disregarding the payments they have to make. This is different than the standard game theoretical notion of Pareto efficiency meaning not being Pareto dominated. This is also called 'economic efficiency' to differentiate it from computational efficiency. It is also called social-welfare maximization.

- Definition: Budget Balance. A transferrable utility mechanism is budget balanced when

<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;v,&space;\sum_i&space;p_i(s(v))&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;v,&space;\sum_i&space;p_i(s(v))&space;=&space;0" title="\forall v, \sum_i p_i(s(v)) = 0" /></a>

where s is the equilibrium strategy profile. In other words, regardless of the agent's types, the mecahnism collects and disburses the same amount of money to and from the agents. 

 - Relaxed version - weak budget balance:

<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;v,&space;\sum_i&space;p_i(s(v))&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;v,&space;\sum_i&space;p_i(s(v))&space;\geq&space;0" title="\forall v, \sum_i p_i(s(v)) \geq 0" /></a>

The mechanism never takes a loss, but it may make a profit.

- Ex ante: the mechanism bust break even only on expectation

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbb{E}_v&space;\sum_i&space;p_i(s(v))&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbb{E}_v&space;\sum_i&space;p_i(s(v))&space;=&space;0" title="\mathbb{E}_v \sum_i p_i(s(v)) = 0" /></a>

- Ex interim individual rationality: a mechanism is ex iterim individual rationality when 

<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;i&space;\forall&space;v_i,&space;\mathbb{E}_{v_{-i}|v_i}v_i(\chi(s_i(v_i),s_{-i}(v_{-i})))-p_i(s_i(v_i),s_{-i}(v_{-i}))&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;i&space;\forall&space;v_i,&space;\mathbb{E}_{v_{-i}|v_i}v_i(\chi(s_i(v_i),s_{-i}(v_{-i})))-p_i(s_i(v_i),s_{-i}(v_{-i}))&space;\geq&space;0" title="\forall i \forall v_i, \mathbb{E}_{v_{-i}|v_i}v_i(\chi(s_i(v_i),s_{-i}(v_{-i})))-p_i(s_i(v_i),s_{-i}(v_{-i})) \geq 0" /></a>

where s is the equilibrium strategy profile. No agent loses by participating in the mechanism. Agents don't get to choose if they participate, but we'd like to say that none of them would have not participated if they had the option on the grounds that they expect to lose utility. It is called ex interim because it holds for every posisble valuation for agent i, but averages over the possible valuations of the other agents. 

- Ex post individual rationality: a mechanism is ex post individual rational when

<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;i&space;\forall&space;v,&space;v_i(\chi(s(v))-p_i(s(v))&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;i&space;\forall&space;v,&space;v_i(\chi(s(v))-p_i(s(v))&space;\geq&space;0" title="\forall i \forall v, v_i(\chi(s(v))-p_i(s(v)) \geq 0" /></a>

This is for when you don't want to average over everybody's types, perhaps you don't have a good prior for people's types. This is a stronger condition that states that you never want to lose utility in any situation under the given mechanism.

- Tractability: a mechanism is tractible when for all vhat, x(vhat) and p(vhat) can be computed polynomial time. We have to be able to determine the outcomes and payments in a computationally feasible manner.

### Objective functions

The mechanism designer can choose among mechanisms that satisfy the desired constraints by adding an objective function such as revenue maximization.

- Revenue maximization: A mechanism is revenue maximizing when, among the set of functions x and p that satisfy the other constraints, the mechanism selects the x and p that maximize 

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbb{E}_\theta&space;\sum_ip_i(s(\theta))" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbb{E}_\theta&space;\sum_ip_i(s(\theta))" title="\mathbb{E}_\theta \sum_ip_i(s(\theta))" /></a>

where s(θ) denotes the agents' equilibrium strategy profile.

- Revenue minimization: Perhaps we intend to not make money, but budget balance may be an impossible constraint. We can set weak budget balance as a constraint with the following objective. A transferrable utility mechanism is revenue minimizing when, among the set of functions x and p that satisfy the constraints, the mechanism selects the x and p that minimize 

<a href="https://www.codecogs.com/eqnedit.php?latex=\textrm{max}_v&space;\sum_ip_i(s(\theta))" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\textrm{max}_v&space;\sum_ip_i(s(\theta))" title="\textrm{max}_v \sum_ip_i(s(\theta))" /></a>

where s(v) denotes the agents' equilibrium strategy profile. This minimizes the worst case instead of figuring with an expected value such as with revenue maximization.

### Fairness

Fairness is hard to define. Which is fairer?

- charge all agents $100 dollars and make a choice that everyone hates
- charge all agents $0 and make a choice that some agents hate and some like

One might naively say that fairness should be about making the utility gained by everyone equal, but the second option is clearly preferrable in this example. The first one is 'fair' because it is the same for eveyone, but doing something awful to everyone is a bad way to design a mechanism.

- Maxmin fairness: maximize the hapiness of the least-happy agent. Choose some x and p that maximize

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbb{E}_v&space;\left[&space;\textrm{min}_{i\in&space;N}&space;v_i(\chi(s(v)))&space;-&space;p_i(s(v))&space;\right]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbb{E}_v&space;\left[&space;\textrm{min}_{i\in&space;N}&space;v_i(\chi(s(v)))&space;-&space;p_i(s(v))&space;\right]" title="\mathbb{E}_v \left[ \textrm{min}_{i\in N} v_i(\chi(s(v))) - p_i(s(v)) \right]" /></a>

Sometimes efficiency is impossible, but we can try to get close. To minimize the worst-case ration between optimal social welfare and the social welfare achieved by the given mechanism, we use price-of-anarchy minimization.

- Price-of-anarchy minimization: a transferrable utility mechanism minimizes the price of anarchy when it minimizes

<a href="https://www.codecogs.com/eqnedit.php?latex=\textrm{max}_{v\in&space;V}&space;\frac{\textrm{max}_{x\in&space;X}&space;\sum_{i\in&space;N}&space;v_i(x)}{\sum_{i&space;\in&space;N}&space;v_i(\chi(s(v)))}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\textrm{max}_{v\in&space;V}&space;\frac{\textrm{max}_{x\in&space;X}&space;\sum_{i\in&space;N}&space;v_i(x)}{\sum_{i&space;\in&space;N}&space;v_i(\chi(s(v)))}" title="\textrm{max}_{v\in V} \frac{\textrm{max}_{x\in X} \sum_{i\in N} v_i(x)}{\sum_{i \in N} v_i(\chi(s(v)))}" /></a>

where s(v) denotes the agents' equilibrium strategy profile in the worst equilibrium of the mechanism, ie the equilibrium in which the denominator is the smallest.



















































