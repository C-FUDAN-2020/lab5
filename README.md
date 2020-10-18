# Lab 5

    本节目标：
        1. 嵌套 if 语句
        2. PJ 实现第一步：输入命令与打印

## 获取及提交lab

**获取**：通过 `https://github.com/C-FUDAN-2020/lab5`，获取（建议通过Download ZIP方式下载）。

**提交物**：将你完成目标1的思考题、目标2的源代码文件作为 lab5 的提交物。

**提交**：将提交物文档命名为学号_姓名 （如20302010000_王明），提交至超星学习通对应的作业中。

**截止时间**：北京时间 2020年10月25日 23:59:59 

## if 语句的嵌套问题

请观察以下代码，思考命令行有何种输出

> 请提交书面答案的文档

### 问题一

```c
int a = -1, b = -1, c = 0;

if (a > b++)
printf("branch one\n\n");
else;
if (a < b)
c++;
else;
printf("%d\n", c);
```

### 问题二

请问下面的代码中，当 `year = 2020` 时，命令行输出什么，当 `year = 1000` 时呢？

```c
if (year % 4 == 0) 
if (year % 100 == 0)
if (year % 400 == 0)
leap = 1;
else
leap = 0;
else
leap = 1;
else
leap = 0;
if (leap)
printf("%d is ", year);
else
printf("%d is not ", year);
printf("a leap year.\n");
```

## PJ 实现第一步

从今天开始，lab 将围绕 PJ 的实现进行展开，今天我们要学的是第一步，如何如何输入命令与打印提示。

实现的方法是使用 `if` 或 `switch case`

1. 设置宏定义
    ```c
    #define HELP "\\h"
    #define LOAD "\\l"
    #define SAVE "\\s"
    #define DESIGN "\\d"
    #define GENERATE "\\g"
    #define RUN "\\r"
    #define EXIT "\\e"
    #define QUIT "\\q"
    #define PRINT "\\p"
    #define END "end"
    ```

    请大家思考一下为什么用两个反斜杠？

2. 条件语句判断
    ```c
    if (compare_string(buff, HELP) == 0) {
        printf("\t[\\h]\t打印命令提示\n");
        printf("\t[\\p]\t打印当前地图\n");
        printf("\t[\\l <filename>]\t导入地图\n");
        printf("\t[\\s <filename>]\t保存地图\n");
        printf("\t[\\d]\t进入地图设计模式\n");
        printf("\t[\\q]\t退出地图设计模式\n");
        printf("\t[\\g]\t生成下一代生命\n");
        printf("\t[\\r]\t开始生命游戏\n");
        printf("\t[\\e]\t停止生命游戏\n");
        printf("\t[end]\t退出游戏\n");
    }
    ```

    > compare_string 函数是为了方便写的宏定义

    ```c
    #include <string.h>
    #define compare_string(x, y) strncmp(x, y, strlen(y))
    ```

    **宏定义还能定义函数？请大家思考下宏定义的实现原理是什么**

    > `strncmp` 和 `strlen` 是 `<string.h>` 的库函数，请大家自行百度它的用法

3. 输入语句的获取

    第二步的 `buff` 变量里存储了命令行输入，相信大家已经很熟悉了。

    这个可以用 `scanf` 函数实现，但是助教的 PJ demo 中实际使用了以下代码：

    ```c
    fgets(buff, BUFFLEN, stdin);
    ```

    为什么助教会放弃 `scanf` ？答案会在之后有关 PJ 实现的 lab 中发布。
    *现在请大家自行百度，考虑 `scanf` 和 `fgets` 有哪些异同*


4. 最后请大家补全宏定义指令的其他部分，将代码打包提交

    - 不要求循环打印，程序可以只运行一个输入指令后直接退出
    - 注意，输入未知字符时程序的输出一定要实现！