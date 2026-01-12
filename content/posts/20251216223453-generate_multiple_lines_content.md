+++
title = "generate multiple lines content"
author = ["Cyven Chaney"]
tags = ["emacs"]
draft = false
+++

-   belong: [Emacs]({{< relref "20250317224646-emacs.md" >}})

比如生成这样的

{{< figure src="/ox-hugo/2025-12-16_22-36-00_screenshot.png" >}}


## 使用 rectangle-number-lines {#使用-rectangle-number-lines}

比方生成 THING1 到 THING30
那么先生成30个空行

`C-u 30 RET`

然后再 C-x spa1 ce rectangle mode选择30行
	      2
`C-u C-x r N`

会提示输入 Number from count
以及 format string,这里输入 THING%d, 就可以了
