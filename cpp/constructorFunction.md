## function of construction function

构造函数执行必要的初始化工作，不用再去写初始化函数，并且避免忘记调用初始化函数😉

## name is the same as the class name
## it may have parameters, but no return
## it is mainly used for Initialization,

## the bulid will generate a construct function with no para.

## copy constructor functin

### reference object
X::X( X&) or X::X(const X&)

Complex c1;
Complex c2(c1);

func(Complex c1){}
func(c2);

Complex func()
{
  Complex b(4);
  return b;
}
return
