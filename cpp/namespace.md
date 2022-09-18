# namespace

`std::cin` where **::** is the scope operator, this means the compiler should look in the scope of left-hand operator for the name of the right-hand operand. we want to use cin from the namespace std.

## How to create a new namespace

max.h

```cpp
namespace newnamespace
{
    int a=3;
    int Max(int n1, int n2){return n1<n2?n2:n1;}
}
```

min.h

```cpp
namespace newnamespace
{
    int a=3;  // error: redefinition of 'int newnamespace::a'
    int Min(int n1, int n2){return n1>n2?n2:n1;}
}
```

main.cpp

```cpp
#include <iostream>
#include "min.h"
#include "max.h"

using namespace newnamespace;
using namespace std;

int main()
{
    cout << Max(1,2)<<endl;
    cout << Min(1,2)<<endl;
    cout << a <<endl;
}
```

## How

using declaration allow us use a name from a namespace without qualifying the names with a namespace_name::prefix

using namespace::name;

## rules

1. a separate using declaration is required for each name

using std::cin;
using std::cout;
using std::endl;

2. Headers should not include using declarations

to avoid unexpected name conflicts

 
