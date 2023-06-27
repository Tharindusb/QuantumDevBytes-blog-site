---
title: Blog 2 - Understanding Constructors in C++
subtitle: Mastering Object Initialization with Constructors in C++
date: 2023-06-27
tags: ["C++","BackToBasics","OOP"]
---

Constructors play a crucial role in object-oriented programming, particularly in C++. They are special methods that are responsible for initializing objects when they are instantiated. In this blog post, we will explore the concept of constructors, their significance in C++, and how they can be utilized to initialize object members effectively. We will also discuss default constructors, constructors with parameters, and the concept of deleting constructors. Let's dive in!

<!--more-->

## Instantiating Objects and Memory Initialization: 

When an object is instantiated in C++, it is essential to initialize its memory properly. Failure to do so can result in unpredictable behavior. Let's consider the following example code:

```cpp
#include <iostream>

class Entity
{
public:
    float X, Y;
    
    void Print()
    {
        std::cout << X << ", " << Y << std::endl;
    }
};

int main()
{
    Entity e;
    e.Print();
    return 0;
}
```
Output
```
7.26281e-39, 7.26281e-39
```
In this code, we observed that without initializing the memory explicitly, we obtained random values when we printed the object's members using the `Print()` method. This occurs because we did not initialize the memory, and we got whatever was left over in that memory space.

## Introducing Initialization Methods:

To rectify the issue of uninitialized memory, we can introduce an `Init()` method to set the object's members to desired values, such as zero. Consider the modified example code:

```cpp
#include <iostream>

class Entity
{
public:
    float X, Y;
    
    void Print()
    {
        std::cout << X << ", " << Y << std::endl;
    }

    void Init()
    {
        X = 0.0f;
        Y = 0.0f;
    }
};

int main()
{
    Entity e;
    e.Init();
    e.Print();
    return 0;
}
```
output
```
0,0
```
By calling the `Init()` method explicitly after object creation, we ensure that the object's members are initialized to the desired values. However, this approach requires manual intervention every time we create a new `Entity` object.

## Introducing Constructors:

To streamline the initialization process and eliminate the need for separate initialization methods, constructors come into play. Constructors are special methods with the same name as the class, and they are automatically called when an object is created. Let's enhance our example code to include a default constructor:

```cpp
#include <iostream>

class Entity
{
public:
    float X, Y;
    
    Entity()
    {
        X = 0.0f;
        Y = 0.0f;
    }
    
    void Print()
    {
        std::cout << X << ", " << Y << std::endl;
    }
};

int main()
{
    Entity e;
    e.Print();
    return 0;
}
```
In this code, the default constructor `Entity()` is defined, which initializes the `Entity` object's members to zero. Consequently, calling the `Init()` method becomes unnecessary, as the constructor automatically handles the initialization during object creation.

## Constructors with Parameters:

Constructors can also accept parameters, allowing us to initialize object members with specific values during object creation. Let's extend our `Entity` class to include a parameterized constructor:

```cpp
#include <iostream>

class Entity
{
public:
    float X, Y;
    
    Entity(float x, float y)
    {
        X = x;
        Y = y;
    }
    
    void Print()
    {
        std::cout << X << ", " << Y << std::endl;
    }
};

int main()
{
    Entity e(10.0f, 5.05f);
    e.Print();
    return 0;
}
```

In this code, we have added a constructor that takes `float` values for `X` and `Y`. When creating a new `Entity` object, we can pass the desired values directly to the constructor. This feature provides flexibility and convenience, enabling us to set initial values during object instantiation.

## Deleting Constructors:

In some scenarios, it might be desirable to prevent the usage of default constructors. By default, C++ provides a default constructor that takes no parameters. However, we can delete this default constructor to disallow its usage, ensuring that objects can only be created using constructors with parameters. Let's consider the following example:

```cpp
class Log
{
public:
    static void Write()
    {
        // Logging implementation
    }
};

int main()
{
    Log::Write();
    Log l; // Compiling error: attempting to use deleted function
}
```
In this code, the default constructor is deleted using the `delete` syntax, making it inaccessible for object creation. Consequently, attempting to create an object of the `Log` class using the default constructor will result in a compilation error.

## Conclusion:

Constructors are integral to C++ programming, serving as a means to initialize objects effectively. They eliminate the need for separate initialization methods and allow us to set object members conveniently during instantiation. Whether it's the default constructor, constructors with parameters, or the concept of deleting constructors, understanding these concepts empowers us to write cleaner and more efficient code. By leveraging constructors, we can ensure proper object initialization and improve the reliability of our C++ programs.

Remember, constructors don't run if objects are not instantiated. So, make sure to utilize constructors wisely to initialize objects correctly in your C++ projects.

Happy coding!