>[!IMPORTANT]
> By only **reading** this article you **WILL NOT** fully learn and remember the information presented here, to truly learn and retain what it is said in here, you have to **read**, then **make** a small piece of **code** that uses what you learned, **preferably without looking** at this documents information, if you are stuck, you should and are advised to look, and by **repeating** this cycle over a period of time you will truly **learn** and **understand**

## What is recursion?

**Recursion** is a process in which any given function calls itself, be it directly or indirectly, the corresponding function is called a **recursive function**.

### Direct recursion:
**Direct recursion** is the **process** in which **any** given **function** has a function **call to itself** in **itself**

**Analogy:** Lets imagine a dog that chases its own tail, this is how direct recursion works.

**Example:**

```cpp
int largest_even_up_to(int n)
{
	if(n == 0)
		return 0;
	
	if(n % 2 == 0)
		return n;
	return largest_even_up_to(n-1);
}
```

In the example we call the `largest_even_up_to` function in itself.

### Indirect recursion:
If we have two functions, x1 and x2, and x1 calls x2 and x2 calls x1, this process is called **indirect recursion** because it represent a cycle between the two functions.

**Analogy:** Lets say, we have two friends, David and Andrew, and they ask one another what the other said, they will stay in an asking loop, saying "what did you say?".

**Example:**

```cpp
bool is_even(int n) {
    if (n == 0)
        return true;
    return is_odd(n - 1);   // calls is_odd, not itself directly
}
bool is_odd(int n) {
    if (n == 0)
        return false;
    return is_even(n - 1);  // calls is_even back
}
```

In the example the function `is_even` gets called in `is_even` and vice versa,  the function `is_even` gets called in `is_even`.


## Steps when writing an recursive function

- **Step 1 - Define a base case:** The **simplest case** is the **base** one, for example the base case might be `n == 0` like in the examples above, or it could be anything else, depending of your requirements.
	- **Why is it needed?** - The **base** case is needed so we can stop the recursive function from, well, functioning! Without a base case the function would get called until infinity and we don't want to do that

- **Step 2 - Define the recursive case:** The case that needs to be repeated over and over until the base case is met. To define it you have to split the problem into smaller, more manageable parts, that are smaller versions of the original problem, in the examples above we split the problem by doing `n-1` when adding it as a parameter in the function call.
- **Step 3 - Make sure the recursion ends:** This is more of a verification that when doing the steps above the recursion can reach the base case, if it doesn't reach, check if the problem is broken up into smaller pieces.
- **Step 4 - Solution:** Combine the results of the sub-problems to solve the original question.


## Common usages of recursion:
>[!IMPORTANT] 
>This **ISN'T** complete, I will add more as I learn more, I don't want to add things i haven't learned about yet or don't fully understand yet. As my understanding grows so will this list and any list like it will.


1. [Backtracking](./Backtracking.md)
2. [Divide and Conquer](./Divide-and-Conquer.md)

## Sources:
- https://www.geeksforgeeks.org/dsa/introduction-to-recursion-2/
- https://www.pbinfo.ro/articole/3873/recursivitate