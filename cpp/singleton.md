# Design pattern : singleton 单件模式

## Why need singleton

class can only have one instance.

## What is the singleton

mainly put the constructor into **private**

```cpp
#include <iostream>
using namespace std;

class A
{
public:
    static A &getInstance();
    void setup() {}

private:
    A() { cout << "void called" << endl; } // all constructors are private
    A(const A &rhs) {}
};

A &A::getInstance()
{
    static A a; /* 1.a must be static
                   2.implicitly call A::A(){} */
    return a;
}

int main()
{
    A::getInstance().setup(); // correct instance an object via static

    A aa; /* error: 'A::A()' is private within this context,
           the instance can't be created in this way */

    return 0;
}
```
