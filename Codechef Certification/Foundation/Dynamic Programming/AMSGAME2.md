# Problem
Chef is playing a game on a sequence of **N** positive integers, say **A<sub>1</sub>, A<sub>2</sub>, ... A<sub>N</sub>**. The game is played as follows.

*   If all the numbers are equal, the game ends.
*   Otherwise
    *   Select two numbers which are unequal
    *   Subtract the smaller number from the larger number
    *   Replace the larger number with the result from above

Chef has already figured out that the game **always terminates**. He also knows, for a given sequence of integers, the game will always terminate on the **same value**, no matter how the game is played. Chef wants you to simulate the game for him and tell him if the game terminates on **1**.

In fact, there may be many such games. Given a sequence of integers Chef wants to know the number of **sub-sequences** of the given sequence, for which, playing the above game on the subsuquence will terminate on **1**. A **sub-sequence** can be obtained from the original sequence by **deleting 0 or more** integers from the original sequence. See the explanation section for clarity.

### Input
The first line of the input contains an integer **T**, the number of test cases. Then follow the description of **T** test cases. The first line of each test case contains a single integer **N**, the length of the sequence. The second line contains **N** positive integers, each separated by a single space.

### Output
For each test case, **output a single integer** - the number of **sub-sequences** of the original sequence, such that, playing the game on the **sub-sequence** results in ending the game with all the values equal to **1**.

### Constraints
- **1 ≤ T ≤ 100**  
- **1 ≤ N ≤ 60**  
- **1 ≤ A<sub>i</sub> ≤ 10<sup>4</sup>**  
- **All A<sub>i</sub> will be distinct.**

### Example
>Input:<br/>
3<br/>
4<br/>
2 3 5 7<br/>
4<br/>
3 4 8 16<br/>
3<br/>
6 10 15<br/>

>Output:<br/>
11<br/>
7<br/>
1<br/><br/>

### Explanation
**Test Case 1:** The following 11 sub-sequences are counted.

*   { 2, 3 }
*   { 2, 5 }
*   { 2, 7 }
*   { 3, 5 }
*   { 3, 7 }
*   { 5, 7 }
*   { 2, 3, 5 }
*   { 2, 3, 7 }
*   { 2, 5, 7 }
*   { 3, 5, 7 }
*   { 2, 3, 5, 7 }

**Test Case 2:** The following 7 sub-sequences are counted.

*   { 3, 4 }
*   { 3, 8 }
*   { 3, 16 }
*   { 3, 4, 8 }
*   { 3, 4, 16 }
*   { 3, 8, 16 }
*   { 3, 4, 8, 16 }

**Test Case 3:** There are 8 subsequences of { 6, 10, 15 }

*   {} => The game cannot be played on this sub-sequence
*   { 6 } => The game cannot be played on this sub-sequence
*   { 10 } => The game cannot be played on this sub-sequence
*   { 15 } => The game cannot be played on this sub-sequence
*   { 6, 10 } => The game cannot end at { 1, 1 }
*   { 6, 15 } => The game cannot end at { 1, 1 }
*   { 10, 15 } => The game cannot end at { 1, 1 }
*   { 6, 10, 15 } => The game ends at { 1, 1, 1 }. Hence this is the only sub-sequence that is counted in the result.

#### `<Problem link>` : <https://www.codechef.com/problems/AMSGAME2>
<br/>
<details>
  <summary>Solution Approach</summary>
  
  ######
  
  Since **N** is only 60, we can use the include exclude recursion with dp to find the answer. The game will terminate at 1 if and only if the gcd of numbers in the subsequence is **1** i.e they are co-prime to each other (proof: Read definition of GCD).
  
  We will recur for all the sub-sequences considering a[i] as the currGcd where (i = 0..n). The base case is when `i==n` then if the `currGcd==1` then we return **1** else **0**. For including the current number we take the gcd of currGcd with a[i] and for excluding the current number we just use the same currGcd and recurr for `n-1` subproblems.
  
  To prevent re-computation we use a 2d array dp[][] to keep track of indices that have been visited with a particular currGcd.
  
  ### References
  
  >https://discuss.codechef.com/problems/AMSGAME2<br/>
  
</details>
