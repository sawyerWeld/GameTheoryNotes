## #1

Three players together can obtain 1 to share, any 2 can obtain 0.8, and one player by themself can obtain 0. Which allocation is in the core of the game?

- (1/3, 1/3, 1/3)

## #2

- There is a market for an indivisibel good with B buyers and S sellers.
- Each seller has only one unit of the good and has a reservation price of 0.
- Each buyer wantes to buy only one unit of the good and has a reservation price of 1.
- Thus v(C) = min(Bc,Sc) where Bc and Sc are the number of buyers and sellers in coalition C (and so, for instance v(i) = 0 for any single player, and v(i,j) = 1 if i,j are a pair of a buyer and a seller).

If the number of buyers and sellers is B=2 and S=1, which allocations are in the core?

Note: I don't know what a reservation price is, that wasn't in the lectures.

- Each seller receives 1 and each buyer 0. No.
- Each seller receives 0 and each buyer 1. Yes.
- Each seller receives 1/2 and each buyer receives 1/2. No. Could total to 3/2.

## #3

Same as above, but B=2 and S=2. 

- Each seller receives 1 and each buyer receives 0. 
- Each seller receives 0 and each buyer receives 1.
- Each seller receives 1/2 and each buyer receives 1/2.

I think the answer is all 3?

## #4

- The instructor of a class allows students to collaborate and write up together a particular problem in the homework assignment.
- Points earned by a collaborating team are divided up among the students in any way they agree on.
- There are exactly three students taking the course, all equally talented, and they need to decide if any should collaborate.
- The problem is so hard that none alone can score any points. Any two of them can score 4 points. All three could score 6 points.

Which allocation is in the core?

- (2,2,2)

## #5

Same as above, what is the shapley value of each player?

Each should be 2. 

The following format would the followed for every construction of a coalition:

1 12 123 v(1)=0, v(12)=4, v(123)=6

Here 2 gets 4 points and 3 gets 2. There are 6 possible constructions. In 1/3 each player gets 0, in 1/3 each gets 4, and in 1/3 each gets 2. In total this is (1/3)(0)+(1/3)(4)+1/3)(2) = a shapley value of 2 each.

## #6 

There is a single capitalist (c) and a group of 2 workers (w1,w2).

The production funciton is such that total output is 0 if the coalition is composed of only the capitalist or only the workers 

The production function satisfies:

- F(c union w1) = F(c union w2) = 3
- F(c union w1 union w2) = 4

Which allocations are in the core? Form is (c,w1,w2)

- (2,1,1)
- (2.5,0.5,1)
- (4,0,0)

## #7 

Same as above, find the Shapley value of the capitalist.

(c,w1,w2) = (1,2,3)

```
1 12 123 v(1) = 0
1 13 123 v(1) = 0
2 12 123 v(12)-v(2) = 3
2 23 123 v(123)-v(23) = 4
3 13 123 v(13)-v(3) = 3
3 23 123 v(123)-v(23) = 4
```

Shapley(c) = (1/3)(0)+(1/3)(3)+(1/3)(4) = 1+4/3 = 7/3

## #8

Same as above, find the Shapley value of each worker.

Let's analyze w1, who is represented by a 2.

```
1 12 123 v(12)-v(1) = 3
1 13 123 v(123)-v(13) = 1
2 12 123 v(2) = 0
2 23 123 v(2) = 0
3 13 123 v(123)-v(13) = 1
3 23 123 v(23)-v(3) = 0
```

Shapley(w1) = (1/2)(0)+(1/3)(1)+(1/6)(3) = 1/3 + 1/2 = 5/6

## #9






