# delegation: composion by reference

delegation is a class has a pointer pointed to another class

![class](https://user-images.githubusercontent.com/111368834/192310688-e0444053-7925-49c5-9dde-4dcf17e163fd.png)

## details

**User class**

```cpp
class User
{
    public:
    ~User(){}
    User(const User &u){}
    User operater= (const User &u){}
    private:
    Implementation *pImpl; 
};
```
**Implementation class**
```cpp
class Implementation
{};
```
