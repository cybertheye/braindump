+++
title = "Emacs programming tips"
author = ["Cyven Chaney"]
tags = ["emacs"]
draft = false
+++

-   belong: [Emacs]({{< relref "20250317224646-emacs.md" >}})


## 原生操作 {#原生操作}


### 搜索 {#搜索}

ctrl-s
ctrl-r


### undo {#undo}

ctrl-x u

ctrl-space 框选一个region, 然后在 ctrl-x u 这样的话就会在这个指定的区域内 undo


### 复制剪切粘贴 {#复制剪切粘贴}

粘贴 ctrl-y
ctrl-k 当前光标位置到行尾剪切
先选定区域然后
复制 Esc-w
剪切 ctrl-w


### 补全 {#补全}

Esc-/ 或者 M-/ 补全一个最接近的词


### 编译 {#编译}


#### c/c++ mode {#c-c-plus-plus-mode}


## 我写的操作 {#我写的操作}


### 插入 {#插入}

在这行代码下面插入一行,类似 vim 中的 o 操作
ctrl-return

ctrl-shift-return 在上面插入一行


### 删除整行 {#删除整行}

command-backspace


## 第三方库 {#第三方库}


### c/c++ mode 编译 {#c-c-plus-plus-mode-编译}


## 其他 {#其他}


### [Indent issue after pasting]({{< relref "20251216153131-indent_issue_after_pasting.md" >}}) {#indent-issue-after-pasting--20251216153131-indent-issue-after-pasting-dot-md}
