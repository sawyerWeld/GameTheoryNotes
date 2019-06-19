## #1

Consider a society of 1002 voters, in which voters rank four candidates A,B,C,D as follows:

```
400: A B D C
300: D C B A
200: B D C A
100: C A B D
  2: C D A B
```

Under the plurality voting system, which candidate would be declared the winner?

A. A got more votes as first than any other candidate.

## #2

Same as above, but plurality with elimination.

Nobody has a majority, so C is eliminated:

```
400: A B D 
300: D   B A
200: B D   A
100:   A B D
  2:   D A B
```

Next B is eliminated:

```
400: A   D 
300: D     A
200:   D   A
100:   A   D
  2:   D A  
```

D wins 502 to 500.

## #3

Same as above, with the borda count rule.

```
								Running Total     
     3 2 1 0 <- 'Borda Points'  A     B     C     D
400: A B D C = 1200 800 400 0   1200  800   0     400
300: D C B A =  900 600 300 0   1200  1100  600   1300
200: B D C A =  600 400 200 0   1200  1700  800   1700
100: C A B D =  300 200 100 0   1400  1800  1100  1700
  2: C D A B =    6   4   2 0   1402  1800  1106  1704
```

B wins on Borda count.

## #4

Same as above, but with successive elimination with ordering D,B,A,C

```
400: A B D C
300: D C B A
200: B D C A
100: C A B D
  2: C D A B
```

D vs B: 302 vs 700, B progresses

B vs A: 500 vs 502, A progresses

A vs C: 400 vs 602, C progresses and wins

## #5

Let us adapt the pairwise successive elminination voting scheme to produce a social welfare function - instead of determining one wining outcome, we want to rank the alternatives. Let us define this welfare function as follows:

- Perform successive elimination with the current agenda to determine a 'winner'
- Remove the winner from the agenda and then repeat this process with the remaining agenda

Does this satisfy IIA?

No. A social welfare function that satisfies IIA depends only on the relative orderings between two agents to determine their relationship.

## #6

Same as above, does this social welfare function satisfy dictatorship?

No, the initial ordering is specified by agent 1, who could alter their vote to specify an exact outcome under the right circumstances (im a little iffy on this one?)

## #7

Same as above, does this social welfare function satisfy the Condorcet principal?

The condorcet principal states that if a condorcet winner (wins every pairwise comparison) exists, it should be the winner of the social welfare funciton. This principal is satisfied, as successive elimination works through pairwise comparison.

Yes.

## #8

Consider the following social choice function, which we'll call benign dictatorship (BD). Under this social choice function, each voter submits a strict total ordering over the candidates, and the winning candidate is determined as follows: For each candidate, count the number of times that it appears at the top of a voter's ordering. If there is a single candidate with the maximum count, it is declared the winner. Otherwise, there must be a tie. The tie is broken according to the preference of voter #1 (the benign dictator). Thus, BD is plurality rule with dictatorial tie breaking.

Does DB satisfy Weak Pareto efficiency?

Yes. In the case of a weak pareto winner, there is no tie, so nothing dictatorial happens.

## #9 

Same as above, does BD satisfy dictatorship?

No, if everyone ties, voter 1's vote is chosen as the outcome.

## #10

Same as above, does BD satisfy monotonicity?

No. Monotonicity states that an outcome must remain the winner when support for it is increased. This is not satisfied by plurality.

## #11

Same as above, does BD satisfy the Condorcet Criterion? 

No. The condorcet criterion states that if a condorcet winner exists (a candidate which is preferred to every other candidate by majority), it will win. Plurality does not satisfy the condorcet criterion.

## #12

Same as above, is it ever rational for a voter to lie? IE will a voter ever recieve more utility from voting from expressing a preference which is not their true preference? 

Yes, this is the whole problem with plurality. You receieve more ulitity from voting for a candidate you're ok with who has high chance of beating out candidates you don't like than you do from voting for a candidate who you love but has no chance of winning.







