+++
title = "What processes and threads does a browser have?"
author = ["Cyven Chaney"]
draft = false
+++

-   belong: [browser]({{< relref "20250420220350-browser.md" >}})
-   relation: TODO

可以在浏览器的任务管理器查看所有的进程

{{< figure src="/ox-hugo/2025-04-20_22-15-20_screenshot.png" >}}

这里最主要的进程有:

1.  [browser process]({{< relref "20250421232225-browser_process.md" >}})  浏览器进程:
2.  [rendering process]({{< relref "20250421232426-rendering_process.md" >}}) 渲染进程:
3.  [network process]({{< relref "20250421232510-network_process.md" >}}) 网络进程

包含的线程则是在各个进程里面
