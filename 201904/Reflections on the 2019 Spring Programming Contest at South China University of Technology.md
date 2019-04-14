# Reflections on the 2019 Spring Programming Contest at South China University of Technology

On the morning of the competition, the neighboring dormitory was undergoing renovation, which was extremely noisy and
toxic. I gathered my necessary materials, including code templates and books, and headed to the B3 academic building.

### Preparation before the competition

I installed Firefox, CodeBlocks, and Python3, which covered most of the necessary tools. One new realization I had this
time was the importance of organizing code files using the acronym of team members' names. This way, we wouldn't have to
constantly switch between files, and everyone would immediately know who wrote which code. If someone needed to open
multiple files, they could simply add a number or letter at the end for their own distinction.

Personally, I'm not a big fan of using faster input, but in order to maintain consistency within the team, I decided to
adapt to the habits of the other two members. After all, not every competition allows to copy sample input directly, and
some, like the XuZhou Site Regional Competition that used PC2 (a coding platform), required reading input from files
instead of stdin.

### The Competition Begins

#### [Problem A - 1st try]

At first, I mistakenly thought it was a digit DP problem, but we should better to started with the sign-in problem.

#### [Problem L]

Initially, Pan Dalao found the sign-in problem "Rock Paper Scissors, and I started coding on the computer (to avoid
getting no experience). However, I had some issues with my typing speed, and I made a few mistakes. Nevertheless, I
managed to pass it in a little over two minutes, which was normal.

That was the 1st AC.

#### [Problem C - 1st try]

Mo Dalao found problem C, which involved popping out the maximum values from four positions in a specific order. We
didn't have a clear greedy approach in mind, so I initially submitted a wrong algorithm and then corrected it and
submitted again. Through some random test cases, we accidentally discovered a bug. In fact, when encountering the same
numbers, we should prioritize popping out the one with a larger second highest digit, and if the second highest digits
are the same, we continue this process. After finishing that, I switched with Pan Dalao to work on the stock trading
problem.

#### [Problem I]

It was a simple dynamic programming problem, and I think I had solved a similar one on Codeforces before. Pan Dalao
quickly solved it.

That was the 2nd AC.

#### [Problem E - 1st try]

I started working on the Sudoku problem, thinking it required depth-first search.

#### [Problem H]

I realized that problem H was about finding the sum of the greatest common divisors (GCDs) of every subinterval in a
given interval. My initial thought was to use a segment tree for range minimum query (RMQ) since GCD is essentially the
minimum of the prime factors. So, I thought of enumerating RMQ for each subinterval, but it turned out to be too
inefficient due to the time it would take to enumerate all the subintervals.

However, my wrong algorithm gave Pan Dalao an idea. And he mentioned that he had dealt with a similar problem before,
estimated the complexity, and started coding. Meanwhile, I continued thinking about problem C.

That was the 3rd AC.

#### [Problem C - 2nd try]

Pan Dalao randomly mentioned using BigInteger for problem C and comparing which one is larger. His wrong algorithm
inspired me, and after careful consideration, I realized it should be sorted in lexicographic order. In cases where
neither string reached the end, a larger lexicographic order indicated a higher priority. If one string was a prefix of
the other, it was better to pop out the longer string first because there might be a larger character following it after
the shorter string was popped. This insight helped us solve the problem. Since I failed to solve it myself and became
afraid of touching keyboard, Pan Dalao combined my understanding with his code and made adjustments using structs and
other operations. We passed the case we used to discover the previous bug and submitted, resulting in an acceptance.

That was the 4th AC.

#### [Problem E - 2nd try]

Next was the Sudoku problem, which was a template problem. Initially, I couldn't find the template, so I started writing
it by hand, which was a disadvantage. After Pan Dalao found the Kuangbin's template and copied it, we debugged it, and
it passed quickly.

That was the 5th AC.

#### [Problem B]

Mo Dalao started working on problem B. I couldn't quite understand if it was a greedy problem or not. It didn't really
fall under my responsibility.

#### [Problem A - 2nd try]

I thought it was a digit DP problem again, but upon closer inspection, the task was to find the factorization of the
product of all digit, and the product should be between L and R, rather than the attendance of products between L and R.

After some analysis and relying on my intuition from solving numerous (trivial) number theory problems, it was clear
that the product could only have four factors: 2, 3, 5, and 7, since all numbers between 0 and 9 will be factorizated to
them. (Actually, we needed to handle the special case of 1 as well, thanks to Pan Dalao's reminder, as it resulted in
avoiding an unnecessary Wrong Answer). I started considering a depth-first search to enumerate all possible products, as
I believed there wouldn't be many since we only had four factors to enumerate, and it would quickly exceed the range of
the type unsigned int.

#### [Problem K]

