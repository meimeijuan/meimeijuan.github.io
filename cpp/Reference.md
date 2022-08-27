# Reference

## define
  Type & nickname = variable name;
```cpp  
  int n = 4;
  int &r = n; Initialize n
```

## the refence is assigned to the first one

## exchange value 😊

```cpp
    void swap(int a, int b)
    {
      int tmp;
      tmp = a;
      a = b;
      b = tmp;
    }
    
    int n1,n2;
    swap(n1, n2);  // n1 and n2 keep original value
    
    void swap(int* a, int* b)  // solution with C using pointer
    {
      int tmp;
      tmp = *a;
      *a = *b;
      *b = tmp;
    }
    int n1, n2;
    swap(&n1, &n2);
    
    void swap(int &a, int &b)  // solution with C++
    {
      int tmp;
      tmp = a;
      a = b;
      b = tmp;
    }
    int n1,n2;
    swap(n1, n2);  // n1 and n2 exchanged value 
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
