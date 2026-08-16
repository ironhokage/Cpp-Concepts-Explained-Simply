>[!IMPORTANT]
> By only **reading** this article you **WILL NOT** fully learn and remember the information presented here, to truly learn and retain what it is said in here, you have to **read**, then **make** a small piece of **code** that uses what you learned, **preferably without looking** at this documents information, if you are stuck, you should and are advised to look, and by **repeating** this cycle over a period of time you will truly **learn** and **understand**

## <u>Operators sheet:</u>

It is the same operator that pointers use for getting the address of a variable, meaning `&`, the ampersand, if you don't know what a pointer is or how it works, please refer to [Pointers](./Pointers.md). 

## <u>Definition:</u>

A reference works like a **pointer**, it stores the address of a value in memory, but unlike a pointer it cannot be changed after declaration and it can't be dereferenced, you can't get the numerical value from it. It also cannot be set to null.

The only "numerical value" you can get from a reference is the memory address value, i have put between quotes because you don't get a value like 20, or 50 or a string and so on. 

There are two kinds of references:
1. *Lvalue* references
2. *Rvalue* references

## Lvalue references

Named variables that are references are named `Lvalue` references. These exist as declared variables in the code base. 

`Lvalue` references use the `&` sign.

**Analogy:** You can think of an `Lvalue` reference as another name for an object, like a nickname someone has.

**Example:** 

```cpp
#include<iostream>

int main()
{
	int lValue = 10;
	int &lValueRef = lValue;
	
	std::cout << &lValueRef << endl;

	return 0;
}

```
 
## Rvalue references

`Rvalue` references use the `&&` sign.

## Sources:
- https://learn.microsoft.com/en-us/cpp/cpp/lvalue-reference-declarator-amp?view=msvc-170
- https://learn.microsoft.com/en-us/cpp/cpp/references-cpp?view=msvc-170
- 
