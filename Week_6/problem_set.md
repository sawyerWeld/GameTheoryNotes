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

The expected payout for player 2 is not altered by player one being strong or weak, they recieve -w in the case of (attack,attack) either way. 

What strategy profile is a bayesian nash equilibrium if p=0.5?

Option 1: If A1 is weak, they should not attack, if they are strong they should always attack, A2 should always attack. No deviation can improve payouts here, so it is nash.

## #2

Rock Paper Scissors

P1 is a normal player. P2 is a normal player (p) or a simple player who always plays paper (1-p). 

| P2=Normal | R    | P    | S    |
| --------- | ---- | ---- | ---- |
| R         | 0,0  | -1,1 | 1,-1 |
| P         | 1,-1 | 0,0  | -1,1 |
| S         | -1,1 | 1,-1 | 0,0  |

| P2=Simple | P    |
| --------- | ---- |
| R         | -1,1 |
| P         | 0,0  |
| S         | 1,-1 |

Suppose p=1/3, what are the pure strategy bayesian equilibria?

P1 must decide a strategy to always play, and P2 must chose a strategy to play in the 1/3 of time he is a normal player. P1 most likely should play S always because he has a (1-p) chance of getting 1 utility. This is a dominating strategy. P2 therefore should play what does well against P1's S, which is R. 

## #3

Same situation as above, but p=2/3. 

- Consider P1=R, P2(Normal)=P. 3/3 of the time the situation is (R,P)->(-1,1). P1 can improve by chosing S instead, this is not an equilibrium.

- Consider P1=P, P2(Normal)=S. 1/3 of the time the situation is (P,P)->(0,0). 2/3 of the time the situation is (P,S)->(-1,1). The expected utility is therefore (-2/3,2/3). P1 can improve by playing S instead to get an expected utility of 1/3. This is not an equilibrium.

- Consider P1=S, P2(Normal)=R. 1/3 of the time the situation is (S,P)->(1,-1). 2/3 of the time the situation is (S,R)->(-1,1). The expected utility is therefore (-1/3,1/3). P1  can improve by  playing P. This would lead to 1/3(0,0) + 2/3(1,-1). This is not an equilibrium.

## #4

An engineer has talent t={1,2}, private information known only to the engineer. The engineer must decide to apply to the company or found a startup. A company must decide if they should hire or not hire the engineer. If the engineer applies and is rejected, he will found a startup.

The engineer recieves t=talent utility from a startup and w=wage from the company.

The company recieves t-w from hiring the engineer and 0 from not.

| t=2     | Hire  | Not |
| ------- | ----- | --- |
| Startup | 2,0   | 2,0 |
| Apply   | w,2-w | 2,0 |

| t=1     | Hire  | Not |
| ------- | ----- | --- |
| Startup | 1,0   | 1,0 |
| Apply   | w,1-w | 1,0 |

Suppose w=2, which are nash equilibria? form = (engineer's strategy if t=2, if t=1, company strategy)

Here the engineer benefits from being hired if t=1 and is neutral if t=2. The company gets 0 if t=2 and -1 if t-1. In this case the company would benefit from not hiring, as they never gain anything from it and sometimes lose utility.

- (apply, apply, not). Yes
- (apply, apply, hire). Company would benefit from not hiring.
- (startup, apply, not). Yes
- (startup, apply, hire). Company would benefit from not hiring.

## #5

Same as above, but suppose w=1. 

The engineer would rather not apply for the job if his talent is t=2, because at the job he only recieves 1 now. The company recieves 1 utility from hiring when t=2 and 0 from hiring when t=1. Hiring is a strictly dominate strategy.


Given (startup,apply) the company does not benefit from hiring or not hiring, the utility of both is 0. 

- (apply, startup, hire). t=1 apply is dominated 
- (startup, apply, hire). yes
- (startup, apply, not). yes
- (apply, startup, not). t=1 apply is dominated

## #6

Battle of the Sexes but incomplete information.

Player 1 is the usual player (type 'meet') player 2 is variable. Player 2 knowns her type while player 1 does not.

'Meet' player is the same as the usual game, would like to meetup with their partner. Probability p. 

'Avoid' player is antisocial, would like to avoid their partner. Probability 1-p.

| P2=Meet | L   | P   |
| ------- | --- | --- |
| L       | 2,1 | 0,0 |
| P       | 0,1 | 1,0 |

| P2=Avoid | L   | P   |
| -------- | --- | --- |
| L        | 2,0 | 0,2 |
| P        | 0,1 | 1,0 |

Given p=1/2, which is a pure strategy bayesian equilibria? Form=(1's strat, 2's strat if 2=meet, 2's strat if 2=avoid).

- (L, L, P). 1/2(2,1) + 1/2(0,2) = (1,1.5) yes
- (P, P, L). 1/2(1,0) + 1/2(0,1) = (0.5,0.5) P2 should never play P if they are 'Meet' type.
- (L, P, P). 1/2(0,0) + 1/2(1,0) = (0.5,0) P2 should never play P if they are 'Meet' type.



















