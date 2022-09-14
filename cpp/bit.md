# bit operator

## overview

Operator | Function | Use
---------|----------|----
`&`      | bitwise **AND**  | expression1 & expression2 
`\|`     | bitwise **OR**   | expression1 | expression2
`~`      | bitwise **NOT**  | ~expression 
`^`      | bitwise **XOR**  | expression1 ^ expression2 
`<<`     | left shift       | expression1 << expression2 
`>>`     | right shift      | expression1 << expression2

___

## set bit and clear bit

```cpp
#include <iostream>
using namespace std;

int main()
{
    unsigned int a= 0b1111 0000;
    cout<<hex<<a<<endl;
    cout<<hex<<sizeof(a)<<endl;
    
    /* set 3rd bit of a */
    a |= (1UL<<3);
    cout<<hex<<a<<endl;
    
    /* clear 5rd bit of a */
    a &= ~(1UL<<5); 
    cout<<hex<<a<<endl;
    
    return 0;
}
```

**output**

```
f0
4
f8
d8
```

## left shift and right shift

## unsigned type : shift is simple and clean

```cpp
#include <iostream>
using namespace std;

int main()
{
    unsigned int a= 0b11110000;
    cout<<hex<<"a:"<<a<<", sizeof(a):"<<sizeof(a)<<endl;
    
    /* left shift 1 bit */
    unsigned int a1 = a<<1;
    cout<<hex<<"a1:"<<a1<<endl;

    /* right shift 1 bit */
    unsigned int a3 = a>>1;
    cout<<hex<<"a3:"<<a3<<endl;
    
    /* left shift 24 bit */
    unsigned int a2 = a<<28;
    cout<<hex<<"a2:"<<a2<<endl;
    
    return 0;
}
```
**output**

```
a:f0, sizeof(a):4
a1:1e0
a3:78
a2:0
```

## signed type : shift is dangeous

```cpp
#include <stdio.h>

int main()
{
    int a= -1;
    printf("a:%d, hex(a):%x, sizeof(a):%d\n",a,a,sizeof(a));
    /* left shift 1 bit */
    int a1 = a<<1;
    printf("a1:%d, hex(a1):%x\n",a1,a1);

    /* right shift 1 bit */
    int a2 = a>>1;
    printf("a2:%d, hex(a2):%x\n",a2,a2);
    
    
    return 0;
}
```

**output**
```
a:-1, hex(a):ffffffff, sizeof(a):4
a1:-2, hex(a1):fffffffe
a2:-1, hex(a2):ffffffff
```