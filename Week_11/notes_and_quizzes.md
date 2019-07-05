There isn't all that much to this unit. A brief explanation of what VCG is and the quizzes should suffice.

## What is VCG?

The Vickrey-Clarke-Groves (VCG) mechanism always chooses the action that produces the greatest sum utility among agents.

The payment given to an agent i is given by

<a href="https://www.codecogs.com/eqnedit.php?latex=p_i(\hat{v})&space;=&space;\mathrm{max}\sum_{j\not=i}\hat{v}_j(x)&space;-&space;\sum_{j\not=i}\hat{v}_j(x(\hat{v}))" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p_i(\hat{v})&space;=&space;\mathrm{max}\sum_{j\not=i}\hat{v}_j(x)&space;-&space;\sum_{j\not=i}\hat{v}_j(x(\hat{v}))" title="p_i(\hat{v}) = \mathrm{max}\sum_{j\not=i}\hat{v}_j(x) - \sum_{j\not=i}\hat{v}_j(x(\hat{v}))" /></a>

This is the difference between two parts. The first part

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{max}\sum_{j\not=i}\hat{v}_j(x)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{max}\sum_{j\not=i}\hat{v}_j(x)" title="\mathrm{max}\sum_{j\not=i}\hat{v}_j(x)" /></a>

is the utility all agents receive in sum if i is not part of the mechanism. The mechanism will choose the outcome that maximizes total utility.

The second part 

<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{j\not=i}\hat{v}_j(x(\hat{v}))" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{j\not=i}\hat{v}_j(x(\hat{v}))" title="\sum_{j\not=i}\hat{v}_j(x(\hat{v}))" /></a>

is the utility all agents except for i recieve if i is included in the mechanism.

A groves mechanism (as opposed to a VCG) is a larger class of mechanisms than a VCG. The first part of a groves mechanism can be any function of the utilities the other agents get.

## Unit 3.2 Quiz

Three agents run the VCG mechanism to decide whether or not to build an airport. Their reports are:

| Agent | U(Build) | U(Don't) |
| ----- | -------- | -------- |
| 1     | 0        | 60       |
| 2     | 45       | 15       |
| 3     | 45       | 5        |

### #1

What outcome will VCG choose given the above report?

- VCG will choose to build. U(Build) has a sum utility of 90, U(Don't) has 80. VCG chooses the option with highest sum utility.

### #2

What is agent 2's payment?

If agent 2 were not part of the mechanism, the other agents would recieve a sum of 65 from the mechanism. If agent i is included, the agents who are not i recieve 45. 

- 65 - 45 = 20

### #3 

What is agent 3's payment?

- 75 - 45 = 30

## Unit 3.3 Quiz

### #1

Suppose that edge AF is added to the example network with cost 5.01. What are the new payments for BE?

- 5.01 - 4 = -1.01

### #2

What are the payments for EF?

- 5.01 - 4 = -1.01

## Unit 3.6 Quiz

We have seen that VCG is efficient, weakly budget balanced, and interim individually rational, under certain conditions. In a lecture, we saw an example of valuation distributions for which no mechanism for a simple exchange can be all of efficient, weakly budget balanced, and interim individually rational.

Consider running VCG for this simple exchange setting; the buyer has value 1 for the item, and the seller has value 0.9 for the good. The utilities are therefore:

| Agent  | U(trade) | U(don't) |
| ------ | -------- | -------- |
| Buyer  | 1        | 0        |
| Seller | 0        | 0.9      |

### #1

How much does the buyer pay to the VCG mechanism given the above values?

If the buyer is not in the mechanism, the agents gets 0.9 utility. If the buyer is in the mechanism, agents who are not the buyer get 0 utility. 

- 0.9 - 0 = 0.9

### #2

How much does the VCG mechanism pay to the seller given the above values?

If the seller is not in the mechanism, the buyer recieves 0 utility (no trade can take place). If the seller is in the mechanism, the agents other than the seller recieve 1 utility.

- 0 - 1 = 0.1

### #3

Which of these properties does the VCG mechanism fail to satisfy in this setting?

- Weak budget balance

### #4

What condition guarantees weak budget balance in VCGs, but is not satisfied by this simple exchange setting?

- No single-agent effect
