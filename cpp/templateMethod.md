# template method

![image](https://user-images.githubusercontent.com/111368834/194761437-7b6770b1-0feb-42b4-83b3-f76bcd76af0f.png)

Reference: https://refactoring.guru/design-patterns/template-method

## code instance

```cpp
#include <iostream>
using namespace std;

class CDocument {
   public:
    // OnFileOpen() is the Template Method
    void OnFileOpen() {
        cout << "open file" << endl;
        Serialize();       // this step will be overrided by derived class
        cout << "close file" << endl;
    }

    virtual void Serialize() {}
};

class CMyDoc : public CDocument {
   public:
    virtual void Serialize() 
    { cout << "CMyDoc::Serialize() called" << endl; }
};

int main() {
    CMyDoc myDoc;
    myDoc.OnFileOpen();

    return 0;
}
```
