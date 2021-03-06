# Problem
There is a pile of  n  wooden sticks. The length and weight of each stick
are known in advance. The sticks are to be processed by a woodworking machine
in one by one fashion. It needs some time, called setup time, for the  machine
to  prepare  processing  a  stick.  The  setup  times  are  associated  with
cleaning  operations  and changing tools and shapes in the machine. The setup
times of the woodworking machine are given as follows: 
 
(a) The setup time for the first wooden stick is 1 minute.<br/> 
(b) Right after processing a stick of length  l  and weight  w , the machine will
need no setup time for a stick of length  l'  and weight  w'  if  l ≤ l' and  w ≤ w'. 
Otherwise, it will need 1 minute for setup. 
 
You are to find the minimum setup time to process a given pile of  n  wooden sticks. 
For example, if you have five sticks whose pairs of length and weight are  
( 9 , 4 ) , ( 2 , 5 ) , ( 1 , 2 ) , ( 5 , 3 ) , and ( 4 , 1 ) , then the minimum
setup time should be 2 minutes since there is a sequence of pairs ( 4 , 1 ) , 
( 5 , 3 ) , ( 9 , 4 ) , ( 1 , 2 ) , ( 2 , 5 ) .

### Input
The input consists of T test cases. The number of test cases (T) is given 
in the first line of the input file. Each test case consists of two lines:
 The first line has an integer n , 1 <= n <= 5000 , that represents the number 
of wooden sticks in the test case, and the second line contains 2n positive
integers l1 , w1 , l2 , w2 ,..., ln , wn , each of magnitude at most 10000 ,
where li and wi are the length and weight of the i th wooden stick, respectively.
The 2n integers are delimited by one or more spaces.

>SAMPLE INPUT<br/>
3 <br/>
5 <br/>
4 9 5 2 2 1 3 5 1 4 <br/>
3 <br/>
2 2 1 1 2 2 <br/>
3 <br/>
1 3 2 2 3 1<br/>

### Output
The output should contain the minimum setup time in minutes, one per line. 

>SAMPLE OUTPUT<br/>
2<br/>
1<br/>
3<br/>

#### `<Problem link>` : <https://www.spoj.com/problems/MSTICK/>
<br/>
<details>
  <summary>Solution Approach</summary>
  
  ######
  
  This problem is similar to [MDOLLS](https://rajanjha.codes/code.html?1056) problem. Read the solution approach to it and then come back.
  
  We sort the lengths in decreasing order. The difference is in this problem when length is equal we sort the weights too in decreasing order to maintain the constraint of `l < l'` and  `w < w'` when taking LIS. 
  
  If we have (3, 3), (3, 2), and (3, 1) then sorting in this order will give LIS on weights of **1** which is indeed the time required. 
  
  ### References
  
  >https://rajanjha.codes/code.html?1056<br/>
  
</details>
