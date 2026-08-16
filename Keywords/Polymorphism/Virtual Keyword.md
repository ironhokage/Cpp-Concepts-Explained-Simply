>[!IMPORTANT]
> By only **reading** this article you **WILL NOT** fully learn and remember the information presented here, to truly learn and retain what it is said in here, you have to **read**, then **make** a small piece of **code** that uses what you learned, **preferably without looking** at this documents information, if you are stuck, you should and are advised to look, and by **repeating** this cycle over a period of time you will truly **learn** and **understand**

## Declaration and usages:

``` cpp
class Base
{
   virtual void PrintMessage()
   {
	   std::cout << "First message" ;
   }
   virtual void Calculate(int a, int b)
   {
	   std::cout << a + b ;
   }
};

class Derived : public Base
{
    void Calculate(int a, int b)
    {
	    std::cout << a * b ;
    }
    
    void PrintMessage()
    {
	    std::cout << "Second Message" ;
    }
};
```

## What is a virtual function? 

A `virtual function` is a function that belongs to a base class/is declaed within a base class which can be overridden, its implementation can be modified, in a class that derives from the base one

## The main benefits of this keyword are :

- Letting the derived classes changed how the base classes functions behave, essentially customising the behaviour of the base classes functions.
- Forms the base of `polymorphism` in C++.

## Rules for Virtual Functions:

1. We are putting the `virtual` keyword in before the functions declaration (ex: `virtual void PrintMessage()`);
2. They cannot be static
3. When they are initialised with 0, this means they don't have any base implementation, the derived classes need provide their own implementation.
4. If the base version is not overridden then the base implementation is used.
5. To use them we need a pointer to the base class or a reference to the base class during runtime.

## Why use virtual functions?

Virtual functions are one of the most important concepts in C++ `polymorphism` as they let us essentially avoid duplicate code, this is (from what i understand so take it with a grain of salt) the main advantage over not using them.

Lets say we have a game, and in that game we need players and enemies, and because both are human, we make a base class named `Humanoid Character`, then we take that class and add some functions, `Walk()`, `Die()`, etc.

Now, we derive the class for player and the one for enemies from the base class `Humanoid Character`. 

In each of the derived classes we can add new functions, we can change, maybe the players can also fly, so in the walk function we can add that when we press a button we fly instead of moving on ground.

By using virtual functions we prevent duplicate code, we don't need or want to write more code than needed, we are developers, not typists, leave the typing job to the printing press.

## Why do we need virtual functions?

Okey so we explained why use them, but some of you maybe are wondering, why do we strictly need the `virtual` keyword and virtual functions, maybe you wonder if there are some alternatives to them.



# Sources:
- https://www.geeksforgeeks.org/cpp/virtual-function-cpp/
- https://stackoverflow.com/questions/2391679/why-do-we-need-virtual-functions-in-c