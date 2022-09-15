# function template

## function template original view

```cpp
#include <iostream>
using namespace std;

template<typename T>   // define a type T

const T& min(T& a, T& b)
{
  return b<a?b:a;
}


int main() 
{
  cout<< min(1,2) <<endl;
  cout<< min(1.0,2.1) << endl;
  return 0;
}
```

## compiler view

```cpp
#include <iostream>
using namespace std;

template<typename T>
const T & min(T & a, T & b)
{
  return operator<(b, a) ? b : a;
}



int main()
{
  std::cout.operator<<(std::min(1, 2)).operator<<(std::endl);  // argument deduction, through 
  std::cout.operator<<(std::min(1.0, 2.1000000000000001)).operator<<(std::endl);
  return 0;
}

```
