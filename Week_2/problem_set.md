## #1

|       | Left | Right |
| ----- | ---- | ----- |
| Left  | 4,2  | 5,1   |
| Right | 6,0  | 3,3   |

P1 randomizes over L(p) and R(1-p). What is p?

P1 would like to equilize the benefit that P2 gets from Left and Right.
P2's payoff for Left is 2p + 0(1-p) = 2p.
P2's payoff for Right is 1p + 3(1-p).

```
2p = 1p + 3(1-p)
2p = 1p + 3 - 3p
2p = -2p + 3
4p = 3
p = 3/4
```

## #2

|       | Left | Right |
| ----- | ---- | ----- |
| Left  | X,2  | 0,0   |
| Right | 0,0  | 2,2   |

Same as above but different payoffs. How does p change as X changes?

P1 would like to equilize the benefit that P2 gets from Left and Right.
P2's payoff for Left is 2p + 0(1-p) = 2p.
P2's payoff for Right is 0p + 2(1-p) = 2-2p.

```
2p = 2-2p
4p = 2
p = 1/2, regardless of X.
```

P2 would like to equalize the benefit that P1 gets from Left and Right.
P1's payoff for left is Xq + 0(1-q) = Xq.
P1's payoff for Right is 0q + 2(1-q) = 2-2q.

```
Xq = 2(1-q)
Xq = 2-2q
Xq+2q = 2
q(X+2) = 2
q = 2/(X+2)
As X increases, q decreases.
```

## #3

There are two firms, each with a job opening.

Firm 1 offers wage of 4, firm 2 offers wage of 6.

There are 2 unemployed workers looking for jobs. They both apply to one of the firms.

If only one worker applies to a firm, he gets the job. If both apply to the same job, each have a 50% chance of getting the job.

What is the mixed strategy equilibrium?

|        | Firm 1 | Firm 2 |
| ------ | ------ | ------ |
| Firm 1 | 2,2    | 4,6    |
| Firm 2 | 6,4    | 3,3    |

P1 would like to equalize P2's payoffs from applying to 1 and 2.

P2's payoff for F1 is 2p + 4(1-p).

P2's payoff for F2 is 6p + 3(1-p).

```
2p + 4(1-p) = 6p + 3(1-p)
2p + 4 - 4p = 6p + 3 - 3p
-2p + 4 = 3p + 3
1 = 5p
p = q = 1/5 (game is symmetric)
```

## #4

A king is deciding where to hide his treasure, while a pirate is deciding where to look.

The payoff to the king for hiding the treasure successfully is 5 and from having it found is 2.

The payoff to the pirate from finding the treasure is 9 and from not is 4.

| Payouts | King | Pirate |
| ------- | ---- | ------ |
| Found   | 2    | 9      |
| Not     | 5    | 4      |

Form=(King,Pirate). Found=(2,9) Hidden=(5,4).

The king can hide the treasure in locations x,y,and z.

The pirate can inspect x and y or just z (z is far away). What is a mixed strategy Nash equilibrium where p is the probability of hiding in xy and (1-p) is the probability of hiding in z?

|         | Look xy | Look z |
| ------- | ------- | ------ |
| Hide xy | 2,9     | 5,4    |
| Hide z  | 5,4     | 2,9    |

The king would like to equalize the pirates utility from looking (x or y) or z.

Pirate's payout from xy is 9p + 4(1-p).

Pirate's payout form z is 4p + 9(1-p).

```
9p + 4(1-p) = 4p + 9(1-p)
9p + 4 - 4p = 4p + 9 - 9p
5p + 4 = -5p + 9
10p = 5
p = 1/2
```

The pirate would like to equalize the king's utility from hiding (x or y) or z.

King's payout from xy is 2q + 5(1-q).

King's payout form z is 5q + 2(1-q).

```
2q + 5(1-q) = 5q + 2(1-q)
2q - 5q + 5 = 5q - 2q + 2
-3q + 5 = 3q + 2
3 = 6q
q = 1/2
```

## #5

Same as above, but the pirate can now invesitage any two locations, so he has pure strategies xy, yz, and xz. The king has 3 pure strategies x,y,and z.

What are the mixed strategy profiles?

|        | Look xy | Look yz | Look xz |
| ------ | ------- | ------- | ------- |
| Hide x | 2,9     | 5,4     | 2,9     |
| Hide y | 2,9     | 2,9     | 5,4     |
| Hide z | 5,4     | 2,9     | 2,9     |

There is nothing better than random selection here.




















