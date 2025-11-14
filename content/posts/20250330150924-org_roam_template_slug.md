+++
title = "org-roam template slug"
author = ["Cyven Chaney"]
draft = false
+++

-   issue: **其实这里要解决的是文件名空格问题**
-   relation: [org-roam template expansion]({{< relref "20250330153040-org_roam_template_expansion.md" >}})

<!--listend-->

```elisp
("d" "default" plain "%?"
     :target (file+head "%<%Y%m%d%H%M%S>-${slug}.org"
                        "#+title: ${title}\n")
     :unnarrowed t)
```

这里的 `${slug}` 是什么意思?

其实这里的 slug 表示一个 org 文件里面的一个 property

org-roam在创建一个文件node的时候会默认的创建几个 property,比如 slug,id,title等

而这个 slug 是由 `org-roam-node-slug` 函数创建的, 它的作用是,比如 title 是 hello world, slug就是 hello_world

`${slug}` 表示引用这个属性值,这样创建出来的文件名就不会有空格问题了
