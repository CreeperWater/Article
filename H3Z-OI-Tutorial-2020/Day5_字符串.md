# Day5 字符串
想要存储一串字符，我们可以使用一个字符数组，或C++的string

既然刚学完数组，我们还是用字符数组吧

## 字符串和字符数组
虽然我们可以用字符数组存储字符串，但字符数组和字符串其实是两个东西。

字符串：由零个或多个字符组成且通过双引号括起来的有限序列，例如，"Hello, world", "A", "123456"等

字符串结束标志符：'\0'，表示空字符 (null character)，是由编译器自动添加到字符串结尾处

字符数组：由字符构成的数组，结尾不一定是\0

```c++
char ch[10000];
char ch[]="1234567876543";
scanf("%s",ch);//字符串的输入，没有&符号
cin>>ch;
printf("%s",ch);//字符串输出
cout<<ch;
```
## 字符串的遍历及常用操作
```c++
char s[]="abcdefg1234567";
//字符串的长度
int length=strlen(s);
//遍历字符串中每一个字符
for(int i=0;s[i]!='\0';i++){
    cout<<s[i];
}
//或
for(int i=0;i<length;i++){
    cout<<s[i];
}
char s1[]="gfy";
char s2[]="wxpakioi";
char s3[]="wzy";
//字符串的比较
//字符串的比较采用了字典序比较，即由低位到高位比较，如a<b, ab<ac, ab<b, a<ab
//比较字符串 s1 与 s2 ，函数在 s1 等于、小于或大于 s2 时分别返回 0 、-1、1
strcmp(s1,s2); //-1
strcmp(s3,s2); //1
strcmp(s1,s1); //0
//比较字符串前n个字符
strncmp(s2,s3,1); //0
//字符串追加（将后面的连接到前面的字符串上）
//注意不要溢出
char res[100];
strcat(res,s3); //res---"wzy"
strcat(res,s2); //res---"wzywxpakioi"
strncat(res,s2,1) //res---"wzywxpakioiw"
//字符串的复制
//同样注意溢出的问题
char ans[100];
strcpy(ans,s1); //ans---"gfy"
memset(ans,0,sizeof(ans)); //清空ans
strncpy(ans,s1,2); //ans--"wxpakioi"
//同时注意strcpy只是覆盖，并不会清空目标数组
char ans[100];
strcpy(ans,s1); //ans---"gfy"
// memset(ans,0,sizeof(ans)); //清空ans
strncpy(ans,s2,2); //ans--"wxy"
```
**更多内容可以查看群里的PPT**