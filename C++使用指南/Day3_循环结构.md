# Day3 循环结构
## for 循环
```c++
for(初始化循环变量;条件表达式;增量表达式){
    //语句
}
```
其中，“初始化循环变量”用来设立循环所涉及到的初始值，“条件表达式”用来判断是否应该跳出循环，增量表达式改变循环变量的值。

例1：求解1~n之间所有偶数的和
```c++
int sum=0;
for(int i=1;i<=n;i++){
    if(i%2==0) sum+=i;
}
cout<<sum<<endl;
```
**注意：** 求和时，变量sum必须初始化为0。求积时，变量sum必须初始化为1。

例2：求解1~n之间所有奇数的积
```c++
int sum=1;
for(int i=1;i<=n;i++){
    if(i%2==1) sum*=i;
}
cout<<sum<<endl;
```
**注意：** 求积时，变量sum必须初始化为1。

## while 循环
```c++
while(条件表达式){
    //语句
}
```
𝑤ℎ𝑖𝑙𝑒循环会不断检测条件表达式的值是否为𝑡𝑟𝑢𝑒，如果为𝑡𝑟𝑢𝑒就会执行一遍整个语句块内的内容。如果在循环内部没有改变条件表达式/退出循环的操作，会造成死循环。

## 简单循环 / 死循环
```c++
for(;;){
    //语句
}
while(1){
    //语句
}
```
省略条件表达式，或让条件表达式始终为true就构成了死循环，这样的循环在程序编写中也有很大的用处。

## 跳过 / 退出循环
使用`break`退出循环；使用`continue`跳过一次循环
```c++
for(int i=1;i<=10;i++){
    if(i==4) break;
    cout<<i<<" ";
}
//输出：1 2 3
for(int i=1;i<=10;i++){
    if(i==4) continue;
    cout<<i<<" ";
}
//输出：1 2 3 5 6 7 8 9 10
```