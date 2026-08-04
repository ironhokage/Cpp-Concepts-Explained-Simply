>[!IMPORTANT]
> By only **reading** this article you **WILL NOT** fully learn and remember the information presented here, to truly learn and retain what it is said in here, you have to **read**, then **make** a small piece of **code** that uses what you learned, **preferably without looking** at this documents information, if you are stuck, you should and are advised to look, and by **repeating** this cycle over a period of time you will truly **learn** and **understand**

## What is Backtracking?
It is a **class** of algorithms, a programming **method** used to solve different types problems that admit partial answers. 

It finds the results in an incremental manner, by using recursion as the back bone of the system.

As a visual representation think of **backtracking** as a **tree** with **branches** and **leaves**.

## Why do we use Backtracking?
 It is used when the problem lets us have "partial solutions" and if the test size is small enough and also ordered, this method is useless for big sets of unordered numbers. 

The core of backtracking is handing to the algorithm a set of known data(numbers, strings, etc), and finding the answer to a question that uses those values.

## How does it work?
I said above to think of it as a tree, this is a visual representation to help you understand but it is also how this method works.

We start at a root, lets say a base condition for example `n==0`, now we will do something called **depth first search ([DFS](/Graphs/DFS))**, this, as the name implies, goes in depth , down from the root to the leaves. 

Each leaf is a possible answer, if the leaf has a correct answer or it doesn't have a optimal one, the algorithm backtracks, it goes back to a earlier state to try another branch, it does this until all results are found.

As each correct result is found it is added to a solution vector `v[] = {v[1], v[2], ... , v[n]}`. 
Each element from the solution vector belongs to a set A, this set A is finite and ordered.

## Step by step implementation:

### Conceptual:

The `v[]` vector gets computed staring from one until n with the step of k, the current element of the vector gets computed in the following manner:

1. Element `v[k]` gets the values from the set A<sub>k</sub> in a linear order.
2. Each value is compared to `v[1], v[2], ... , v[k-1]` (i think it finishes at k-1 because k its the final value) and there are 2 scenarios that can happen:
	1. The value is "bad" and we continue checking, if all values are "bad" we backtrack, we do this because we might find a "good" value after the "bad" one.
<<<<<<< HEAD
	2. If the value is good, we add it to the vector and continue until we reach the end of that branch, then we backtrack
=======
>>>>>>> origin/main



## Sources:

https://www.pbinfo.ro/articole/16597/metoda-backtracking#intlink-4
https://en.wikipedia.org/wiki/Backtracking