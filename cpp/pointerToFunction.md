# pointer to function

## How to define a pointer that pointed to a function

```cpp
#include <iostream>
using namespace std;

int Max(int a, int b)
{
    return (a > b) ? a : b;
}

int main()
{
    int (*pFunc)(int a, int b);  // define a function pointer
    pFunc = Max;  // initialize a function pointer
    cout << "the Max. one is " << pFunc(3, 4) << endl;  // 1st method call a function pointer
    cout << "the Max. one is " << (*pFunc)(3, 4) << endl;  // 2nd method to call a function pointer

    cout << "the Max. one is " << *pFunc(3, 4) << endl;  // error: invalid type argument of unary '*' (have 'int')
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;

int Max(int a, int b)
{
    return (a > b) ? a : b;
}

int Min(int a, int b)
{
    return (a < b) ? a : b;
}

int main()
{
    typedef int (*pFuncType)(int a, int b);  // define a new type
    pFuncType pFunc = Max;  // initialize a function pointer
    cout << "the Max. one is " << pFunc(3, 4) << endl;  // call a function pointer

    pFunc = Min;  // pFunc can be pointed to another function Min
    cout << "the Min. one is " << pFunc(3, 4) << endl;  // call a function pointer
    return 0;
}
```

## Situation where needs this function pointer

### act as a function pointer parameter of a function
[qsort](https://cplusplus.com/reference/cstdlib/qsort/?kw=qsort)

```cpp
void qsort (void* base, size_t num, size_t size,
            int (*compar)(const void*,const void*));
```

```cpp
/* qsort example */
#include <stdio.h>      /* printf */
#include <stdlib.h>     /* qsort */

int values[] = { 40, 10, 100, 90, 20, 25 };

int compare (const void * a, const void * b)
{
  return ( *(int*)a - *(int*)b );
}

int main ()
{
  int n;
  qsort (values, 6, sizeof(int), compare);  // int (*compar)(const void*,const void*) = compare
  for (n=0; n<6; n++)
     printf ("%d ",values[n]);
  return 0;
}
```

## see also 

<c++ primer> chapter 6.7 pointer to functions
