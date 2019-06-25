## Part 1: Implementing a Voting Mechanism

### #1

Consider the following 'random dictatorship' voting mechanism over two alternatives a,b: each player submits one vote, vi in {a,b}, and the winning alternative w is uniformly rnadomly chosen from the votes submitted by all players. For instance, if there are n players, each of their votes will be chosen with a probability 1/n.

Consider the following.

- 1) Players have dominant strategies in this mechanism
- 2) There exists a Bayes Nash equilibrium to this mechanism

The mechanism will select from {a,b} with probability proportional to the votes, the players are all incentivized to select the candidate they like best. I believe that is a dominant strategy.

There should therefore be a BN equilibrium of eveybody choosing the candidate they like best, but there aren't the equilibria such as all voting a or all voting b that we saw with plurality voting.

## Part 2: Impossibility of General, Dominant-Strategy Implementations

### #2

Consider the following mechanisms, in which one is truthful reporting of preferences NOT a dominant strategy?

- Voting with Player 1 being a dictator. Players 2...N's votes don't matter, so none of their strategies are dominated.
- A buyer chooses between buying or not, when the price is fixed. Truthful reporting is dominant here.
- Voting under Borda rule. I think Borda is manipulable. Consider I like C>A>B but I think candidates A and B will be almost 50/50, with C getting almost no votes. I might like to report A>C>B instead so A receives more Borda score than B potentially.

## Part 3: Transferrable Utility



















