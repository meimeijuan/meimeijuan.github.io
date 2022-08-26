# problem 

理解难 修改难 查错难 重用难

# object oriented program

absract + wrap 
class
数据结构 + 函数

class classname
{
    public:
    int w, h;
    void Init(int w_, int h_)
    {
        w = w_;
        h = h_;
    }
    int Area()
    {
        return w*h;
    }
    int Perimeter()
    {
        return 2(w +h);
    }
};

classname r;  //r是一个对象，即类的实例

## 访问方式1
r.w = 5;
r.Init(3, 4);

## 访问方式2
classname *p1 = r;
p1->w = 5;

## 访问方式3 reference 
classname & rr = r;
rr.w = 5;

## 成员函数方式2

int classname::Aera()
{
    return w*h;
}

instance/instance pointer/instance reference
