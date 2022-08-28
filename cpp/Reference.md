# Reference

## define

Type & nickname = variable name;
  
```cpp  
  int n = 4;
  int &r = n; // Initialize n
```

### Note

the refence is assigned to the first one

## exchange value 😊

```cpp
void swap(int n1, int n2)
{
  int tmp;
  tmp = n1;
  n1 = n2;
  n2 = tmp;
}

int main() {
    int n1 = 2, n2 = 0;
    swap(n1, n2);  // n1 and n2 keep original value
  return 0;
}
```

```cpp
#include <iostream>
using namespace std;

void swap(int* n1, int* n2)  // solution with C using pointer
{
  int tmp;
  tmp = *n1;
  *n1 = *n2;
  *n2 = tmp;
}
    
int main() 
{
    int n1 = 2;
    int n2 = 0;
    swap(&n1, &n2);  // n1 and n2 exchanged value
    cout << "n1 address is " << &n1 << endl;
    cout << sizeof(&n1) << endl;
    return 0;
}
```

```cpp
void swap(int &n1, int &n2)  // solution with C++
{
  int tmp;
  tmp = n1;
  n1 = n2;
  n2 = tmp;
}
    
int main() 
{
    int n1 = 2;
    int n2 = 0;
    swap(n1, n2);  // n1 and n2 exchanged value
  return 0;
}
```

 ## Reference as the return of a function

 ```cpp
 int n = 4;
 int & SetValue() {return n;}
 int main()
 {
    SetValue() = 40;
    cout<<n;
    return 0;
 }
 ```

 ## const reference

 ```cpp
 int n;
 const int & r = n;
```
