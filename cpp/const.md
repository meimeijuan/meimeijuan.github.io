# define a value

const int MAX_VAL = 23;
const double Pi = 3.14;
const char* SCHOOL_NAME = "Peking University";

# define a const pointer

int n, m;
const int* p = &n;

*p = 5; //编译报错
n = 4;
p = &m; //常量指针的指向可以变化

# 函数参数为常量指针时，可避免函数内部不小心改变参数指针所指地方的内容

void MyPrintf(const char* p)
{
    strcpy(p, "this"); //not allowed
    printf("%s", p);   //ok
}
