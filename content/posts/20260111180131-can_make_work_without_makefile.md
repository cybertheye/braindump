+++
title = "can make work without Makefile"
author = ["Cyven Chaney"]
tags = ["question"]
draft = false
+++

-   belong: TODO

可以.

如果没有 Makefile, make 可以自动推断. 这是因为它内置了一套强大的隐式规则（Implicit Rules）和默认变量。

比如目录下面有一个 hello.c 文件, make hello 会执行 cc hello.c -o hello

另外可以使用命令行环境变量给make传参 make hello CC=clang CFLAGS="-g -Wall"

但通常这用于比较简单的文件,项目可能都称不上.
