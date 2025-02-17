---
title: 第一个C程序
author: imcpap
date: 2025-01-01 00:00:00 +0800
categories: [编程简要笔记, C语言基础]
tags: [C语言,编程简要笔记,编程基础笔记,中文]
---
> 网站测试内容。
{: .prompt-warning }

因为最近正在学习编程，但发现中文教程质量参差不齐（其他语言也没好到哪去）。所以计划将学习过程中的想法与感悟在此记录，试图用最简洁的语言来表述该语言逻辑。当然，也顺便强制让自己写点东西，语言水平不要退步地太离谱吧（已经要傻了）。

说到C语言，虽然确实已经多年没有重大更新了（不像隔壁Cpp每隔段时间就好像换了个语言一样），但这也代表其因为十分基础而无需过多更改。我在学过C了之后，才对其他编程语言有了更深入的理解。

因为网上关于安装C语言环境的教程较多，且这个步骤也不很重要（因为其广泛地支持性，即使用文本文件编程也不算那么麻烦），我想在之后写到其他语言和应用范围时一同补上。

## 摘要

- 最基本的Hello World程序
- 在C代码中添加注释

## 你好，世界！

一个标准的C语言Hello World程序如下所示：

```c
#include <stdio.h>

int main (){
printf_s("Hello, World!");
return 0;
}
```

该程序由每个C程序都必要的4个部分组成，现在将分别解释每个部分的作用。

### 头文件 (Header)

```c
#include <stdio.h>
```

这行代码就如其字面意义所示：**包含**名为**stdio**的**头文件**。

> 你可以在[互联网](https://en.cppreference.com/w/c/io)上查询各种标准头文件所包括内容。
{: .prompt-tip }

**#**符号开头的命令被称为预处理指令，其在编译器编译源代码之前执行。

**头文件**是一种载体文件。先前的程序员（也可以是你自己）为了将复杂的程序变成易于想象的语言，使用头文件来定义各种程序中使用的函数和类型。你可以将这个文件简单地理解为“字典”。

这段代码的含义就是告诉编译器：在开始编译（阅读和理解）代码之前，请先打开名为stdio的头文件（字典），不然接下来的东西你看不懂。

> 注意：stdio是standard input and output的缩写，小心拼写错误！
{: .prompt-warning }

### （主）函数

```c
int main(){}
```

任何C程序由三个部分组成：数据类型、数据和函数。

**int**代表这个函数的数据类型是整数。在C语言中，数据类型包括整数int、浮点数（小数）float、字符char等。事实上这代表了这些数据是如何被储存（并阅读）的。在这里，int指main函数的回传值（return）是整数。

> 偶尔，这里也可以写void（没有数据），但return（回传值）不能与其同时出现。道理也很简单：既然已经写了这里没有数据，那就不应该出现数据。主函数使用void虽然不合规范，但在某些需要极度精简性能的场景下可能是必要的。
{: .prompt-info }

C语言中的函数不同于数学上的，它其实应该被翻译作“功能”或者类似的名字。函数中记录着所有希望其所达到的目的和步骤。在C中（事实上是任何编程语言中）可以让函数有着各种各样的名字，因为通常函数名称都是程序员自己命名的。但此处的main不太一样。

**main**这个名字代表主函数。主函数在所有函数之中极为特殊，它表示起点：当程序开始运行之后，其可能无限循环做某事而没有终点，但其一定有一个起点。这就好像宇宙大爆炸，一定有一个开始，但是未来却不一定有终结。编译器在读完预处理指令后，就会来寻找main在哪里，并从这里开始执行。

> 如果没写main，编译器就会一脸懵逼：门在哪里？当然了，如果写了很多个main，编译器也会懵：我应该从哪个门进？所以，请务必保证所写的程序中只包含1个main函数。
{: .prompt-warning }

**()**圆括号代表参数。如果你希望函数在执行前就知道一些数据作为参考，那就请把它应该知道的数据写在这里。很快，你就会对这个值有更直观的理解。在这个简单的程序中，main函数不需要知道任何事情，所以我们不在括号内填写任何内容。

处于**{}**大括号内的是函数主体。所有该函数所需要的命令都被写在大括号之内，编译器将会自上而下依次阅读。

### 函数

```c
printf_s("Hello, World!");
```

这大概是所有C程序学习者所学习的第二个函数（第一个是主函数），它的功能是将其**接受值**呈现在屏幕上。不过，这个函数好像跟主函数不太一样，它只包括了**名称**和**参数**。这是因为它已经在**stdio.h**中被定义过了，编译器只需要去查已经提前打开的字典就知道它该干什么了。

> 你也可以使用printf来实现此功能，其代表格式化打印（Print Formatted）。printf_s比printf增强了安全性，比如其能检测输入的内容是否有效。
{: .prompt-info }

使用两个双引号**"**将你想在屏幕上显示的内容包裹（这是为了告诉编译器，其中的内容不需要理解，直接照搬即可）。

在函数结尾，使用分号**;**将其与其他语句分开，表示结束。

### 回传值

当函数执行完毕之后，你可以选择将结果传回。

你可以这样理解：**参数**负责告诉这个函数解题需要知道的调解，函数主题就是解题过程，而回传值就是答案。不是所有时候我们都需要答案，因为过程就可能已经达到了目的（就例如printf_s这个函数，其将内容显示在屏幕的过程就已经完成了我们现在的需求，因此我们也不需要其给出什么答案）。

> 其实这个函数是有回传值的，其数据类型是整数int。只是我们并不需要。
{: .prompt-info }


那么，我们可以从头到尾来“读”一下这个程序代表的含义：

1. 在开始编译（阅读和理解）代码之前，先打开名为stdio的头文件（字典），不然接下来的东西看不懂。
2. 找到名称为main的函数，那里是程序的开始。可以看到，main函数的回传值类型是整数（int），不需要参数。
3. 开始执行main函数，其中的第一个函数是printf_s，可以在名为stdio的头文件中发现这个定义。而需要执行这个函数需要参数，参数是"Hello, World!"。执行完毕后，这个函数的回传值不被需要。
4. 现在，已经完成了这个函数所需完成的，将“0”回传。

主函数的回传值代表这个程序的行为：0代表成功退出。可以简单地（但可能并不严谨地）理解为：如果程序顺利运行到此，那么就可以结束了。

### 注释的方法

好像稍微有点复杂，需要记录一下？C语言提供了两种极为方便的注释方法：

```c
// 两条斜杠的注释让自其开始，至换行结束的所有内容都被视为注释。
/* 但如果注释内容非常多，也可以使用（斜杠加星号）的写法。
在其结束符号（星号加斜杠）之前的所有内容都被视为注释，无论换行与否。
不过注释将在你第一次写（星号加斜杠）时立即结束，
无论你在其之前写了多少个/*，*/这里总是注释以外
```

注释的内容不会被编译或阅读，其存在意义就是为了源代码能被读懂：

```c
#include <stdio.h> // 预处理指令

int main (){ // 主函数
printf_s("Hello, World!"); // 格式化打印
return 0; // 回传值
}
```

## 接下来

