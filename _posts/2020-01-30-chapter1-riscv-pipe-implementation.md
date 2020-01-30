---
layout: post
title:  "[Chapter 1] riscv pipe实现的注释"
date: 2020-01-30 11:52:43 +0800
---

[Line 100](https://github.com/mit-pdos/xv6-riscv/blob/riscv/user/sh.c#L100)

```c
  case PIPE:
    pcmd = (struct pipecmd*)cmd;
    if(pipe(p) < 0)
      panic("pipe");
    if(fork1() == 0){ // 对左边进行处理，将左边的标准输出重定向到pipe的write fd
      close(1);
      dup(p[1]);
      close(p[0]);
      close(p[1]);
      runcmd(pcmd->left);
    }
    if(fork1() == 0){ // 对右边进行处理，将右边的标准输入重定向到pipe的read fd
      close(0);
      dup(p[0]);
      close(p[0]);
      close(p[1]);
      runcmd(pcmd->right);
    }
    close(p[0]);
    close(p[1]);
    wait(0);
    wait(0);
    break;
```
