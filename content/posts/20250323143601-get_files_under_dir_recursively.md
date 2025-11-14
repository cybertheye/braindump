+++
title = "get files under dir recursively"
author = ["Cyven Chaney"]
tags = ["directory", "file", "org-mode", "org-agenda", "question", "elisp"]
draft = false
+++

我设置了 `(setq org-agenda-file '("path/to/root-agenda-dir"))`

Org-agenda 默认不会递归检索 `"path/to/root-agenda-dir"` 子目录的 org 文件，

可以使用 `directory-files-recursively` 函数, 这是系统自带的方法

`(setq org-agenda-files (directory-files-recursively "/Users/mmmmmcclxxvii/Documents/cybertheye's life" "\\.org$"))`

-   relation: [org agenda]({{< relref "20250323162846-org_agenda.md" >}})
