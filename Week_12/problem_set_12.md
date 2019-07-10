# Problem Set 13

### #1

Which of the three following auctions, First-Price, Japanese, Second-Price, have dominant strategies in the case of private values?

- Japanese and Second-Price. Truth-telling is a dominant strategy in both.

### #2

The second-price auction with private values is a special case of what?

- Vickrey-Clarke-Groves Mechanism

### #3

Consider a first-price auction with 3 bidders with private valuations independantly drawn from uniform distributions in [0,1]. Suppose they bid according to the symmetric Bayes-Nash equilibrium, and have realized valuations of 0.2, 0.5, 0.9 respectively. Who wins and how much does he pay?

- The bayes-nash equilibrium in first price auctions is to bid (n-1)/(n) proportion of your valuation. (2/3)x(0.9) = 0.6

### #4

Of the following auctions, which leads to the greatest expected revenue in the case of independant private values? Options are Dutch, first price, Japanese, and second price.

- By the equivalence theorem, they should all be the same (?) todo

### #5

Suppose you're planning to bid in a second-price auction with private values and have a valuation of 10 for the good. Because the second-price-auction is a dominant strategy, you plan to bid 10. When you arrive, the auctioneer has added a reserve price of 5. What should your new bid be?

- Still 10

### #6

True or false: The second price auction has a price of anarchy of 1.0 for the case of private values (i.e. it is always efficient in every Nash equilibrium).

- True. Every Nash equilibrium is playing truthfully. Truthful play gives the good to the agent who gets the most utility from it.

#### Not true

### #7

Suppose you had a single good to sell to a gingle agent with a private valuation which is drawn from an exponential distribution (cdf F(x) = 1-e^(-x), pdf f(x) = e^(-x)). The agent knows her value and you must post a price that can either she can either take or leave. This is a monopoly question that is equivalent to an optimal auction design (setting a reserve prive) with a single bidder. What price should you set to maximize your profit? 

- An agent's virtual valuation is calculated as r(v) = v - (1-F(v) / f(v))

```
v - ( 1 - F(v) / f(v) )
v - ( 1 - (1-e^(-v)) / (e^(-v)) )
:= v-1
```

- 1/2

#### Not 1/2

### #8

Consider the case of two risk-neutral bidders in an all-pay auction. If their private values are independently drawn from the uniform distribution [0,1]. How do they bid as a function of their values in a symmetric Bayes-Nash equilibrium?

- 0

#### Not 0

### #9 

Consider an optimal auction with two bidders A and B who have independent private values, but where A's valuation is drawn from uniform [0,1] while B's valuation is drawn from uniform [0,3]. If A's valuation realized is 0.8 and B's realized valuation is 1.6, who wins and what does she pay?

- B, 0.8

#### Not B, 0.8




