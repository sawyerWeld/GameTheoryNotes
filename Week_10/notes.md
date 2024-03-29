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


















