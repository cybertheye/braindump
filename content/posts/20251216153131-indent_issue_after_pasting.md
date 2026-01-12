+++
title = "Indent issue after pasting"
author = ["Cyven Chaney"]
draft = false
+++

-   belong: [Emacs programming tips]({{< relref "20251214153420-emacs_programming_tips.md" >}})

有时候在代码块中,拷贝其他地方粘贴过来的代码,往往会出现第一行缩进,但是其他行没有缩进的情况

这是因为Emacs中的 C-y yank 功能只是 **复制原始文本** ,插入到光标位置,他不会触发缩进

{{< figure src="/ox-hugo/2025-12-16_15-36-08_screenshot.png" >}}

解决方法

1.  手动,Emacs 的 indent-region 功能
2.  手动,format全部代码 / lsp-bridge-code-format
3.  `c-ts-mode-indent-defun` 在一个方法里面 call C-c C-q 格式化整个方法缩进
