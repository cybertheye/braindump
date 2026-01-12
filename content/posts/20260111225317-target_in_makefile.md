+++
title = "target in Makefile"
author = ["Cyven Chaney"]
tags = ["concept"]
draft = false
+++

-   belong: [Makefile]({{< relref "20260111151751-makefile.md" >}})
    ```nil
    .PHONY: test
    test: tests.out
            @./tests.out

    .PHONY: memcheck
    # ... (memcheck 在后面)

    .PHONY: clean
    # ... (clean 在更后面)

    ```

这里的 test, memcheck, clean就是 Target

一般 test,clean,all,install 都跟 [PHONY in Makefile]({{< relref "20260111230239-phony_in_makefile.md" >}}) 搭配

如果只执行 make ,后面不带任何 target,
那就会尝试构建Makefile中第一个定义的目标, 在上面就是 test

如果你希望默认的 make 命令是编译你的业务程序，你需要新增一个业务程序的目标，并把它放在 test 前面。
例如，你可以添加一个 all 或 app.out 目标放在最前面：

```nil
  # 将 'all' 放在最前面，使其成为默认目标
.PHONY: all
all: app.out

app.out: main.c math_utils.c # 假设这是你的业务源文件
        $(CC) $(CFLAGS) $^ -o $@ $(LIBS)

# 然后才是你的测试目标
.PHONY: test
test: tests.out
        @./tests.out

# ... 其他规则 ...

```
