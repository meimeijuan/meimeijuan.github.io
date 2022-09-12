# names have scope

`Scope`: the scope of a name is *the part of the program's text* in which that name is visible.

## global scope

the name defined outside a function has global scope.

```cpp
int i=0;  // i has global scope
int main(){}  // main also has global scope
```

```cpp
class complex{};  // class type complex has global scope
```

## block scope

the name is active in the current minimum block.

```cpp
int main()
{
    int sum = 0;  // sum is active in main function
    for (int val = 1; val <= 10; ++val)  // val is active in the for block
    {
        sum += val;
    }
    std::cout << sum << std::endl;  // ok
    
    std::cout << val << std::endl;  // error
    
    return 0;
}
```

## nested scope

the same name is defined in different scope, the current program line will use the nearest one.

```cpp
#include <iostream>

using namespace std;

int reuse = 20;

int main()
{
    cout << reuse << endl;  // use the global one
    int reuse = 10;
    cout << reuse << endl;  // use the 1st local one
    for(reuse = 0; reuse < 1; reuse ++)
    {
        cout << reuse << endl;  // use the local one in for block
    }
    return 0;
}
```
