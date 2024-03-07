## Fundamental Principles

>[!def] Definition Addition Principle ([[../../../PDFs/brualdi2004.pdf#page=57|Source]])
>Suppose that a set $S$ is partitioned into parts $S_{1}, S_{2}, \dots, S_{m}$. The number of objects in $S$ can be determined by finding the number of objects in each of the parts, and adding the numbers so obtained: $$\lvert S \rvert = \lvert S_{1} \rvert + \lvert S_{2} \rvert + \dots+ \lvert S_{m} \rvert   $$
>>[!example] 
>> Suppose we wish to find the number of different courses offered by the University of Wisconsin-Madison. We partition the courses according to the department in which they are listed.
>>
>>Provided there is no cross-listing, the number of courses offered by the University equals to the sum of the number of courses offered by each department
>
>>[!example] 
>>A student wishes to take either a mathematics course or a biology course, but not both. If there are 4 mathematics courses and 3 biology courses for which the student has the necessary prerequisites, then the student can choose a course to take in $4+3=7$ ways.

^2c1488


>[!def] Definition Multiplication Principle ([[../../../PDFs/brualdi2004.pdf#page=58|Source]])
>Let $S$ be a set of ordered pairs $(a,b)$ of objects, where the first object $a$ comes from a set of size $p$, and for each choice of object $a$ there are $q$ choices for object $b$. Then the size of $S$ is $p \times q$:
>$$\lvert S \rvert = p \times q $$
>>[!remark] Remark Multiplication Principle a consequence of the Addition Principle
>> Let $a_{1}, a_{2}, \dots , a_{p}$ be the different choices for set $p$. We partition $S$ into $$S=S_{1} \cup S_{2} \cup \dots \cup S_{p}$$
>> where
>> $$S_{i} = \{ (a_{i}, b_{1}), (a_{i}, b_{2}), \dots, (a_{i}, b_{q}) \}$$
>> Hence, $\lvert S_{i} \rvert = q$
>> By the addition principle we have
>> $$\begin{align}
>> \lvert S \rvert &= \lvert S_{1} \rvert + \lvert S_{2} \rvert + \dots + \lvert S_{p} \rvert  \\
>>       &= \lvert p \rvert \cdot \lvert q \rvert \\
>>       &= \lvert p \times q \rvert   
>>\end{align}$$
>
>>[!example]
>>Chalk comes in 3 different lengths, 8 different colors, and 4 different diameters. How many different kinds of chalk are there?
>>
>> We denote the different kinds of enumerated sets indexed with the set-subscript 
>> - $L$ - length
>> - $C$ - colors
>> - $D$ - diameters
>>
>>we have
>>$$\begin{align}
>> L &= \{ 1_{L}, 2_{L}, 3_{L} \} \\
>> C &= \{ 1_{C}, 2_{C}, \dots, 8_{C} \}  \\
>> D &= \{ 1_{D}, 2_{D}, 3_{D}, 4_{D} \}
>>\end{align}$$
>>Looking for all possible kinds of subset, we need to combine each item of a set with each of item of the other sets, which is by definition the cross product
>>$$L \times C\times D = \{ (1_{L}, 1_{C}, 1_{D}), \dots \}$$
>>The number of all kinds therefore is
>>$$\lvert L \times C \times D \rvert =  \lvert L \rvert \cdot \lvert C \rvert \cdot \lvert D \rvert = 3 \cdot 8 \cdot 4 = 96    $$
>
>>[!example] 
>>Given are 5 men, 6 women, 2 boys and 4 girls. Count the number of ways a man, woman, boy and girl can be selected.
>>
>>Again, we can denote sets enumerating the persons of each category, where there is no overlap between them
>>$$\begin{align}
>> M &= \{ 1, \dots, 5 \} \\
>> W &= \{ 1, \dots, 6 \} \\
>> B &= \{ 1,2 \} \\
>> G &= \{ 1,\dots, 4 \}
>>\end{align}$$
>> Asking for the number of ways to combine the items of these sets, asks for the cardinality of their cross product
>> $$\lvert M \times W \times B \times G \rvert = \lvert M \rvert  \cdot \lvert W \rvert \times \lvert B \rvert \times \lvert G \rvert = 5 \cdot 6 \cdot 2 \cdot 4 = 240 $$
>
>>[!example]
>>Determine the number of positive integers that are factors of the number
>>$$3^4 \cdot 5^2 \cdot 11^7 \cdot 13^8$$
>>Note, the bases are all prime numbers, hence, these can be the only possible factors. Any multiplication of these will be a factor of the given number. We can describe the factors over a set of powers of the primes, i.e.
>>$$\begin{align}
>> \mathbb{3} &= \{ 0,1,2,3,4 \} \\
>> \mathbb{5} &= \{ 0,1,2 \} \\
>> \mathbb{11} &= \{ 0,1,\dots,7 \} \\
>> \mathbb{13} &= \{ 0,1,\dots,8 \}
>>\end{align}$$
>> Using the multiplication principle we determine the number of elements in the cross product and get
>> $$\lvert \mathbb{3} \times \mathbb{5} \times \mathbb{11} \times \mathbb{13} \rvert = 5 \cdot 3 \cdot 8 \cdot 9 = 1080$$
>>>[!note]
>>>In this example we have repetition in the elements which count factorizations with $x^0$ multiple times, i.e.
>>>$$(1,1,1,1),(1,3,1,1), (1,1,1,3),\dots$$
>>>Further, we have the order is taken into account and the factors are considered to be distinguishable

^e662cc

>[!def] Definition Subtraction Principle ([[../../../PDFs/brualdi2004.pdf#page=60|Source]])
>Let $A$ be a set and let $U$ be a larger set containing $A$. Let 
>$$\overline{A} = \{  x \in U : x \not\in A \}$$
>be the complement of $A$ in $U$. Then the number $\lvert A \rvert$ of objects in $A$ is given by the rule 
>$$\lvert A \rvert = \lvert U \rvert - \lvert \overline{A} \rvert $$
>>[!remark]
>> - $U$ is called the universal set
>> - this method makes sense, if it is easier to count the number of object in $U$ and $\lvert \overline{A} \rvert$ than in $A$
>
>>[!example]
>> Computer passwords are to consist of a string of 6 symbols taken from the digits $0,1,2,\dots,9$ and the lowercase letters $a,b,c.., z$. How many computer passwords have a repeated symbol?
>>
>> First, we calculate the total amount of possible passwords. Using the multiplication principle we have for the set of all strings $\Sigma$
>> $$\begin{align}
>> \Sigma &= \{ 0,1,\dots, 9, a, b, \dots, z \} \\
>> \lvert \Sigma \rvert &= 36 \\
>> \lvert \Sigma^6 \rvert &= 36^6  \\
>> &= 2\;176\;7823\;336 
>>\end{align}$$
>>Now we determine the number of passwords with no repeated symbol. For the first string we choose some arbitrary string $\alpha_{1} \in \Sigma$ where we can choose from 36 strings. After choosing $\alpha_{1}$ we are not allowed to choose $\alpha_{1}$ again. Hence, we now are allowed to choose another string $\alpha_{2} \in \Sigma \setminus \{ \alpha_{1} \}$ which is now a set with 35 strings. Repeating this for all the 36 strings yields:
>>$$\begin{align}
>> \lvert \overline{A} \rvert &= \lvert \Sigma \rvert  \cdot \lvert \Sigma \setminus \{ \alpha_{1} \} \rvert  \cdot \lvert \Sigma \setminus \{ \alpha_{1}, \alpha_{2} \} \rvert \cdot\dots \cdot \lvert \Sigma \setminus \{ \alpha_{i} \}_{i=1}^6 \rvert    \\
&= 36 \cdot 35 \cdot 34 \cdot 33 \cdot 32 \cdot 31  \\
>> &= 1\;402\;410\;240
>>\end{align}$$
>> 

>[!def] Definition Division Principle ([[../../../PDFs/brualdi2004.pdf#page=61|Source]])
>Let $S$ be a finite set that is partitioned into $k$ parts in such a way that each part contains the same number of objects. Then the number of parts in the partition is given by the rule
>$$k = \frac{\lvert S \rvert }{\text{number of obects in a part}}$$
>
>>[!example]
>> There are 740 pigeons in a collection of pigeonholes. If each pigeonhole contains 5 pigeons, the number of pigeonholes equals
>> $$\frac{740}{5} = 148$$

>[!example] Mixed Examples 
>>[!example]
>>Give Aunt Mollie a basket of fruit. Our refrigerator contains
>>- 6 oranges
>>- 9 apples
>>
>>The requirement is, the basket must contain at least one fruit. How many different baskets of fruit are possible?
>>>[!Example] Solution 1
>>> First compute all possible ways to fill a basket, denote the set of oranges $O = \{ 0,\dots,6 \}$ and the set of apples $A=\{ 0,\dots, 9 \}$ including to have $0$ either of them. We have
>>> $$\begin{align}
>>> \lvert O \rvert  &= 7  \\
>>> \lvert A \rvert &= 10
>>>\end{align}$$
>>> By the multiplication principle we have the total amount of ways $\lvert U \rvert$to fill the basket
>>> $$\begin{align}
>>> \lvert U \rvert &= \lvert O \times A \rvert  \\
>>> &= \lvert O \rvert \cdot \lvert A \rvert  \\
>>> &= 7 \cdot 10 \\
>>> &= 70
>>>\end{align} $$
>>>The requirement is to have always at least one fruit in it. Let $\overline{K}$ denote the set of enumerations where the basket is empty
>>>$$\overline{K} = \{ (0,0) \}$$
>>>Hence, the enumeration with non empty basket is $K = U \setminus \overline{K}$. By the subtraction principle we have
>>>$$\begin{align}
>>> \lvert K \rvert &= \lvert U \rvert - \lvert \overline{K} \rvert \\
>>> &= 70-1 \\
>>> &= 69 \tag*{$\square$}
>>>\end{align}$$
>>
>>>[!example] Solution 2
>>> We partition the set of all ways to fill the basket as follows:
>>> 1. $S_{1}$ denotes the set with **at least 1 apple** and **no oranges**
>>> 2. $S_{2}$ denotes the set with **arbitrary many apples** and **at least 1 orange**
>>>i.e. $(apples, oranges)$
>>>$$\begin{align}
>>> S_{1} &= \{ (1,0), \dots,(9,0) \} \\
>>> S_{2} &= \{ (0,1), (0,2), \dots, (0,6),\dots , (10, 1), (9,2), \dots (9,6) \}
>>>\end{align}$$
>>>The multiplication principle gives us the amount of $S_{1}$ and $S_{2}$
>>>$$\begin{align}
>>> \lvert S_{1} \rvert &= 9 \cdot 1 = 9 \\
>>> \lvert S_{2} \rvert &= 10 \cdot 6 = 60  
>>>\end{align}$$
>>>By the addition principle we get
>>>$$\begin{align}
>>> \lvert S \rvert &= \lvert S_{1} \cup S_{2}\rvert   \\
>>> &= \lvert S_{1} \rvert + \lvert S_{2} \rvert \\
>>> &= 69 \tag*{$\square$}  
>>>\end{align}$$

>[!def] Definition Multiset ([[../../../PDFs/brualdi2004.pdf#page=50|Source]])
> A multiset is a collection of objects which can occur multiple, i.e. elements of such a set need not to be distinct
> $$\begin{align}
> M&= \left\{  \underbrace{ a_{1}, \dots ,a_{1} }_{ k_{1}\text{ times} }, \underbrace{ a_{2}, \dots, a_{2} }_{ k_{2}\text{ times} }, \dots, \underbrace{ a_{r}, \dots, a_{r} }_{ k_{r}\text{ times} }\right\} \\
> &= \{ k_{1} \cdot a_{1}, k_{2} \cdot a_{2}, \dots, k_{r} \cdot a_{r} \}
>\end{align}$$
>>[!note]
>>Usually sets are agnostic to elements occurring multiple times. An element occurring multiple times would usually only be counted once.

## Permutation of Sets

>[!def] Definition $r$-permutations ([[../../../PDFs/brualdi2004.pdf#page=65|Source]])
>Let $r$ be a positive integer. By an $r$-permutation of a set $S$ of $n$ elements, we understand an ordered arrangement of $r$ of the $n$ elements.
>
>We denote the $r$-permutation as 
>$$P(n,r)$$
>>[!terminology]
>>We say
>>****
>>**<div align="center">We arrange $r$ out of $n$</div>**
>>****


>[!theorem] Theorem ([[../../../PDFs/brualdi2004.pdf#page=65|Source]])
>For $n,r \in \mathbb{N}^+$ with $r \leq n$ 
>$$\begin{align}
> P(n,r) &= n \cdot (n-1) \cdot \dots \cdot (n-r+1) \\ 
> &= \frac{n!}{(n-r)!} \\
> &= n^{\underline{r}}
>\end{align}$$
>>[!remark]
>>
>>If $r > n$ we agree on
>>$$P(n,r) = 0$$
>
>>[!proof]- Proof (Constructive)
>> Given is an $n$-element set $S$. Constructing the ordered arrangement, we choose some element $\alpha_{1} \in S$ with $n$ choices. Since $\alpha_{1}$ is chosen, the set reduces to $S \setminus \{ \alpha_{1} \}$. Next, we choose another element $\alpha_{2} \in S \setminus \{ \alpha_{1} \}$ where we had $n-1$ choices. Again, the set reduces to $S \setminus \{ \alpha_{1}, \alpha_{2} \}$. This can be repeated until we have chosen $r$ elements.
>> 
>> By the [[#^e662cc| multiplication principle]] we get
>> $$\begin{align}
>> P(n,r) &= \Big\vert S  \times \Big(S \setminus \{ \alpha_{1} \}\Big) \times \Big(S \setminus \{ \alpha_{1}, \alpha_{2} \}\Big) \times \dots \times \Big(S \setminus \{ \alpha_{i} \}_{i=1}^r\Big)\Big\vert \\
>> &= \Big\vert S \Big\vert \cdot \Big\vert S \setminus \{ \alpha_{1} \} \Big\vert \cdot \Big\vert S \setminus \{ \alpha_{1}, \alpha_{2} \}\Big\vert \cdot  \ \dots \cdot \Big\vert S \setminus \{ \alpha_{i} \}_{i=1}^r\Big\vert \\ 
>> &= n \cdot (n-1) \cdot (n-2) \cdot \dots \cdot (n-r+1) \tag*{$\square$}
>>\end{align}$$


>[!remark]
>If
>1. $r < n$ we denote the $r$-permutation as **variation**
>2. $r = n$ we denote the $r$-permutation as **permutation** with $$P(n,n) = \frac{n!}{0!} = n!$$

>[!example] Examples
>>[!example]
>>Find the number of 4 letter strings that can be formed by using each of the letters $a,b,c,d,e$ at most once
>>>[!example]- Solution
>>>We have
>>>$$\begin{align}
>>> n &= 5 \\
>>> r &= 4
>>>\end{align}$$
>>>Using the formula for $r$-permutations
>>>$$P(5,4)= \frac{5!}{(5-4)!} = 120$$
>>
>
>>[!example]
>>Find all possible configurations of the so called "15 puzzle", no matter it is possible or not.
>>
>>![[Figures/ex_puzzle.png|center]]
>>>[!example]- Solution
>>>The set of all possible configurations is to permute all 16 fields. We have
>>>$$\begin{align}
>>> n &= 16 \\
>>> r &= 16
>>>\end{align}$$
>>>$$P(16,16) = 16!$$
>>
>>Now, assume we have a 16x16 grid, how many possible configurations are possible?
>>>[!example]- Solution
>>>Note, any empty field can be well distinguished, because of its position. We are looking at how to place the numbers in the grid. We have 36 possible locations to place them, and we have in total 15 numbers. Hence,
>>>$$\begin{align}
>>> n&=36 \\
>>> r &= 15
>>>\end{align}$$
>>> Therefore,
>>> $$P(36,15) = \frac{36!}{(36-15)!} = \frac{36!}{21!}$$
>
>>[!example] 
>>What is the number of ways to order the 26 letters of the alphabet so that no two of the vowels $a,e,i,o$ and $u$ occur consecutively?
>>>[!example]- Solution
>>>First we consider the consonants, which are 21. They can be arranged in
>>>$$P(21,21) = 21!$$
>>>ways. Now consider the following
>>>$$|\;b\;| \;c\; | \;d\; | \; \dots | \; z \; | $$
>>>where each vertical bar can be considered a gap where a vowel can be placed. Since we have 21 consonants, we have 22 vertical bars. Hence, we can choose from 22 positions to put a vowel. 
>>>>[!note]- Note on Connection to Multiplication Principle
>>>>Putting the vowels into the blank spaces (vertical bars) can be constructed as a multiplication problem. Denote the spaces as $S=\{ s_i \;|\; 1\leq i\leq 22 \}$ and the set of vowels $V=\{ a,e,i,o,u \}$. We are looking for the amount of pairings $A$ with some choice $\alpha_{j} \in V$
>>>>$$A = S \times V \times V \setminus{\{ \alpha_{j} \}} \times \dots V \setminus{\{ \alpha_{i} \}}_{i=1}^4$$
>>>>where $\lvert A \rvert$ yields the amount of placements
>>>
>>>For these choices, we calculate the $r$-permutation
>>>$$P(22, 5) = \frac{22!}{(22-5)!} = \frac{22!}{17!}$$
>>>By the multiplication principle the total amount of arrangements can be given as
>>>$$21! \cdot \frac{22!}{17!}$$
>
>>[!example]
>>How many seven-digit numbers are there such that the digits are distinct integers taken from $\{ 1,2, \dots, 9 \}$ and such that the digits 5 and 6 do not appear consecutively in either order?
>>>[!example]- Solution 1
>>> 1. Neither $5$ nor $6$ Is inserted
>>> The case where none of the digits $5,6$ are placed can be given as the permutation of the set $\{ 1,2,3,4,7,8,9 \}$ with $7$ digits.
>>> $$\begin{align}
>>> P_{0}&=P(7,7) \\
>>>  &= 7! \\
>>> &= 5040
>>>\end{align}$$
>>> 2. Either a single $5$ or $6$ is inserted
>>> First we calculate the permutations of the digits without restrictions. We still have the set $\{ 1,2, \dots, 9 \}$, but we choose 6 out of 7, hence we have
>>> $$\begin{align}
>>> P'&=P(7,6)  \\
>>> &= 7! \\
>>> &= 5040
>>>\end{align}$$
>>>Now for each of these variations we can place either a 5 or a 6. Again we can imagine some variation of the form
>>>$$\underbrace{ |\; 1 \; | \; 2 \; | \; 3 \; | \dots |\; 9 \; | }_{ \substack{6 \text{ digits} \\ 7 \text{ bars}} }$$
>>> Therefore, we can place the last digit in any of these bars. For any variation, we therefore have 7 possible placements, hence
>>> $$\begin{align}
>>> P_{1} &= 7P' \\
>>> &= 7\cdot 7!
>>>\end{align}$$
>>>Lastly, since we can do this procedure for either 5 or 6, we have to count it twice, i.e.
>>>$$2P_{1}= 14 \cdot 7! = 70\;560$$
>>> 
>>> 3. Both 5 and 6 will be inserted
>>> For this case we again first arrange the set of unrestricted digits $\{ 1,2, \dots, 9 \}$. We choose 5 out of 7 and get
>>> $$\begin{align}
>>> P' &= P(7,5)  \\
>>>    &= \frac{7!}{(7-5)!} \\
>>>    &= 2520
>>>\end{align}$$
>>>Now we place both the 5 and 6 into 
>>>$$\underbrace{ |\; 1 \; | \; 2 \; | \; 3 \; | \dots |\; 9 \; | }_{ \substack{5 \text{ digits} \\ 6 \text{ bars}} }$$
>>> Hence, we calculate to choose 2 out of 6 bars and get
>>> $$\begin{align}
>>> P'' &= P(6,2)  \\
>>> &= \frac{6!}{(6-2)!} \\
>>> &= 30
>>>\end{align}$$
>>> Since any arrangement of the unrestricted digits can be paired with any placement of 5 and 6, we use  the  [[#^e662cc|multiplication principle]]. For the last case we get
>>> $$\begin{align}
>>> P_{3} &= P' \cdot P'' \\
>>> &= 2520 \cdot 30 \\
>>> &= 75\; 600
>>>\end{align}$$
>>>
>>> By the [[#^2c1488| addition principle]] combining our results for 1., 2. and 3. we get
>>> $$\begin{align}
>>> P_{0} + 2P_{1} + P_{2} &= 5\;040 + 70\;560 + 75\; 600 \\
>>> &=151\;200
>>>\end{align}$$
>>
>>>[!example] Solution 2
>>> Consider the whole set of digits $T=\{ 1,2,3,4,5,6,7,8,9 \}$. We compute all possible 7 digit arrangements. We arrange 7 out of 9
>>> $$\begin{align}
>>> P(9, 7) &= \frac{9!}{(9-7)!}  \\
>>> &= 181\; 440
>>>\end{align}$$
>>>Now, let's denote the set $S$ as the set of 7-digit numbers of $T$, where 5 and 6 are not consecutive. If we remove now the number of cases where they are consecutive, i.e $\overline{S}$, we yield the desired result. We now compute the number of elements of $\overline{S}$. Again, we arrange 5 of the unrestricted digits $\{ 1,2, \dots, 9 \}$, hence, we arrange 5 out of 7
>>>$$\begin{align}
>>> P(7,5) &= \frac{7!}{(7-5)!} \\
>>> &= 2520
>>>\end{align}$$
>>>Now we want to place the pair 56 (or 65) in the gaps
>>>$$\underbrace{ |\; 1 \; | \; 2 \; | \; 3 \; | \dots |\; 9 \; | }_{ \substack{5 \text{ digits} \\ 6 \text{ bars}} }$$
>>>Note, we treat the pair 56 (or 65) as a single element, hence, there are 6 choices for one element. Since we want to calculate for both pairs, we have to multiply everything by 2. By the multiplication principle we get
>>>$$\begin{align}
>>> \lvert \overline{S} \rvert &=  2 \cdot 6 \cdot 2520 \\
>>> &= 30\;240
>>>\end{align}$$
>>>Finally, using the subtraction principle we get
>>>$$\lvert S \rvert = \underbrace{ 181\;440 }_{ =\lvert T \rvert  } - \underbrace{ 30\;240 }_{ =\lvert \overline{S} \rvert  } = 151\;200$$

>[!note] Note, Circular Permutations have been omitted
## Combination of Sets

>[!def] Definition $r$-Combination ([[../../../PDFs/brualdi2004.pdf#page=72|Source]])
> Let $r$ be a non-negative integer. By an $r$-combination of a set $S$ of $n$ elements, we understand an unordered selection of $r$ of the $n$ objects of $S$.
>
>We denote the $r$-combination as
>$$C(n,r)$$
>>[!terminology]
>>We say
>>****
>>**<div align="center">We choose $r$ out of $n$</div>**
>>****

>[!def] Definition Binomial Coefficient
>$$\begin{align}
> \binom{n}{k} = \frac{n^{\underline{k}}}{k!} = \frac{n!}{k!(n-k)!}
>\end{align}$$

^4dc155

>[!property] Properties
>$$\begin{alignat}{2}
> \binom{n}{r} &= 0 \qquad && \text{ if } r > n\\
> \binom{0}{r} &= 0 && \text{ if } r > 0 \\
> \binom{n}{0} &= 1 \\
> \binom{n}{1} &= n \\
> \binom{n}{n} &= 1 
>\end{alignat}$$

>[!theorem] Theorem
> For $0 \leq r \leq n$
> $$P(n,r) = r!\binom{n}{r}$$
> It follows
> $$\begin{align}
> \binom{n}{r} &= \frac{P(n,r)}{r!} \\
> &= \frac{n!}{r!(n-r)!}
>\end{align}$$
>>[!proof]-
>> Let $\lvert S \rvert = n$. We break down an $r$-permutation into the following steps
>> 1. Choose $r$ elements from $S$ => $C(n,r) = \binom{n}{r}$
>> 2. Arrange the chosen $r$ elements in some order => $P(r,r) = r!$
>> 
>> Hence, by the multiplication principle we have
>> $$\begin{align}
>> P(n,r) &= r! \binom{n}{r} \\
>> &= \frac{n!}{r!(n-r)!}
>>\end{align}$$
>>Rearranging yields
>>$$\binom{n}{r} = \frac{P(n,r)}{r!}=\frac{n!}{r!(n-r)!}\tag*{$\square$}$$
>
>>[!note]
>> Looking at the proof, we notice, a combination is basically a permutation, where we remove for each.
>> 
>> Recall an $r$-permutation is any possible ordering from a set $S$ and choices $\alpha_{i} \in S$
>> $$S \times S\setminus \{ \alpha_{i} \} \times \dots \times S\setminus \{ \alpha_{i} \}_{i=1}^r$$
>> Note, by calculating the cross product we create a set of orderings of the form
>> $$\{ (\alpha_{1}, \alpha_{2},\dots, \alpha_{r})\; | \; \alpha_{i}\in S \}$$
>> In this set we will find the elements $\alpha_{1}-\alpha_{r}$ in $r$ different orderings. These orderings can be calculated for these particular elements as
>> $$P(r,r) = r!$$
>> An $r$-combination is basically an $r$-permutation where the different orderings for the set $\alpha_{1}-\alpha_{r}$ are removed.

>[!example] Examples
>>[!example]
>> There are 15 people enrolled in a mathematics course, but exactly 12 attend on any given day. Determine the number of students which could possibly attend the course.
>>>[!example]- Solution
>>>Since the ordering does not matter, we have a combination
>>>$$\begin{align}
>>> C(15,12) &= \frac{15!}{12!(15-12!)} \\
>>>   &= 455
>>>\end{align}$$
>>
>>Now assume there are 25 seats in the classroom, how many seating configurations would be possible, given that there are 12 out of 15 possible students.
>>>[!example]- Solution
>>> The possible combinations students could attend the course are already given by $$C(15,12)$$
>>> Since the ordering is meaningful in a room with seats, we calculate the $r$-permutation
>>> $$P(25,12) = \frac{25!}{(25-12)!}$$
>>> The final solution is
>>> $$C(15,12)\cdot P(25,12)$$
>

>[!property] Corollary ([[../../../PDFs/brualdi2004.pdf#page=75|Source]])
>For $0 \leq r \leq n$
>$$\binom{n}{r}= \binom{n}{n-r}$$

>[!theorem] Theorem ([[../../../PDFs/brualdi2004.pdf#page=75|Source]])
>$$\binom{n}{0}+\binom{n}{1}+\binom{n}{2}+ \dots + \binom{n}{n} = 2^n$$
>>[!proof]-
>> Let $S$ denote a set of cardinality $n$. First we note, that any binomial coefficient is the $r$-combination
>> $$C(n,r) = \binom{n}{r}$$
>> By the addition principle 
>> $$\sum_{i=1}^n \binom{n}{i} \tag{1}$$
>> represents the number of total combinations possible in $S$.
>>
>>Now we describe the set of all combinations in terms of $2^n$. If we wanted to choose for each element of $S$ to go into a combination or not, i.e. a binary decision with two outcomes. Since $S$ has $n$ elements, we would have to decide $n$ times. Thus, by the multiplication principle we have $$2^n\tag{2}$$ different combinations. Since equation $(1)$ and $(2)$ both represent the total amount of combinations, they must be equal
>>$$\sum_{i=1}^n \binom{n}{i} = 2^n \tag*{$\square$}$$

## Permutation of Multisets

>[!def] Definition Multiset Permutation ([[../../../PDFs/brualdi2004.pdf#page=76|Source]])
> If $S$ is a multiset, an $r$-permutation of $S$ is an ordered arrangement of $r$ of the objects of $S$. If the total number of objects of $S$ is $n$ (including repetitions), then an $n$-permutation of $S$ will also be called a permutation of $S$

>[!theorem] Theorem ([[../../../PDFs/brualdi2004.pdf#page=76|Source]])
>Let $S$ be a multiset with objects of $k$ different types, where each has an **infinite** repetition number.
> $$S = \{ \infty \cdot \alpha_{1}, \infty \cdot \alpha_{2}, \dots, \infty \cdot \alpha_{k} \}$$
>Then the number of $r$-permutations of $S$ is $$k^r$$
>>[!proof]-
>> Note, we want to arrange $r$ objects, where we can choose for each of the objects one of the $k$ distinct objects, which are in infinite supply. Let's denote the objects chosen from $S$ as $x_i$ with $1\leq i \leq r$. The first choice $x_1$ can be chosen from $k$ different objects. For any subsequent $x_i$ the choice remains the same. By the [[#^e662cc|multiplication principle]] we yield
>> $$k^r \tag*{$\square$}$$
>
>>[!example]
>>What is the number of ternary numerals (a number in base 3) with at most 4 digits
>>>[!example] Solution
>>> Note, the alphabet to choose from is $\Sigma = \{ 0,1,2 \}$. The multiset constructed from the alphabet is denoted as
>>> $$S = \{  \infty \cdot 0, \infty \cdot 1, \infty \cdot 2 \}$$
>>> Since we are looking for 4 digits ternary numerals, we can also give the multiset as
>>> $$S= \{  4 \cdot 0, 4 \cdot 1, 4 \cdot 2 \}$$
>>> Using the theorem, we arrange 4 digits from the multiset with 3 distinct objects, i.e.
>>> $$\begin{align}
>>> k&=3 \\
>>> r &= 4 \\
>>> k^r &= 3^4 = 81
>>>\end{align}$$

^9a298e

>[!theorem] Theorem ([[../../../PDFs/brualdi2004.pdf#page=77|Source]])
>Let $S$ be a multiset with objects of $k$ different types with **finite** repetition numbers $n_{1},n_{2}, \dots, n_{k}$ respectively. Let the size of $S$ be $n=n_{1}+n_{2}+\dots+n_{k}$. Then the number of permutations of $S$ equals
>$$\frac{n!}{n_{1}!n_{2}!\dots n_{k}!}$$
>>[!proof]-
>> Consider we want to put the objects into $n$ places. First we arrange all objects of type $n_1$ into places. Note, the objects of type $n_1$ are indistinguishable, hence, the order how they are placed is not of interest. Therefore, to place $n_{1}$ objects into $n$ places is a combination $$C_{n}^{n_{1}} = \binom{n}{n_{1}}$$
>> We repeat this process for the following objects. Note, the number of total reduces each time by the places occupied of the $n_i$ objects, i.e.
>> $$\begin{align}
>> C_{n-n_{1}}^{n_{2}} &= \binom{n-n_{1}}{n_{2}} \\
>> &\;\;\vdots \\
>> C_{n-\sum_{i=1}^{k-1}}^{n_{k}} &=\binom{n-\sum_{i=1}^{k-1} n_{i}}{n_{k}}  \\
>> &= \binom{n-n_{1}-n_{2}-\dots-n_{k-1}}{n_{k}}
>>\end{align}$$
>>By the multiplication principle we get
>>$$\binom{n}{n_{1}}\binom{n-n_{1}}{n_{2}}\binom{n-n_{1}-n_{2}}{n_{3}}\dots\binom{n-n_{1}-n_{2}-\dots-n_{k-1}}{n_{k}}$$
>>Using the definition of the [[#^4dc155| binomial coefficient]] we get
>>$$\begin{align}
>> &\frac{n!}{n_{1}!\cancel{ (n-n_{1})! }}\frac{\cancel{ (n-n_{1})! }}{n_{2}!\cancel{ (n-n_{1}-n_{2})! }}\frac{\cancel{ (n-n_{1}-n_{2}) }!}{n_{3}!\cancel{ (n-n_{1}-n_{2}-n_{3}) !}}\dots\frac{\cancel{ (n-n_{1}-n_{2}-\dots-n_{k-1})! }}{n_{k}!\underbrace{ (n-n_{1}-n_{2}-n_{3}-\dots-n_{k}) }_{ =0 }!}\\ 
>> =& \frac{n!}{n_{1}!n_{2}!n_{3}!\dots n_{k}!0!} \\
>> =&\frac{n!}{n_{1}!n_{2}!n_{3}!\dots n_{k}!} \tag*{$\square$} 
>>\end{align}$$
>
>>[!example]
>>How many permutations exist of the letters in the word "MISSISSIPPI"?
>>>[!example] Solution
>>> First we denote the multiset derived from the letters in the word MISSISSIPPI as
>>> $$S = \{ 1 \cdot M, 4 \cdot I, 4 \cdot S, 2 \cdot P \}$$
>>> Applying the theorem we have
>>> $$\begin{align}
>>> n &= 11 \\
>>> \frac{n!}{n_{1}!n_{2}!n_{3}!n_{4}!} &= \frac{11!}{1!\cdot 4!\cdot 4!\cdot 2!} \\
>>> &= \frac{39\;916\;800}{1\;152} \\
>>> &= 34\;650
>>>\end{align}$$
>
>>[!example]
>>How many possibilities are there for 8 non-attacking rooks on an 8-by-8 chessboard?
>>![[Figures/rook_example.png| center]]
>>>[!example]- Solution
>>>Lets denote a square on the board as $(i,j)$ with $i$ denoting a row and $j$ a column and $1 \leq i,j \leq 8$. Since rooks attack each other if they are on the same row or column, we know that a rook must be placed on each row and column. Lets first fix the position of the rows, i.e.
>>>$$(1, j_{1}), (2, j_{2}), \dots, (8, j_{8})$$
>>>To find all possible configurations of non-attacking rooks, we require all $j$ to be distinct, hence the $j$ form a permutation over the set $\{ 1,2,\dots ,8 \}$, which can be given as
>>>$$P(8,8)=8! = 40\;320$$
>>
>>Now assume the rooks are distinguishable, hence, each rook has a different color.
>>>[!example]- Solution
>>>Assuming each rook has a different color means, that for any of the squares a different rook can be chosen. Hence, given one solution for the non-attacking rook problem, we can choose for 8 squares from 8 different rooks, which is
>>>$$P(8,8) = 8! =  40\;320$$
>>>Since there are $8!$ different possible configurations where we can place the 8 different rooks distinctly, we have by the multiplication principle
>>>$$8!\cdot 8! =  40\;320^2 = 1\;625\;702\;400$$
>>
>>Suppose the rooks are partitioned into the following set of colors
>>- 1 red rook (R)
>>- 3 blue rooks (B)
>>- 4 yellow rooks (Y)
>>
>>>[!example]- Solution
>>>As in the previous example the number of rook placements is given by $8!$, now we ask again, given a certain placement solution for the non-attacking rook problem, how can we place the rooks of the multiset
>>>$$S = \{ 1 \cdot R, 3 \cdot B, 4 \cdot Y \}$$
>>>This can easily be solved using the introduced theorem
>>>$$\begin{align}
>>> \frac{n!}{n_{1}!n_{2}!n_{3}!} &= \frac{8!}{1 \cdot 3! \cdot 4!} \\
>>> &= 280
>>>\end{align}$$
>>>Again, we have to consider this for each of the $8!$ configurations, hence, by the multiplication principle we get
>>>$$8! \cdot 280 = 11\,289\,600$$

^0a387a

## Combination of Multisets

>[!theorem] Theorem ([[../../../PDFs/brualdi2004.pdf#page=83|Source]])
> Let $S$ be a multiset with objects of $k$ types, each with an infinite repetition number. Then the number of $r$-combinations of $S$ equals
> $$\binom{r+k-1}{r} = \binom{r+k-1}{k-1}$$
>>[!proof]
>>Let $S$ denote the multiset with $k$ different objects, i.e.
>>$$S = \{ \infty \cdot a_{1}, \infty \cdot a_{2}, \dots, \infty \cdot a_{k} \}$$
>>Any $r$-combination therefore will be a set
>>$$\{ x_{1}\cdot a_{1}, x_{2} \cdot a_{2}, \dots, x_{k} \cdot a_{k} \}$$
>>where $x_{1} \geq 0$ are integers. Note, that any selection of $x_1, x_2,\dots, x_{k}$ with
>>$$x_{1}+ x_{2}+ \dots+ x_{k} = r \tag{1}$$
>>represents an $r$-combination. Let $T$ denote a multiset of zeros and ones with
>>$$T = \{ r \cdot 1, (k-1) \cdot 0 \}$$
>>We want to show, that the combination of a multiset is equal to the permutation of $T$. Note, by equation $(1)$ we can separate the 1's by the (k-1) 0's, i.e.
>>$$\underbrace{ 11\dots 1 }_{ x_{1} \text{ times} }0\underbrace{ 11\dots 1 }_{ x_{2} \text{ times} }0\underbrace{ 1\dots 11 }_{ x_{k-1} \text{ times} }0\underbrace{ 1\dots11 }_{ x_{k} \text{ times} }$$
>>Note, there are exactly $(k-1)$ 0's between the one's. Further note, all $x_i$ can have different values with the condition that $\sum_{i=1}^k x_{i} = r$. 
>>>[!example]
>>>Let $T=\{ 5 \cdot 1, 3 \cdot 0 \}$, then possible permutations can be given as
>>>$$\begin{align} 
>>> &11010101  \\
>>> &11111000 \\
>>> & 10101101 \\
>>> & \dots
>>>\end{align}$$
>>
>>Hence, the multiset permutations of $T$ can be calculated as according to the [[#^0a387a| solution theorem for finite multiset permutations]]
>>$$\frac{(r+k-1)!}{r!(k-1)!} = \binom{r+k-1}{r}$$