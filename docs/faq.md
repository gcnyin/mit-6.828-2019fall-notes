# FAQ

## 1. 为什么我写对了却仍然无法通过测试？

看下grade-xxx，这是测试文件，里面有测试用例，可以比对下。

## 2. 为什么我添加了.c文件却无法编译？

修改Makefile中的UPROGS。如果添加的文件名为'user/xxx.c'，那么就在UPROGS下添加'$U/_xxx\'

## 3. 如何退出qemu emulator？

```
<Ctrl a + x>
```

## 4. 安装riscv64时遇到了问题？

如果make时出现这样的错误

```
riscv64-unknown-elf-gcc Library not loaded: /usr/local/opt/isl/lib/libisl.21.dylib
```

考虑使用[这个issue](https://github.com/riscv/homebrew-riscv/issues/15)提到的方式来修复

```
$ brew reinstall --build-from-source riscv-gcc
```