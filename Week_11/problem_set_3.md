## Part 1: VCG Variants

Suppose we wish to allocate an item to a set of 10 agents. For every integer v=1:10 exactly one agent values the item at $v. An outcome is thus to which agent the item is allocated. Consider the following mechanisms:

- X: The outcome and payments are decided by the VCG mechanism.

- Y: The outcome and payments are chosen by VCg, and then each agent recieves 1/10 of the total payments back so that the transfers balance.

- Z: Each agent pays a $2 fee, and then the outcome and payments are according to the VCG on top of those payments.


Work:

What will the payments be under X? No agent recieves payment except 10, because no others are pivotal. Agent 10 will recieve payment. If agent 10 does not participate, 9 utility is gained by other agents. If agent 10 does participate, all other agents recieve 0 utility. Therefore agent 10 has to pay 9.

What about under Y? Same as above, but each agent recieves 1/10 of the total payments back. Therefore agents 1-9 recieve 0.9 utility and agent 10 recieves 9.9 and pays 9.

What about under Z? Same as X, but everyone pays $2. Agents 1-9 recieve -2 utility and agent 10 recieves 10 and pays 11 (-1).


### #1

For which mechanism is truth-telling a dominant strategy? 

If truth is a dominant strategy under X, it should be under Z as well. The utility recieved under X is the same as those under Z + 2. Truth may not be a dominant strategy under Y





