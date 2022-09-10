# pass parameter

## by value vs by reference

**principle**

1. built-in type pass by value (int, double,...)
2. others pass by reference

## direction of pass parameter

### In parameter

```cpp
int sum(int a, int b) // where a and b are In parameters, they are right value - read only
{
    return a + b;
}
```

### Out parameter

```cpp
int divide(double a, double b, double &c) // a,b are In parameter, c is Out parameter
{
    if(b==0) 
    { return -1; // error: divide 0}
    else{
    c = a / b;
    returb 0; // success
    }
}

int sum;
sun(1,2,sum);

```

### In-Out parameter

```cpp
void swap(int &n1, int &n2)  // n1, n2 is a In-Out parameter
{
    int temp = n1;
    n1 = n2;
    n2 = temp;
}
```
