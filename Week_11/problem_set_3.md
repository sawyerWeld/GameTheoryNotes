## Part 1: VCG Variants

Suppose we wish to allocate an item to a set of 10 agents. For every integer v=1:10 exactly one agent values the item at $v. An outcome is thus to which agent the item is allocated. Consider the following mechanisms:

- X: The outcome and payments are decided by the VCG mechanism.

- Y: The outcome and payments are chosen by VCg, and then each agent recieves 1/10 of the total payments back so that the transfers balance.

- Z: Each agent pays a $2 fee, and then the outcome and payments are according to the VCG on top of those payments.


Work:

What will the payments be under X? No agent recieves payment except 10, because no others are pivotal. Agent 10 will recieve payment. If agent 10 does not participate, 9 utility is gained by other agents. If agent 10 does participate, all other agents recieve 0 utility. Therefore agent 10 has to pay 9 (recieves 1 utility).

What about under Y? Same as above, but each agent recieves 1/10 of the total payments back. Therefore agents 1-9 recieve 0.9 utility and agent 10 recieves 10.9 and pays 9 (1.9 total).

What about under Z? Same as X, but everyone pays $2. Agents 1-9 recieve -2 utility and agent 10 recieves 10 and pays 11 (-1).


### #1

For which mechanism is truth-telling a dominant strategy? 

There are two classes of agents to consider. Suppose I value the item at some amount less than 10. Deviating to any amount below 10 will have no effect under any mechanism. Deviating above 10 will let me recieve the item, but I have to pay 10 under VCG (10 is now the second highest bid). My valuation is less than 10, so this is not a profitable deviation. Suppose I value the item at 10. If I deviate to declare a valuation less than 10, I will go from recieving 1 utility to 0, an unprofitable deviation. If I declare anything above 10, I still recieve 1, not a profitable deviation. If I declare my value between 9 and 10, I also don't change the outcome. Therefore truth telling is a dominant strategy under VCG for this sitation. The same should be true if there is a buy-in cost of 2. 

If every agent recieves the total payout divided by 10 at the end, we must also consider the price-setting agent, agent 9. If agent 9 increases their valuation to something between 9 and 10, it will recieve somewhere between 0.9 and 1.0 utility instead of 0.9. This is a profitable deviation.

- X and Z only

### #2

Which of the mechanisms are 'Groves' mechanisms?

Review is necessary.

### #3

Which of the mechanisms are weakly budget balanced?

Under weak budget balance, the mechanism never takes a loss, but may make a profit or break even. 

Under X, the mechanism makes a profit of 9.

Under Y, the mechanism makes a profit of 0.

Under Z, the mechanism makes a profit of 29.

- All three.

### #4

Which of the mechanisms are ex post individual rational (presuming honest reporting)?

Ex post individual rational means no agent ever loses utility by participation in the mechanism under any circumstance.

- X and Y satisfy this. Everyone loses under Z.

### #5

Which mechanisms are budget balanced in this environment?

- Y is budget balanced under honest reporting.

## Part 2: Single-item VCG

Suppose we wish to use VCG mechanism to allocate a block of bandwidth to one of three companies: X, Y, and Z. X and Y are competitors in the same industry; Z is in a different industry not competing with X or Y. The payoffs of three possible allocations are:

| Agent | U(give to X) | U(give to Y) | U(give to Z) |
| ----- | ------------ | ------------ | ------------ |
| X     | 10           | -15          | 0            |
| Y     | -12          | 5            | 0            |
| Z     | 0            | 0            | 4            |














