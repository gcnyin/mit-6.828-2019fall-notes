---
layout: page
title: FAQ
permalink: /faq/
---

### 1. 为什么我写对了却仍然无法通过测试？

看下grade-xxx.py，这是测试文件，里面有测试用例，可以比对下。

### 2. 为什么我添加的.c文件无法编译？

要改Makefile中的`UPROGS`部分。

### 3. 为什么执行make失败了？

如果你使用macOS，并且错误信息里有类似这样的描述

```
riscv64-unknown-elf-gcc Library not loaded: /usr/local/opt/isl/lib/libisl.21.dylib
```

请考虑使用这个[issue](https://github.com/riscv/homebrew-riscv/issues/15)提到的方式来修复

```
$ brew reinstall --build-from-source riscv-gcc
```