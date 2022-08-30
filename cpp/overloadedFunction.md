# overloaded function

## What means overloaded function?

same function name, but with different parameter list (parameter type and numbers of parameter)

```cpp
int Max(int n1, int n2);
double Max(double, double);  // overloaded with different parameter type
double Max(double, double, double);  // overloaded with different numbers
double Max(const double, double, double);  // overloaded with different type const

float Max(double, double);  // error: redefined
```

### Note

function call with default arguments may lead to Ambiguity 😃

```cpp
#include <iostream>
using namespace std;

int Sum(int n1, int n2)
{
    return n1 + n2;
}

int Sum(int n1, int n2, int n3 = 0)
{
    return n1 + n2 + n3;
}
int main()
{
    cout << Sum(3, 4) << endl;  // error: call of overloaded 'Sum(int, int)' is ambiguous
    return 0;
}
```
