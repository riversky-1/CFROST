---
title: interview_sangfor_2
tags: Interview
abbrlink: 13c2f15d
date: 2022-02-17 17:00:17
---

# 深信服二面（C/C++软件开发工程师）

下午两点开始的面试

开局先进行自我介绍

**1、说说你参与度最高的一个项目吧**

**2、你在项目中遇到的最大困难是什么**

**3、平常有用过linux吗？说说grep是干嘛的吧**

答：grep是文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来

**4、ps命令是拿来干嘛的？**

答：进程查看命令。

参数：

- -A ：所有的进程均显示出来，与 -e 具有同样的效用；
- -a ： 显示现行终端机下的所有进程，包括其他用户的进程；
- -u ：以用户为主的进程状态 ；
- x ：通常与 a 这个参数一起使用，可列出较完整信息。

输出规则格式：

- l ：较长、较详细的将该PID 的的信息列出；
- j ：工作的格式 (jobs format)
- -f ：做一个更为完整的输出。

**5、说说main函数之前有哪些步骤**

答：去掉注释、展开define（预编译）；词法分析；语法分析；语义分析（编译）；将汇编代码生成目标文件（汇编；把多个目标文件链接成一个可执行文件（链接；

**6、给两个升序链表，合并成一个非递减链表**

答：

```c++
 struct ListNode{
    int var;
    ListNode *next;
    ListNode(int a) : var(a){next = NULL;}
};

ListNode* ansList(ListNode *pHead1, ListNode *pHead2)
{
    ListNode *p1 = pHead1, *p2 = pHead2, *p0 = pHead1, *p3 = pHead2 -> next;
    while(p1 != NULL && p2 != NULL){
        while(p1 && p1 -> var < p2 -> var)p0 = p1, p1 = p1 -> next;
        p0 -> next = p2;
        p2 -> next = p1;
        p0 = p2;
        p2 = p3;
        if(p3)p3 = p3 -> next;
    }
    while(p2 != NULL){
        p0 -> next = p2;
        p0 = p2;
        p2 = p2 -> next;
    }
    return pHead1;
}
```