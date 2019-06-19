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







