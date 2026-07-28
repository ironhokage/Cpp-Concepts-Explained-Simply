>[!IMPORTANT]
> By only **reading** this article you **WILL NOT** fully learn and remember the information presented here, to truly learn and retain what it is said in here, you have to **read**, then **make** a small piece of **code** that uses what you learned, **preferably without looking** at this documents information, if you are stuck, you should and are advised to look, and by **repeating** this cycle over a period of time you will truly **learn** and **understand**

## What is D&C ?

**Divide et Impera**, **Divide and Conquer** or **D&C** however you want to call it, it is a **programming method** that works by following a very simple principle:

- We firstly take a problem and split it into two (or more) sub-problems so we have smaller and easier to compute problems.
- The sub-problems have to be of the same type as the initial one, just a smaller size, meaning, if we need a int, the sub-problems can only be of type int, nothing else.
- Additionally the sub-problems have to be solved in the same way as the main problem.
- Then each sub-problem is solved independently of the main, root problem.
- After each sub problem finished and got a result we will combine the results of each into the final result for the initial problem

In D&C there are three types of problems:
1. The main problem that we start with
2. The sub-problems
3. The "best case" problem

The **"best case"** problem is a special type of sub - problem, that is small enough so we don't need to split it into further sub-problems, its like the easiest problem that has to be solved.


## Rules for writing D&C problems in code:
- When writing a D&C function we **MUST** always use `st == dr` (or however you named your variables for left side and right side)
- NEVER forget to use **r1** and **r2** in the else case( adding, them or lets say `r1 || r2`, etc)


## Tips and tricks for D&C problems:
- When the problem looks at only **ONE** number at a time we do a check for what we are looking for in the `st == dr` (it is also called leaf). 
- When the problem has to compare **TWO** numbers that might be in different halves of the problem we need to do the check at the composition part.
- When using `r1` and `r2`, these can be made to give the final result themselves (`return r1 + r2` or `return r1 || r2`) or they can be used as PART of the decision when filtering to give the final result (`if(r1 == 1 && r2 == 1) return 1 else return 0`, etc).
- When doing sums in the base case you need to return `n[st]`, n being the vector of numbers and st being the first element
- For programs or exercises that require the use of vectors or matrices, the implementation is very similar, the only difference being the need of a for loop in the leaf

## Advantages of Divide and Conquer Algorithm:
- **Speed & Algorithm Efficiency:**
- **Parallelism:**

## Disadvantages of Divide and Conquer Algorithm:
- **Overhead:**

## Code Examples:

**Example 1:** 

``` cpp
#include <iostream>
#include <cmath> // For sqrt() function
using namespace std;

/**
 * Function: ExistsPrimeDivOdd (Original name)
 *
 * Purpose: Recursively checks if there is at least ONE prime number 
 *          in the array segment from index 'st' to 'dt'.
 * 
 * Parameters:
 *   arr[] - the array of integers
 *   left  - the leftmost index of the current segment (starting at 1)
 *   right - the rightmost index of the current segment
 * 
 * Returns:
 *   1 (true)  - if a prime number exists in this segment
 *   0 (false) - if NO prime number exists in this segment
 */
int ExistsPrimeDivOdd(int arr[], int left, int right)
{
    // ----- BASE CASE: Only ONE element in this segment -----
    if (left == right)
    {
        // Step 1: Numbers less than 2 are NOT prime (0, 1, negative numbers)
        if (arr[left] < 2) 
            return 0;

        // Step 2: Check if the number is prime
        // We only need to check divisors up to sqrt(n) for efficiency
        for (int divisor = 2; divisor <= sqrt(arr[left]); divisor++)
        {
            // If divisible by any number, it's NOT prime
            if (arr[left] % divisor == 0) 
                return 0;
        }

        // If we passed the loop, the number has no divisors -> it IS prime
        return 1;
    }
    // ----- RECURSIVE CASE: More than one element -----
    else
    {
        // Step 3: Split the segment into two halves (Divide & Conquer)
        int mid = (left + right) / 2;

        // Step 4: Recursively check the LEFT half
        // Step 5: Recursively check the RIGHT half
        // Step 6: Combine results using LOGICAL OR (||)
        // 
        // Why OR? We only need ONE prime number in the ENTIRE array.
        // If the left half has a prime -> we don't even need to check the right half
        // (Short-circuit evaluation saves time!)
        return ExistsPrimeDivOdd(arr, left, mid) || 
               ExistsPrimeDivOdd(arr, mid + 1, right);
    }
}

int main()
{
    int count;          // The number of elements we will read
    int array[201];     // Array with capacity for 201 elements (indices 1 to 200)

    // Read the number of elements from the user
    cin >> count;

    // Read the array elements one by one (using 1-based indexing, 
    // so we start at index 1 and go up to 'count')
    for (int i = 1; i <= count; i++)
        cin >> array[i];

    // Call the recursive function on the entire array (from index 1 to count)
    // If the result is 0 (false), print "NO" (no prime exists)
    // Otherwise (1/true), print "YES" (at least one prime exists)
    if (ExistsPrimeDivOdd(array, 1, count) == 0)
        cout << "NO";
    else
        cout << "YES";

    return 0;
}
```

**Example 2:**

``` cpp
#include <iostream>
using namespace std;

// Function to count odd numbers in an array using divide and conquer (recursion)
// Parameters:
//   arr[] - the array of integers
//   left  - the leftmost index of the current segment
//   right - the rightmost index of the current segment
int CountOdd(int arr[], int left, int right)
{
    // Base case: only one element in this segment
    if (left == right)
    {
        // Check if the single element is odd
        if (arr[left] % 2 == 1) 
            return 1;   // It is odd, count it
        else 
            return 0;   // It is even, don't count it
    }
    else
    {
        // Recursive case: split the array into two halves
        int mid = (left + right) / 2;
        
        // Count odds in the left half
        int leftResult = CountOdd(arr, left, mid);
        
        // Count odds in the right half
        int rightResult = CountOdd(arr, mid + 1, right);
        
        // Return the total sum
        return leftResult + rightResult;
    }
}

int main()
{
    int count, elements[1001];
    
    // Read the number of elements
    cin >> count;
    
    // Read the array elements (using 1-based indexing, as in the original)
    for (int i = 1; i <= count; i++)
        cin >> elements[i];
    
    // Call the recursive function and display the result
    cout << CountOdd(elements, 1, count);

    return 0;
}
```

## <ins>Sources used</ins>:
- https://www.geeksforgeeks.org/dsa/introduction-to-divide-and-conquer-algorithm/
- https://www.pbinfo.ro/articole/7651/divide-et-impera
- https://www.pbinfo.ro/probleme/1149/existaprimedivimp
- https://www.pbinfo.ro/probleme/1018/cntimpare