## Part 1: Implementing a Voting Mechanism

### #1

Consider the following 'random dictatorship' voting mechanism over two alternatives a,b: each player submits one vote, vi in {a,b}, and the winning alternative w is uniformly rnadomly chosen from the votes submitted by all players. For instance, if there are n players, each of their votes will be chosen with a probability 1/n.

Consider the following.

- 1) Players have dominant strategies in this mechanism
- 2) There exists a Bayes Nash equilibrium to this mechanism

The mechanism will select from {a,b} with probability proportional to the votes, the players are all incentivized to select the candidate they like best. I believe that is a dominant strategy.

There should therefore be a BN equilibrium of eveybody choosing the candidate they like best, but there aren't the equilibria such as all voting a or all voting b that we saw with plurality voting.

True/True

## Part 2: Impossibility of General, Dominant-Strategy Implementations

### #2

Consider the following mechanisms, in which one is truthful reporting of preferences NOT a dominant strategy?

- Voting with Player 1 being a dictator. Players 2...N's votes don't matter, so none of their strategies are dominated.
- A buyer chooses between buying or not, when the price is fixed. Truthful reporting is dominant here.
- Voting under Borda rule. I think Borda is manipulable. Consider I like C>A>B but I think candidates A and B will be almost 50/50, with C getting almost no votes. I might like to report A>C>B instead so A receives more Borda score than B potentially.

## Part 3: Transferrable Utility

### #3

Here is a game with 2 players with types denoted (θ1, θ2), let the outcome be o = (x,p) = ((x1,x2),(p1,p2)) Consider the following 3 utility funcitons, which of them has private values.

- A) ui(θ,o) = (x1 + x2)θi pi

All the other options include θ2, which implies public values.

## Part 4: Mechanism Design as an Optimization Problem

### #4

consider a voting setting with 3 players (1,2,3) and 2 alternatives (1,b). Each player has a strict preference and prefers a or b with equal probability independently across players. Each player gets 5 if their top choice is selected and 0 otherwise.

Consider the following 2 voting rules with transferable utility: in both cases the player i in 1,2,3 submits one vote vi in a,b. 

- A) The winning alternative, w, is uniformly randomly chosen from the 3 votes submitted by the 3 players, and there is no transfer

- B) The winning alternative, w, is chosen under the same rule as in A. Players with vi = w pay 1 and players with vi != w get 1.

For example under B, if player 1 prefers a, votes a and w = v1 = a is selected to be the winning alternative, player 1 gets 5 because a wins, pays 1 because v1 = a, and thus gets a net payoff of 4.

Which voting rules are truthful (so that voting for a player's most preferred alternative is a dominant strategy)?

| other votes | i chooses a         | i chooses b             |
| ----------- | ------------------- | ----------------------- |
| a, a        | (1)4 = 4            | (2/3)6 + (1/3)-1 = 10/3 |
| a, b        | (2/3)4 + (1/3)1 = 3 | (1/3)6 + (2/3)-1 = 5/3  |
| b, a        | (2/3)4 + (1/3)1 = 3 | (1/3)6 + (2/3)-1 = 5/3  |
| b, b        | (1/3)4 + (2/3)1 = 2 | (1)-1 = -1              |

As we can see, if we are want a and we thing the other players also prefer a, we can vote b to get 6 util instead of 4 possibly, but the expected value of this is less than simply playing a because the mechanism could randomly select our vote for b.

- Both A and B are truthful mechanisms

### #5

As above, which voting rule(s) are efficient in terms of always choosing an outcome that maximizes the total sum of utilities?

Using the table I made for the previous problem, under truthful reporting and uniformly random types, the expected utility of playing under Mechanism B is (4+3+3+2)/4 = 3. Under Mechanism A with truthful reporting, we'd get this:

| other votes | i chooses a |
| ----------- | ----------- |
| a, a        | 5           |
| a, b        | 5           |
| b, a        | 5           |
| b, b        | 0           |

Mechanism A gives an expected utility of (5x3)/4, which is 3/4 larger than that from Mechanism B.

- Only A.

#### redo apparently this is wrong

I think neither voting rule is efficient. Neither.

### #6

As above, which voting rules are budget balanced?

- Only A. Because N = 3 is odd, the revenue is never 0, even if the expected value is 0 (which it isn't necessarily, I haven't calculated it yet).

### #7

As above, which voting rules are ex interim individually rational under truthful reporting?

Ex interim requires agents to never lose utility by participating in the mechanism. As seen from the tables made for the previous questions, truthful reporting never leads to negative payoff in either mechanism, so ex interim holds for both.


### #8

Which voitng rule earns a higher expected revenue for whoever runs the mechanism?

- The expected revenue of B is greater. Revenue of A is always 0, while B always has some payout > 0.

### #9

Which voting rule gives a higher maxmin fairness?

Maxmin fairness is the the util recieved by the agent who recieves the least util.

- Mechanism B has higher maxmin fairness (1 versus 0).


















