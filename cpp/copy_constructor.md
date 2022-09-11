# Copy Constructor (within class with pointer members)

## Problem

### shallow copy

![image](https://user-images.githubusercontent.com/111368834/189531796-600affd5-cc0e-43be-9154-5c23783190f5.png)

### deep copy

```cpp
#include <cstring>
#include <iostream>

using namespace std;

class String
{
    public:
    String(const char* cstr);
    String(const String& str);
    String& operator= (const String& str);
    ~String();
    char* get_c_str() const {return m_data;}
    
    private:
    char* m_data;
};

inline String::String(const char* cstr = 0)
{
    if(cstr)
    {
        m_data = new char[strlen(cstr)+1];
        strcpy(m_data, cstr);
    }
    else
    {
        m_data = new char[1];
        *m_data = '\0';
    }
}

inline String::~String()
{
    delete[] m_data;
}

inline String::String(const String& str)
{
    m_data = new char [strlen(str.m_data) + 1];
    strcpy(m_data, str.m_data);
    cout << " copy consructor is called " << endl;
}

int main()
{
    String s1("hello");
    String s2(s1);  // equal String s2 = s1;
                    // copy constructor called
}
```

### Why we need a new type constructor? though we have learned constructor.

    There are some circumstances that need to create a new object fron an existing object.

```cpp
Complex c2(c1);  // Instance c2 with c1

Complex c2 = c1; // is different from "=" operation
```

```cpp
void Func(Complex c1){}  // where object c1 is parameter

int main()
{
    Complex c2;
    Func(c2);  // Complex c1 = c2; see 1
    return 0;
}
```

```cpp
Complex Func()
{
    Complex c(4);
    return c;  // return Complex xxx = c;
}
```

### Note

```cpp
Complex c1, c2;
c2 = c1;  // won't call the copy constructor
```

