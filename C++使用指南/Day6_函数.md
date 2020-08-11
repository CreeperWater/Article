# Day6 函数
- 从概念角度：函数是一段具有特定功能的、按固定顺序执行的、可重用语句块
- 从使用角度：函数是一个黑盒。使用时，只需了解“函数名称、输入数据、输出结果、实现功能”等信息，不必关心具体的设计方法。
- 从程序角度：程序是函数集合体，每个函数都是一个独立模块。
## 函数的声明、定义和调用
```c++
返回值类型 函数名(形参列表){
    //函数体
}
```
- 函数名：有意义的标识符，详细的命名规则请复习变量命名规则。
- 形式参数列表：用逗号分隔的<数据类型><形参名称>对，说明参数数量、顺序和类型。函数没有形参时，函数名 f 后的括号内容为空或void，即f( ) 或 f(void)。
- 返回值类型：是被调函数向主调函数返回值的数据类型，一般和return语句返回值的类型相同。如果函数没有返回值，则设置为void。

例如
```c++
#include<iostream>
using namespace std;
long long fab(int);//函数的声明
int main(){
    int n;
    cin>>n;
    cout<<fab(n); //函数的调用
    return 0;
}
//函数的定义
long long fab(int x){
    long long ans=1;
    for(int i=2;i<=x;i++) ans*=i;
    return ans;
}
```
在OI中，也常常采用一种偷懒的做法，即同时进行声明和定义
```c++
#include<iostream>
using namespace std;
//函数的定义
long long fab(int x){
    long long ans=1;
    for(int i=2;i<=x;i++) ans*=i;
    return ans;
}
int main(){
    int n;
    cin>>n;
    cout<<fab(n); //函数的调用
    return 0;
}
```
值得注意的是，在第二种定义方法下，需要按照一定顺序定义函数。先定义的函数不能去调用后定义的函数。

### return 的三种应用场景
- 返回函数的计算结果，如上文中的fab()
- 返回函数的执行状态，一般是具有逻辑判断功能的值
- 返回空，强制退出当前函数
```c++
//返回计算结果
int f1(int x){
    return x-1;
}
//返回执行状态，1为偶数0为奇数
int is_even(int x){
    return x%2==0;
}
//返回空，退出执行
void isLeapYear(int y){
    if((y%4==0&&y%100!=0)||y%400==0){
        cout<<"Leap year";
        return;
    }
    cout<<"Normal year";
}
```
### 函数定义的注意事项
- 函数不能嵌套定义，不能在函数中定义函数，但可以嵌套调用，即可以在函数中调用函数

### 函数的参数传递
向函数中传递的参数一般都是参数的拷贝，在函数内改变参数的值并不会改变原参数的值
```c++
void fun(int x){
    x=1;
    cout<<x;//1
}
int main(){
    int a=0;
    fun(a);
    cout<<a;//0
}
```
如果要改变参数的值，需要传递参数的引用或指针
```c++
void fun(int &x){
    x=1;
    cout<<x;//1
}
int main(){
    int a=0;
    fun(a);
    cout<<a;//1
}
```
### 向函数中传递数组
向函数中传递数组，并不是传递数组的拷贝，而是数组本身。相当于把数组进行了重命名
```c++
void fun(int x[]){
    x[4]=1;
    cout<<x[4];//1
}
int main(){
    int a[10];
    fun(a);
    cout<<a[4];//1
}
```
## 函数的递归调用
一看就会，一写就废

函数可以嵌套调用，即可以在函数中调用函数，这就意味着，函数自己也可以调用自己。

### 斐波那契数列
```
f(1)=1
f(2)=1
f(3)=f(1)+f(2)=2
f(4)=f(2)+f(3)=3
......
f(n)=f(n-1)+f(n-2)
```
这样一个程序如何用函数实现？
```c++
int fib(int x){
    if(x<=2) return 1; //最简单问题，fib(1)和fib(2)
    return fib(x-1)+fib(x-2); //将复杂问题fib(x)不断分解，直到出现最简单问题fib(1) fib(2)
    //思考，为什么上一行可以不加else？
}
```
### 递归函数的基本思想
我们要解决的问题比较复杂，但我们知道最简单的情况如何解决。如斐波那契数列我们很容易就知道第一项、第二项的值。

针对更加复杂的情况，我们可以利用更简单的情况经过一系列运算得出。如斐波那契数列的第n项等于前两项的加和。

因此，我们将更复杂的情况不断分解，最终分解到最简单的问题，最终计算出原结果。

### gcd 最大公约数（Greatest Common Divisor）
利用辗转相除法，可以求得最大公约数，在`b!=0`时`gcd(a,b)=gcd(b,a%b)`，当b==0时，a即为最大公约数。
```c++
int gcd(int a,int b){
    if(b==0) return a;
    return gcd(b,a%b)
}
```
有一些递归程序可以用while循环代替
```c++
int gcd(int a,int b){
    while(b!=0){
        int tmp=b;
        b=a%b;
        a=tmp;
    }
    return a;
}
```