Pan Dalao managed to solve the suffix automaton problem as if it were a hashing problem. Pan Dalao is truly amazing!
666!

That was the 6th AC.

### Standing freeze

Now only problem A and B are being worked on, with Mo Dalao working on B. I took a look at problem J and decomposed the
determinant, realizing it was about finding the maximum slope. I informed Mo Dalao, who thought it might be a dynamic
convex hull problem. Since it involved geometry, I didn't have to think much about it. Amazing! My teammate is so
strong, and it's really comfortable to work as a supporting role.

#### [Problem A - 3rd try]

After discussing, we decided that I would work on problem A on the computer instead of having Mo Dalao work on problem
B. However, I wasted a lot of time implementing and debugging, which I feel so sorry for Mo Dalao about.

This problem was the only one in the competition that I found quite enjoyable to work on.

Below is the process of my poor implementation using recursion, as I rarely write such problems:

1. Firstly, during the search, I enumerated the powers of the four prime factors and need to use their powers
   extensively. So, I preprocessed them and calculate the maximum powers for unused factors (though I probably only used
   a small portion of the space complexity later).
2. I wrote a depth-first search to enumerate the powers of the four factors. Whenever encountering a combination of
   powers that has not been searched yet (forgot to mark vis = 1, my mistake), recorded it. Finally, sorted it before
   outputting. After running, I found that there were less than 7000 combinations.
3. Then, I thought about how to calculate the factorization of a product. I performed a second depth-first search to
   enumerate the individual factors. I passed an array p representing the powers of the factors from 2 to 9. I replaced
   some 2's with 4 and 8, and replaced 3 with 9. Then I combined 2 and 3 to make 6, and finally combined 2 and 4 to make
   8 (although I was not sure if there would be duplicates).
4. I converted the powers of each factor into a string, where each character was '0' plus the corresponding power.
   Actually, when the power exceeds 9, the display of this string became uncertain, but in this problem nobody would
   care the display form. I inserted the string into a set to check for duplicates.
5. I realized that the set needs to be cleared each time when enumerating a new product.
6. Done! After knowing the powers of each factor, I created a permutation with repeated elements. I copied a template
   from the book called Combinatorial Mathematics, but luckily, Pan Dalao pointed out the error in calculating the
   permutation. Otherwise, I would have wasted a lot of time discovering.
7. I performed the calculation, to create an answer table, and output it to a file.
8. I opened another file to paste the table, but I found that the format of the table is not appropriate, so I go back
   and modify the table.
9. I designed a map to store the corresponding product, but I realized it was not a smart approach, so I changed the
   table to an array (fortunately, generating the table didn't take much time).
10. I manually simulated it and found that "L" is the result of lower_bound(), and "R" is the result of upper_bound() -
    1. Thanks to Pan Dalao's reminder, I handled the cases where L=0 or R=0. Also, I discovered that using digit 1 was
       not allowed in this problem.
11. I computed the prefix sum and obtained the answer. I pasted the example and found that it was not correct; it failed
    for full-scale data sets.
12. I went back to modify the table and realized that the error was in the preprocessing phase before the second
    depth-first search. I forgot to update the decomposition of 7 when copying and pasting.
13. I regenerated the table, pastde it, ran the program, passed the sample input, and handled boundary cases. I
    submitted the code, but it failed to compile. All done in one go.
14. I noticed that the compilation error truncates the second table. It meaned that maybe submitting only the first
    table was sufficient. So, I copied the depth-first search part from the first table and made some modifications for
    a few minutes.
15. I ran it, and it matched the previously submitted table. I submitted it, feeling excited that I finally achieved an
    Accepted (AC) result. Otherwise, I would have to modify the table, and who knows how long it would take. At this
    point, there was only 25 minutes left.

That was the 7th AC.

#### [Problem J]

Mo Dalao stopped writing B and started writing J instead. (Who got the first blood balloon from JB last time?) Pan Dalao
and I officially afk and started reviewing the game, having a lively discussion.

In the end, Mo Dalao gave up on solving a problem. It was okay, geometry was indeed difficult without a readily
available template.

### The competition has ended

The final rankings were out, with 7 problems we solved. We ranked 6th in the university competition, and I was very
satisfied. I managed to secure a gold medal by relying on the support of experienced players.

### Reviewing the Competition

Many teams managed to solve problem F. It seems that this probability dynamic programming problem isn't as complicated
as we thought, but we didn't attempt it because there were easier problems available. I wonder if we would have had a
chance to solve problem F if I had solved problem A faster? It's hard to say. In any case, Mo Dalao spent a lot of
effort on problem B. If we had attempted problem F and come up with a basic approach, Mo Dalao probably wouldn't have
worked on problem B.

They say problem B was an easy problem, but who believes that?

If there's a challenging problem in the next competition, will DQ's them defeat us again?
