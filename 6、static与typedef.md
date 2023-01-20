typedef 重定义
```c
typedef unsigned double u_dle	//将unsigned double 重新定义成u_dle与unsigned double的效果相同
int main()
{
    unsigned double val1 = 3.45;
    u_dle val2 = 3.67;
    printf("%lf\n%lf\n", val1, val2);
    return 0;
}
```
 static静态
可修饰局部变量、修饰全局变量、修饰函数

```c
int main()
{
    int i = 10;
    while (i)
    {
        int j = 1;
        printf("%d \n", j);
        j++;
        i--;
    }
}	//打印结果是10个1

//static 修饰局部变量
int main()
{
    int i = 10;
    while (i)
    {
        static int j = 1;	//局部变量j，只能在循环内部使用，在循环外部将不会存在
        printf("%d ", j);
        j++;
        i--;
    }
}//打印结果从1~10

//static修饰全局变量
//val1.c
int val1 = 10；
static int val2 = 100;
int main()
{
    printf("%d\n%d\n", val1, val2);	//此处将会打印10 100
    return 0;
}
//val2.c
extern int val1;	//此处的extern是用来声明调用外部变量的作用，用来调用val1中的int型变量val1
extern int val2;
int main()
{
    printf("%d\n%d\n", val1, val2);
    return 0;
}	//程序会运行错误，原因是因为val2是satatic修饰过的全局变量，只能用于val1.c中

//static修饰函数
//MAX.c
int MAX(int val1, int val2)	//定义一个int类型的函数函数名为MAX，有两个形参都是int类型val1与val2
{
    return val1 > val2 ? val1 : val2;	/*return是返回一个int类型参数 而exp1 ? exp2 : exp3为三目运算符是将exp1内进行判									  断如果成立将执行exp2，反之执行exp3，最后将结果以int类型返回到主函数中去*/
}
//main.c
#include <stdio.h>

extern int MAX(int val1, int val2); //调用MAX函数
int main()
{
    int a = 10, b = 20;
    int max = MAX(a, b);	/*将主函数内的实际参数传到MAX函数中去，将变量a的值赋给val1，变量b赋值给val2；将函数的运行结果								赋给max*/
    printf("max = %d\n", max);
    return 0;
}
//如果在MAX函数中定义是更改为static int MAX(int val1, int val2)将与static修饰全局变量时相同只能在定义的函数中
```

