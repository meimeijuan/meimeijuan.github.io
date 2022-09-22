# composition

class complex **has a** class realpart

![class](https://user-images.githubusercontent.com/111368834/191779233-1d08ee68-a8ee-4064-8e9d-530020f8c33c.png)

## memory model

![image](https://user-images.githubusercontent.com/111368834/191778573-7ca5fcb6-21db-4b23-a619-81777474390c.png)


## constructor & destructor

- call constructor from **inner to outer**;
- call destructor from **outer to inner**;

```cpp
#include <iostream>

using namespace std;

class realpart
{
public:
    double re;
    // 1st component constructor is called generating object
    realpart(double re_ = 0) : re(re_) 
    { cout << "Constructor realpart is called " << endl; }

    // 2nd component destructor is called
    ~realpart() { cout << "Destructor realpart is called " << endl; }
};

class complex
{
public:
    class realpart real;
    double im;
    // 2nd container constructor is called generating object
    complex(double im_, double r) : im(im_), real(r) 
    { cout << "Constructor complex is called" << endl; }

    // 1st container destructor is called
    ~complex() { cout << "Destructor complex is called" << endl; }
};

int main()
{
    complex c(1, 2);
    cout << "the value is :" << sizeof(c) << endl;
    return 0;
}
```

**output:**

```cpp
Constructor realpart is called 
Constructor complex is called
the value is :16
Destructor complex is called
Destructor realpart is called
```
