+++
title = "what does rendering process do?"
author = ["Cyven Chaney"]
draft = false
+++

-   belong: [rendering process]({{< relref "20250421232426-rendering_process.md" >}})
-   relation: TODO

渲染进程启动后,会开启一个  渲染主线程,它负责执行 HTML,CSS,JS 代码

现在浏览器是每个标签页独立一个渲染进程,这也是标签开多了 chrome 占用内存很大的原因

这么做的主要原因是为了标签页之间互不影响.
