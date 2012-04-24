Topswop
=======

Permutations with maximal top swop iterations

http://oeis.org/A000375/internal

Background
----------

Start by shuffling n cards labeled 1, 2, ..., n.
If top card is m, reverse the order of the top m cards, then repeat.
a(n) is the maximal number of steps before top card is 1.

 n   1  2  3  4  5   6   7   8   9  10  11  12  13   14   15   16   17   18
a(n) 0, 1, 2, 4, 7, 10, 16, 22, 30, 38, 51, 65, 80, 101, 113, 139, 159, 191

If s(permutation) denotes the number of topswops, trivially,
s([1, x, x, ..., x]) = 0, where the x's are an arbitrary permutation
of [2, 3, ..., n].

An example for n=6: p = [5, 6, 1, 4, 2, 3]
s(p)= 9, the swops are:
  1. R[5, 6, 1, 4, 2] + [3] = [2, 4, 1, 6, 5, 3]
  2. R[2, 4] + [1, 6, 5, 3] = [4, 2, 1, 6, 5, 3]
  3. [6, 1, 2, 4; 5, 3]
  4. [3, 5, 4, 2, 1, 6;]
  5. [4, 5, 3; 2, 1, 6]
  6. [2, 3, 5, 4, 1, 6]
  7. [3, 2, 5, 4, 1, 6]
  8. [5, 2, 3, 4, 1, 6]
  9. [1, 4, 3, 2, 5, 6]

There are five permutations which give a(6) = 10 swops:
  416523, 415263, 564132, 365142, and 456213.
None of the 6! = 720 permutations have more than 10 swops.

The first open case a(19) has 19! - 18! (over 115,000,000,000,000,000)
permutations to check, after eliminating the case of zero swops.
Even testing a million a second, checking them would take nearly
3,652 years.

How many permutations p have s(p) = 1?
There are n-1 permutations with 2 places fixed:
  [x1=j, x2, x3, ..., xj=1, .. xn] where x1=j>1.
So there are (n-1)(n-2)! = (n-1)! of them, the same as for s(p)=0.

Easily, a(19) > 70, s[8, 7, 1, 9, 18, 16, 14, 4, 19, 17, 12, 2, 3, 13, 10, 11, 6, 15, 5] = 71.
So we are down to 19! - 2*18! (about 109,000,000,000,000,000) cases.

If xj=k is also not 1, the first swop gives:
  [xj=k, x(j-1), ..., x2, x1; x)j+1), x(j+2), ..., xn].
The permutation p has s(p) = 2 when xk = 1 where k is
in {2, 3, ..., n} / {j}.
There are (n-1)(n-2) permutations with 3 places fixed,
so s(p) = 2 for (n-1)(n-2)(n-3)! = (n-1)!
Reducing our trails to 19! - 3*18! (about 103,000,000,000,000,000) cases.

Counting cases for s(p) = 3 is not so simple because the second swop
has different formats depending on whether j<k or k>j and some of these
cases overlap.

Here is a histogram for n=7:
  s(p)=0  for 720 permutations
  s(p)=1  for 720 permutations
  s(p)=2  for 720 permutations
  s(p)=3  for 648 permutations
  s(p)=4  for 548 permutations
  s(p)=5  for 440 permutations
  s(p)=6  for 338 permutations
  s(p)=7  for 268 permutations
  s(p)=8  for 218 permutations
  s(p)=9  for 160 permutations
  s(p)=10 for 104 permutations
  s(p)=11 for  65 permutations
  s(p)=12 for  44 permutations
  s(p)=13 for  26 permutations
  s(p)=14 for  14 permutations
  s(p)=15 for   5 permutations
  s(p)=16 for   2 permutations

The maximum is reached by [3, 1, 4, 6, 7, 5, 2] and [4, 7, 6, 2, 1, 5, 3].
