## #1

Two armys would like to capture an island. Army 1 is either strong (probability p) or weak (probability 1-p). Army 2 is always week (probability 1).

If one army attacks and the other does not, the attacking army gets the island for free (payout of M). If two weak armys attack, neither gets the island and both lose value of their weak army (payout -w). If a strong and a weak army attack, the strong army gets the island but loses value of their strong army (M-s) and the weak army loses value from upkeep of their weak army (-w). In the cases where an army does not attack, they always recieve 0 utility, even if the other army takes the island.

M > w > s. The payout of getting the island is greater than the losses you recieve from fighting with either size army. The loses you face with a weak army are smaller than those with a weak army.

| A1=Weak, A2=Weak | Attack | Not |
| ---------------- | ------ | --- |
| Attack           | -w,-w  | M,0 |
| Not              | 0,M    | 0,0 |

| A1=Strong, A2=Weak | Attack | Not |
| ------------------ | ------ | --- |
| Attack             | M-s,-w | M,0 |
| Not                | 0,M    | 0,0 |

The expected payout for player 2 if player 1 attacks is 
