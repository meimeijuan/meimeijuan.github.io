# the use of keyword const

## define a const value

```cpp
const int MAX_VAL = 23;
const double Pi = 3.14;
const char* SCHOOL_NAME = "Peking University";
```

## define a const pointer

```cpp
int n, m;
const int* p = &n;
*p = 5; //编译报错
n = 4;
p = &m; //常量指针的指向可以变化
```

## the const pointer is a parameter of a function, can aviod changing the origin content of the address

```cpp
void MyPrintf(const char* p)
{
    strcpy(p, "this"); //not allowed
    printf("%s", p);   //ok
}
```
