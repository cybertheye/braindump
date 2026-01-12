+++
title = "what happened when we ran make test"
author = ["Cyven Chaney"]
tags = ["question"]
draft = false
+++

-   belong: TODO

借鉴一下 [Makefile]({{< relref "20260111151751-makefile.md" >}}) 中的demo配置

当运行 make test 时，Make 会开启以下“套路”：

1.  找目标（Target）：在 Makefile 里搜寻 test: 这个标签。
2.  清点依赖（Dependencies）：它会看到 test 依赖于 tests.out。于是它会检查我所有的 .c 和 .h 文件。只要我改了一行代码，它就会精准地触发重新编译，确保我测的是“最新版”。
3.  静默执行（Execution）：执行命令前的 @ 符号是我的最爱，它让终端不再回显 ./tests.out 这种废话，直接给我看测试结果。
4.  捕获退出码：这是最关键的。如果测试挂了，程序会返回一个非 0 的退出码，Make 捕捉到后会立刻报错“中断”流程，防止我把带 Bug 的代码推送到仓库。
