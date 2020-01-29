---
layout: post
title:  "[Chapter 1] System call"
date:   2020-01-29 22:01:44 +0800
---

int fork()，会返回一个int，代表子进程的pid, process id。

---

int wait(*xstatus)，父进程等待子进程结束，返回一个int，代表子进程的pid。
*xstatus是指传进去一个指针，wait调用结束后，会把子进程的exit status写进去。如果不关心的话，可以直接wait(0)。

---

void exec(string filename, string[] args)。exec会将当前进程进行替换，从文件系统中找一个文件，必须是可执行文件，加载，然后运行，作为新的进程。filename就是文件目录，args是传递过去的参数。 exec会替换进程，但会复用之前的file descriptor。[现实系统中的exec调用](https://www.geeksforgeeks.org/exec-family-of-functions-in-c/ )

疑问：exec family系统调用，int execvp(const char * __file, char * const * __argv)，__argv的最后一个元素是不是一定得是NULL，也就是0。感觉应该是的，用这个表示EOF。

答：是的。

---

Int read(int fd, byte[] buf, int n). 从fd(file descriptor)中读取至多n个字节写入buf中。r返回值是写入的字节数。返回0代表已经到达文件尾了。

--- 

int write(fd, buf, n)。从buf中读取n个字节写入fd中，返回写入的字节数。

---

int close(int fd)。关闭一个file descriptor，以便能让其他系统调使用这个fd。

---

int dup(int fd)。duplicate an existing file descriptor。

比如说传进去一个1（标准输出），可能返回3。

疑问：那如果duplicate 一个已经关闭的fd呢？答：经过试验，得到的fd即使写入，也没什么用。

如果dup之后，把原来那个close掉，dup之后的那个还能用吗？答：经过试验，可以的。

---

int pipe(int pipefd[2]); 创建管道。pipfd[0]代表读，[1]代表写。

疑惑，为什么要在子进程和父进程都去关闭pipfd[0] & pipefd[1]呢？

答： https://stackoverflow.com/questions/19265191/why-should-you-close-a-pipe-in-linux 解释了父进程需要关闭read，子进程需要关闭write，并且不用的话就马上关闭，fd是有限的。
