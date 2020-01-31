# ls实现注释

[源代码](https://github.com/mit-pdos/xv6-riscv/blob/riscv/user/ls.c#L55)，第55行。

这里面这么多花里胡哨的，全是因为标准库不全，写作业能把人累死。

```c
    strcpy(buf, path); // 此时：path为'.', buf为'.'
    p = buf+strlen(buf);
    *p++ = '/'; // 给添加个/的末尾，buf: './'
    while(read(fd, &de, sizeof(de)) == sizeof(de)){
      if(de.inum == 0)
        continue;
      memmove(p, de.name, DIRSIZ); // 给buf添加上文件名文件名, 比如'./file_a'
```