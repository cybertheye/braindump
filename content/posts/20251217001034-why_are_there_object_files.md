+++
title = "why are there object files"
author = ["Cyven Chaney"]
tags = ["QA"]
draft = false
+++

我们可以使用 [gcc]({{< relref "20251125214725-gcc.md" >}}) ,clang这样的编译工具将 [C]({{< relref "20250318222950-c.md" >}}),[C++]({{< relref "20250318223016-c.md" >}}) 的源文件编译得到一个 .o 文件

其实这种编译工具也可以直接得到我们所需要的执行程序,跳过中间的 .o 文件,也就是 object files

但为什么这个中间产物会存在呢?它是干什么用的?

我个人觉得其中最重要的是在大型程序中节省编译时间,
有了这个 .o 文件,可以模块化编译
当改了代码后,只需要编译所需要的文件到新的 .o 文件
其他不用动,再链接就行

{{< figure src="/ox-hugo/2025-12-17_00-29-54_screenshot.png" >}}
