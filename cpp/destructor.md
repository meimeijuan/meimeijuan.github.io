# destructor

## clean up resource in destructor

**if there are any new operation**

```cpp
#include <cstring>
#include <iostream>

using namespace std;

class String
{
public:
    String(const char *cstr = 0);
    String(const String &str);
    String &operator=(const String &str);
    ~String();
    char *get_c_str() const { return m_data; }

private:
    char *m_data;
};

inline String::String(const char *cstr)
{
    if (cstr)
    {
        m_data = new char[strlen(cstr) + 1];
        strcpy(m_data, cstr);
    }
    else
    {
        m_data = new char[1];
        *m_data = '\0';
    }
}

inline String::~String()  // destructor
{
    delete[] m_data;  // clean up resource (eg. memory in heap, opened file)
    cout << "destructor is called " << endl;
}

int main()
{
    String s1;  // not recommend this instance method s1();, for no respective assemably code will generate
    String s2("hello");

    String *p = new String("hello");  // String("hello") a anonimus object in heap
    delete p;
}
```

**Output :**

```
destructor is called 
destructor is called
destructor is called
```
