---
layout: post
title:  "[Chapter 1] File Descriptor"
date:   2020-01-29 22:01:43 +0800
---

文件描述符是int类型，代表一个由内核维护的对象，进程对它进行读/写。

File descriptor是一种抽象，背后可能是文件、pipe、设备。

每个进程有自己的file descriptor，由内核维护。

为了方便，就将file descriptor 0作为标准输入，1作为标准输出，2作为标准错误。

File descriptor可以打开，可以关闭。A newly allocated file descriptor is always the lowest- numbered unused descriptor of the current process. 如果要分配file descriptor，那么得到的值是数值最低的那个file descriptor。从0开始向上计算。如果之前什么都没有打开，那么打开的一定是file descriptor 0，即标准输入。

疑问：一个的进程启动时，0 1 2这三个fd是不是已经默认打开了？
答：是的。