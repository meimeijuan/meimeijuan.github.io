# const Qualifier

## define a variable whose value can not be changed

```cpp
#include <iostream>
using namespace std;

int main() 
{
    const double Pi = 3.14;
    const int bufSize = 512;
    const char* SCHOOL_NAME = "Peking University";
    
    Pi = 4.0;  // error: assignment of read-only variable 'Pi'
    const int bufSizeError;  // error: uninitialized const 'bufSizeError' [-fpermissive]
    
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;

int main() 
{
    int cnt = 0;
    const int sz = cnt;
    cout << "Success" << endl;
    ++cnt ;  // ok
    ++sz;  // error: increment of read-only variable 'sz'
    return 0;
}
```
## define a const pointer

```cpp
#include <iostream>

int main() 
{
    int n, m;
    const int* p = &n;
    // *p = 5; // error: assignment of read-only location '* p'
    return 0;
}
```

```cpp
#include <iostream>

int main() 
{
    int n, m;
    const int* p = &n;
    n = 4;
    std::cout << "*p is " << *p << std::endl;
    p = &m; // this time p is pointed to m's address, even if p is a const pointer.
    std::cout << "*p is " << *p << std::endl;

    return 0;
}
```

```cpp
#include <iostream>

int main() 
{
    const double pi = 3.14;
    const double *const pip = &pi;  // the 1st const is Low-levle const, the 2nd one is Top-level const.
    *pip = 2.72; // error: assignment of read-only location '*(const double*)pip'
                 // the low-level const means the content of (the pointer pip pointed to) can't be changed.
    double p1;
    pip = &p1;  // error: assignment of read-only variable 'pip'
                // the top-level const means the pointet pip itself is a const.
    return 0;
}
```

## the const pointer is a parameter of a function, can aviod changing the origin content of the address

```cpp
void MyPrintf(const char* p)
{
    strcpy(p, "this"); // not allowed
    printf("%s", p);   // ok
}
```

## Reference to const

```cpp
#include <iostream>

int main() 
{
    int ci = 1024;
    const int &r1 = ci;  
    r1 = 1024;  // error: assignment of read-only reference 'r1'

    const int ci2 = 1024;
    int &r2 = ci2;  // error: binding reference of type 'int&' to 'const int' discards qualifiers


    return 0;
}
```

```cpp
#include <iostream>

int main() 
{
    int i = 42;
    int &r1 = i;
    const int &r2 = i;
    r1 = 0;
    std::cout << "r2 is " << r2 << std::endl;  // 0, because the value can be changed via the referenced object

    return 0;
}
```
