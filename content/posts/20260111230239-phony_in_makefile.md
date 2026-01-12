+++
title = ".PHONY in Makefile"
author = ["Cyven Chaney"]
tags = ["concept"]
draft = false
+++

-   belong: [Makefile]({{< relref "20260111151751-makefile.md" >}})

.PHONY 是用來告訴 Make： **这个目标不是一个文件名称,不需要检查同名文件,直接执行指令就可以了**

如果没有 .PHONY

```nil
clean:
  rm -rf *.o
```

make clean 的时候, make会先去在当前目录寻找有没有 clean 的文件,
如果没有 make 才认为目标文件没有构建,然后才去执行指令
如果有,那就不会.

所以如果万一项目目录中有 clean 文件的话,那么就有问题了

```nil
.PHONY: test
test: tests.out
        @./tests.out

```

所以有了 .PHONY 标签,就是让make 直接干活
无论文件夹里有没有叫 clean 的文件，指令都会 100% 被执行。
