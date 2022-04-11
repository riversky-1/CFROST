---
title: interview_sangfor
tags: Interview
abbrlink: dd8202d8
date: 2022-02-17 16:36:49
---

# **深信服一面（C/C++软件开发工程师）**

没有自我介绍，直接开问

**1、字符串复制有哪几种方式**

答：strcpy memcpy

**2、strcpy和memcpy有什么缺点吗**

答：strcpy有可能会数组越界 memcpy的缺点没答出来（memcpy不能拷贝目的地址（dest）和源地址（src）内存空间有重合的部分，更为确切的说应该是当目的地址大于源地址的时候，不能够有重合部分，否则源地址重合部分数据会发生错误）

**3、有哪几种内存的申请方式**

答：new malloc

**4、new如何判断内存是否申请成功**

答：new如果内存申请失败会抛出异常（以前的编译器好像会返回空指针，不抛出异常），申请成功则返回对象指针

**5、写一个类的copy构造函数**

答：

```c++
class test{
	private:
		char *data;
	public:
		test(const test& t){
			data = new char[strlen(t.data) + 1];
			strcpy(data, t.data);
		}
}
```

**6、用过初始化数组的函数吗？**

答：memset

**7、如果我用memset来初始化类，可以吗？**

答：不能，原因瞎说的（正确答案：如果类里面没有虚函数，那么能够用memset初始化，如果有，那么不能使用memset初始化，因为虚函数指针也会被初始化）

**8、vector怎么申请内存的**

答：按当前内存的两倍来申请

**9、vector如何遍历，把遍历方法写出来**

答：用auto或者索引来遍历

```c++
 for(auto &i : v)
for(iterator<int> i = v.begin(); i != v.end(); i++)
```

**10、如果使用vector的erase删除一个元素，那么这个元素的迭代器是否还存在？**

答：存在，因为后续元素会往前面补位，迭代器依然存在，只不过指向的是后一个元素或者空

**11、讲讲list的插入方法**

答：修改要插入位置中间的指针即可

**12、写一个反转链表的伪代码**

```c++
 class Solution{
	public:
		ListNode* reverseList(ListNode* Head){
			ListNode* pNode = Head;
			ListNode* pPre = nullptr;
			ListNode* pNext = nullptr;
			ListNode* pReverseHead = nullptr;
			while(pNode != nullptr){
				pNext = pNode -> next;
				if(pNext == nullptr)pReverseHead = pNode;
				
				pNode -> next = pPre;
				pPre = pNode;
				pNode = pNext;
			}
			return pReverseHead;
		}
};
```

**13、什么是野指针？**

答：指针未初始化，访问一个已销毁或者访问受限的内存区域的指针

**14、一个URL输入后发生了什么？**

答：DNS解析、TCP连接、浏览器发送http请求、服务器处理请求、浏览器解析渲染页面、关闭TCP连接

**15、说说TCP连接的三次握手和四次挥手**

答：三次握手：客户端向服务端发送一段TCP报文，服务器端接收到来自客户端的TCP报文之后，结束LISTEN阶段。并返回一段TCP报文、客户端接收到来自服务器端的确认收到数据的TCP报文之后，明确了从客户端到服务器的数据传输是正常的，结束SYN-SENT阶段。并返回最后一段TCP报文

四次挥手：首先客户端想要释放连接，向服务器端发送一段TCP报文、服务器端接收到从客户端发出的TCP报文之后，确认了客户端想要释放连接，随后服务器端结束ESTABLISHED阶段，进入CLOSE-WAIT阶段（半关闭状态）并返回一段TCP报文、服务器端自从发出ACK确认报文之后，经过CLOSED-WAIT阶段，做好了释放服务器端到客户端方向上的连接准备，再次向客户端发出一段TCP报文、客户端收到从服务器端发出的TCP报文，确认了服务器端已做好释放连接的准备，结束FIN-WAIT-2阶段，进入TIME-WAIT阶段，并向服务器端发送一段报文

**16、Linux创建子进程的命令**

答：fork()

**17、Linux怎么看一个进程是子进程还是父进程**

答：根据父进程查看子进程：pstree -p pid 根据子进程查看父进程：cat /proc/pid/status  fork()如果在父进程中返回子进程的pid，子进程中返回0