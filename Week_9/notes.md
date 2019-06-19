## Introduction to social choice

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








