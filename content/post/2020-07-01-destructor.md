---
title: Blog 3 - Understanding Destructors in C++
subtitle: Managing Object Destruction and Resource Cleanup
date: 2023-07-01
tags: ["C++","BackToBasics","OOP"]
---

In the world of C++, constructors and destructors play crucial roles in managing objects' lifecycle. While constructors are responsible for initializing objects, destructors come into action when objects are destroyed. In this blog post, we'll delve into the significance of destructors, their usage, and how they ensure proper resource cleanup. So let's explore the world of C++ destructors!

<!--more-->

## What are `Destructors` ?

In C++, a destructor is a special member function that gets invoked automatically when an object is destroyed. It's called upon object destruction, ensuring that necessary cleanup operations are performed before the memory occupied by the object is released.

## Triggering Destructor Invocation

- Stack-Allocation: If an object is stack-allocated, its destructor will be automatically called when the object goes out of scope. The scope could be a function or any block enclosed by curly braces.
- Heap-Allocation: For objects allocated on the heap using the `new` keyword, it's essential to manually invoke the destructor by calling `delete`. This ensures that the destructor is executed, releasing the allocated memory.

## Destructor's Role in Resource Cleanup: 
The primary purpose of a destructor is to release any resources associated with the object. This includes deallocating dynamically allocated memory, closing files or database connections, releasing locks, or any other cleanup activities required by the object. By properly implementing destructors, we can prevent memory leaks and ensure the efficient utilization of system resources.

## Example of a Class with a Destructor:

Let's take a look at an example class, `Entity`, which demonstrates the usage of a destructor.

```cpp
#include <iostream>

class Entity {
public:
    float X, Y;

    Entity() {
        X = 0.0f;
        Y = 0.0f;
        std::cout << "Created Entity!" << std::endl;
    }

    ~Entity() {
        std::cout << "Destroyed Entity!" << std::endl;
    }

    void Print() {
        std::cout << X << ", " << Y << std::endl;
    }
};

void Function() {
    Entity e;
    e.Print();
}

int main() {
    Function();
    return 0;
}
```
In this example, when the `main` function is executed, it invokes the `Function` which creates an object of the `Entity` class. The constructor is called upon object creation and initializes the `X` and `Y` variables. Finally, when the `main` function exits, the object goes out of scope, resulting in the destructor being automatically invoked.

The output will be:

```bash
Created Entity!
0, 0
Destroyed Entity!
```

## Manual Destructor Invocation: 
While destructors are usually called automatically, it's also possible to explicitly invoke a destructor using the destructor's name preceded by the object instance, like `e.~Entity();`. However, manually invoking destructors is uncommon and generally not recommended in normal scenarios.

## Importance of Destructors: 
Destructors are crucial for proper resource management in C++. They ensure that any resources acquired during object initialization are released, preventing memory leaks and other resource-related issues. By implementing destructors correctly, you can maintain a clean and efficient codebase.

## Conclusion: 
Understanding destructors is essential for managing object destruction and resource cleanup in C++. By leveraging destructors effectively, you can ensure proper memory management and prevent resource leaks. With the knowledge gained from this blog post, you'll be equipped to write robust C++ code and make informed decisions when it comes to object destruction and cleanup. Happy coding!