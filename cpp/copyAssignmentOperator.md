# copy assignment operator

## 

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
    cout << "copy consructor is called" << endl;
}

inline String& String::operator=(const String& str)
{
    // 1st check if it is self assignment
    if(this == &str)
    {return *this;}
    // 2nd delete old data
    delete[] m_data;
    // 3rd apply new memory
    m_data = new char[strlen(str.m_data)+1];
    // 4th copy to new memory
    strcpy(m_data, str.m_data);

    cout << "copy assignment is called" << endl;
}

int main()
{
    String s1("hello");
    String s2(s1);  // copy consructor is called
    s2 = s1;  // op=
}
```

## self assignment is needed

![image](https://user-images.githubusercontent.com/111368834/189531635-3deca626-e4af-4012-8b0b-a0e9c5645133.png)


