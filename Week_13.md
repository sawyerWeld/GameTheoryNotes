## Final Exam for Course 2

### #1

Consider the following (true) preference orderings or 4 agents over 4 candidates:

```
Agent 1: A>B>C>D
Agent 2: B>C>D>A
Agent 3: C>B>D>A
Agent 4: D>C>A>B
```
Assume that agents 2,3, and 4 are truthful while agent 1 may or may not be truthful in reporting her preference ordering. Under Borda Rule, find the best response of agent 1 among the given strategy profiles. Ties are broken alphabetically.

Among the following three orderings, which one achieves the best outcome for agent 1?
```
Borda Counts before Agent 1 votes
					
                    A B C D
Agent 2: B>C>D>A    0 3 2 1
Agent 3: C>B>D>A    0 5 5 2
Agent 4: D>C>A>B    1 5 7 5

Case 1
Agent 1: B>A>D>C    3 8 7 6  => B wins

Case 2
Agent 1: C>D>A>B    2 5 10 7 => C wins

Case 3
Agent 1: A>B>C>D    4 7 8 5  => C Wins
```

Agent 1 has the power to make B or C win, so it should chose option 1 to make B win.

- B > A > D > C

### #2

Same situation as #1, but under pairwise elimination with ordering C,A,B,D.

```
Agent 1: A>B>C>D

Agent 2: B>C>D>A
Agent 3: C>B>D>A
Agent 4: D>C>A>B

Case 1
Agent 1: B>A>D>C    C beats A. C ties B, loses. B beats D. B wins.

Case 2
Agent 1: C>D>A>B    C beats A. C beats B. C beats D. C wins.

Case 3
Agent 1: A>B>C>D    C beats A. C ties B, loses. B beats D. B wins.
```

- Cases 1 and 3 both make B win, so they are chosen.

### #3

Consider the following social welfare function W. Given (strict) orderings of agents on the candidates, for the comparison between any two candidates, W returns the lexicographically lowest ordering among the n orderings. So if all agents agree in the comparison between two outcomes, then that will be the social ordering, and otherwise the candidate who comes alphabetically first will be preferred socially. 

For example, if some agents have preferences A > B > C and some others have preferences B > A > C, then W chooses A > B > C.

Specify whether this social welfare function, W, satisfies Pareto efficiency for every finite number of agents and three alternatives.

- PE is satisfied if when all agents agree on the ordering of two outcomes, the social welfare function should as well. This trivially satisfies PE.

### #4

As above, does W satisfy transitivity?

- Yes? What does it mean for a social welfare function to satisfy transitivity?

### #5

Consider an auction with 2 risk-neutral bidders whose private values are independent and drawn from a uniform distribution [0,1]. Which of the following auctions is an implementation in dominant strategies (so that truth is a dominant strategy)?

- Second-price auctions. Truth is not a dominant strategy in first-price auctions.

### #6

Consider voting with 3 players (1,2,3) and 2 alternatives (a,b). Each player has strict preference, and prefers a or b with equal probabilities. Each player gets 5 if her top choice is selected and 0 otherwise. 

Consider the following voting rules, where in both cases each player submits a vote v in {a,b}.

1. The winning alternative w is randomly chosen from the 3 votes submitted by 3 players, with each vote determining the winner with equal probability. Players who voted for the winner pay 1 and players who voted for the loser pay 0.

2. w is selected just as in rule 1. Players who voted for the winner pay 0 and players who voted for the loser pay -1.

For which of the voting rules is being truthful a dominant strategy? 

Given that agent 1 would like A to win, if she plays truthfully, the expected value is as follows:

| Votes    | Rule 1    | Rule 2    |
| -------- | --------- | --------- |
| {A, A}   | 5 - 1 = 4 | 5 - 0 = 5 |
| {A, B}   | 5 - 1 = 4 | 5 - 0 = 5 |
| {B, A}   | 5 - 1 = 4 | 5 - 0 = 5 |
| {B, B}   | 0 - 0 = 0 | 0 + 1 = 1 |

Under Rule 1, the expected value of truthfulness is 3. Under Rule 2 it is 4.

If instead agent 1 votes for B, playing not truthfully, the expected value is as follows:

| Votes    | Rule 1     | Rule 2    |
| -------- | ---------- | --------- |
| {A, A}   | 5 - 0 = 5  | 5 + 1 = 6 |
| {A, B}   | 0 - 1 = -1 | 0 + 0 = 0 |
| {B, A}   | 0 - 1 = -1 | 0 + 0 = 0 |
| {B, B}   | 0 - 1 = -1 | 0 + 0 = 0 |

Under Rule 1, playing truthfully is not a dominant strategy (if the votes are {A, A}, agent 1 benefits by lying.)

Under Rule 2, the same is true.

- Neither 1 nor 2.

### #7

As above, which voting rule is budget balanced?

There are 2 scenarios: the winner gets 2 votes or the winner gets 3 votes. Under Rule 1, the first scenario has a revenue of 2 - 0 = 2. Under the second, 3 - 0 = 3. Neither is budget balanced.

Under Rule 2, the first scenario has a revenue of 0 - 1 = -1 and the second has a revenue of 0 - 0 = 0. This is not budget balanced either, because of the first scenario.

- Neither is budget balanced.

### #8

As above, which voting rule has a higher expected revenue (presuming agents are truthful)?

- 1. Agents always pay more to the mechanism under Rule 1.

### #9

Alice currently has one serving of chocolate, which she values at $5, and Bob has one serving of ice cream, which he values at $7. Carol values the chocolate at $7, the ice cream at $10, and both together at $12.

Suppose we run VCG to determine whether some of Alice and Bob's desserts should be transferred to Carol. The following table illustrates the change in payoffs to each agent from transferring one or more desserts from whichever agent has it to Carol.

| Agent | None | choc | ice | choc & ice  |
| ----- | ---- | ---- | --- | ----------- |
| Alice | 0    | -5   | 0   | -5          |
| Bob   | 0    | 0    | -7  | -7          |
| Carol | 0    | 7    | 10  | 12          |

Which outcome will the VCG mechanism choose?

- The VCG mechanism chooses the outcome which maximizes sum utility. Transferring the ice cream to Carol results in a sum utility of 15.

### #10

Suppose that you are selling a single item to n bidders with private valuations drawn uniformly and independently from the range [1,2]. What is the optimal (revenue maximizing) reserve price? 



















