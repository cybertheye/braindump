+++
title = "Emacs basic operations"
author = ["Cyven Chaney"]
tags = ["emacs"]
draft = false
+++

-   belong: TODO


## help {#help}

[C-c C-c](org-ctrl-c-ctrl-c)   查看文档，可以做好多事情，不管什么，可以都试试这个命令

可以使用 [org-store-link](org-store-link) 来保存buffer的页面
然后使用 C-c C-l 来在这里插入


## emacs buffer 操作 {#emacs-buffer-操作}

C-x left/right buffer切换上一个，下一个
ace-swap-window 左右分屏交换


## org-mode操作的部分 <span class="tag"><span class="test3">test3</span></span> {#org-mode操作的部分}

TAB 控制当前的headline以下的级别的展开和隐蔽
S-TAB 控制全局所有的headline的展开和关闭

C-c C-k

C-c C-x c clone克隆 subtree，可以试试在 [deadlines and schedules](#deadlines-and-schedules) 上进行克隆

C-c C-z 插入一个note

C-c C-u 跳到上一级


## refile {#refile}

C-c C-w


### archive {#archive}

C-c C-x C-s 单个的entry的archive。

`#+ARCHIVE: %s_done::datetree/* Finished`
::前面的是archive到哪个文件的文件名，如果没有指定路径就是默认同一个文件夹下，%s代表获取当前文件名
::后面是archive到这个文件的哪个headline下 也可以使用%s,比如 `::* From %s`

C-u C-c C-x C-s 在当前headline下找到所有的DONE的entry去archive
C-u C-u C-c C-x C-s 在当前headline下找到所有时间戳早于今天的entry去archive

C-c C-x C-a Archive the current entry using the command specified in the variable org-archive-default-command.
现在这个命令就是 org-archive-subtree跟 C-c C-x C-s一样
可以自定义更改


## time {#time}

C-c C-x 0 org-timer start
C-c C-x _ org-timer stop
C-c C-x , org-timer pause or continue
C-c C-x . 插入一个relative timer 对于org-timer start时间，如之前没有start，第一次是0:00:00

0:03:31
: C-c C-x - 插入一个org-timer item

C-c C-x ; 倒计时, 如何一个entry设置了 effort，那么就会直接倒计时这个effort


## clock {#clock}

C-c C-x C-i Clocks start
C-c C-x C-o Clocks stop
C-c C-x C-q Clock cancel
C-c C-x C-j Jump to the headline of the currently clocked in task. With a C-u prefix argument, select the target task from a list of recently clocked tasks.
C-c C-x C-d (org-clock-display)


## todo的操作 <span class="tag"><span class="test2">test2</span></span> {#todo的操作}

S-up   :test2:
S-down
C-c , Priority的设置


## tag <span class="tag"><span class="test">test</span></span> {#tag}


### variables {#variables}

-   org-tag-alist

C-c C-q

我现在的tag是和omnifocus一样的，VIP321,URGENCY321,O321
org-mode中还提供了 group 的功能
可以对一组tag组织到一起，算是一个group的，然后在后面agenda筛选group的时候，
属于这个group的tag都出现

[正则表达式的筛选](https://orgmode.org/manual/Tag-Hierarchy.html#:~:text=tags%20mutually%20exclusive.-,Furthermore,-%2C%20the%20members%20of)

```nil
#+TAGS: [ Vision : {V@.+} ]
#+TAGS: [ Goal : {G@.+} ]
#+TAGS: [ AOF : {AOF@.+} ]
#+TAGS: [ Project : {P@.+} ]
```


### tag search {#tag-search}

C-c / m 或者 C-c \\ 进行match,其实就是缩进其他一切不必要的，然后只展现match的


## properties {#properties}

C-c C-x p 设置属性
C-c C-c s 也是设置属性，需要光标停在PROPERTIES里面


## Date and time {#date-and-time}


### Calender {#calender}

S-RIGHT	One day forward.
S-LEFT	One day backward.
S-DOWN	One week forward.
S-UP	One week backward.
M-S-RIGHT	One month forward.
M-S-LEFT	One month backward.
&gt;	Scroll calendar forward by one month.
&lt;	Scroll calendar backward by one month.
M-v	Scroll calendar forward by 3 months.
C-v	Scroll calendar backward by 3 months.
C-.	Select today’s date


### timestamp {#timestamp}

C-c . 创建一个时间戳 默认不加时间  <span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue&gt;</span></span>
C-c . 连着调用两次，time rarnge <span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue&gt;&#x2013;&lt;2023-12-05 Tue&gt;</span></span>
C-u C-c . 也是创建时间戳，但是默认加上当前时间，<span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-12 Tue 12:38&gt;</span></span>
C-u C-u C-c . 创建一个时间戳，而且是当前时间 <span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue 12:36&gt;</span></span>

C-c ! inactive 的时间戳 <span class="timestamp-wrapper"><span class="timestamp">[2023-11-05 Sun] </span></span> <span class="timestamp-wrapper"><span class="timestamp">[2023-12-05 Tue 12:42]</span></span>

C-c &lt; 插入一个时间戳，是光标所在的Calendar上的

C-c &gt; 光标先停在一个时间戳上，然后这个操作会跳到对应的Calendar上
<span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue 12:49 +1w&gt;</span></span>

C-c C-o 打开Org Agenda

C-c C-y 对于<span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue&gt;&#x2013;&lt;2023-12-12 Tue&gt;</span></span>这样的range计算时间差

C-u C-c C-y
不仅计算时间差还会在后面插入 <span class="timestamp-wrapper"><span class="timestamp">&lt;2023-12-05 Tue 12:57&gt;&#x2013;&lt;2023-12-12 Tue 12:57&gt; </span></span> 7d 00:00

S-方向键 时间戳上可以拨动调整


### deadlines and schedules {#deadlines-and-schedules}

C-c C-d 插入一个deadline
C-c C-s 插入一个SCHEDULED,如果已经有那就是改变。


### \TODO repeated task/ 在scheduled和deadline的基础上的 {#todo-repeated-task-在scheduled和deadline的基础上的}

:LAST_REPEAT: <span class="timestamp-wrapper"><span class="timestamp">[2023-12-07 Thu 19:09]</span></span>

解释：<span class="timestamp-wrapper"><span class="timestamp">&lt;2005-10-01 Sat -3d&gt;</span></span>
+1m 表示每隔一个月
-3d 表示在前三天开始warning，

使用C-c C-t 让一个重复的task 从TODO变成DONE，但因为有重复任务，会立刻变回TODO，而且时间戳也变了

如果就像变成DONE的状态，也就是不需要重复了，
使用C-- 1 C-c C-t 来改变状态


### \`++\`,\`.+\`,\`+\`的区别 TOdo中 {#plus-plus-dot-plus-plus-的区别-todo中}

:LAST_REPEAT: <span class="timestamp-wrapper"><span class="timestamp">[2023-12-07 Thu 19:43]</span></span>

三个都是在重复任务中设置 interval 用的
区别在于如果

现在的时间（准确来说是将TODO状态变成DONE状态的时间）
**超过了!!!**
DEADLINE或者SCHEDULE设置的时间
的时候，这个date怎么shift

比如   `<2023-12-05 Tue 12:00 +1d>`
现在是 2023-12-07 19:21
如果现在把这个TODO状态改为 DONE，那么上面的DEADLINE变成 2023-12-02 Sat 12:00.。
这样，就是在计划的时间上机械的加一天
那么这样这个任务也还是 overdue 过期的，在一些场景下，我虽然过了一段时间再去完成，
但是我希望他下次重复是未来的时间
比如每周一给爸爸打电话，虽然过去了4个星期了，我才打一次，那么下次应该是下个周一，不能我需要连打
三次电话把所有过期任务都标记完成

所以 +1d这样，是repeat from assigned date

而类似 ++1d,.+1d 是repeat from completion

看例子：

`<2023-12-08 Fri 22:00 ++1d>`
在2023-12-07 19:36 设置为DONE后是
`<2023-12-09 Sat 22:00 ++1d>`

`<2023-12-08 Fri 22:00 .+1d>`
在2023-12-07 19:36 设置为DONE后是
`<2023-12-08 Fri 22:00 .+1d>`

--- hour
`<2023-12-01 Fri 22:00 ++1h>`
在2023-12-07 19:41 设置为DONE后是
`<2023-12-07 Thu 20:00 ++1h>`

`<2023-12-01 Fri 22:00 .+1h>`
在2023-12-07 19:43 设置为DONE后是
`<2023-12-07 Thu 20:43 .+1h>`

在hour层面，.+是从完成DONE的时刻开始重新计时，会改变timestamp
++不会

所以.+是更加的 repeat from  completion


### effort {#effort}

C-c C-x e (org-set-effort)
C-c C-x C-e (org-clock-modify-effort-estimate)


## <span class="org-todo done CLOSED_TODO">CLOSED-TODO</span> Rich Content {#rich-content}

_One may expect this whole sentence to be italicized, but the
following ~user_?variable~ contains `/` character, which effectively
stops emphasis there./ **test** are wonderful. <span class="underline">hello world</span>


## capture {#capture}

C-c c 是org-capture 我设置了
C-u C-c c 直接到我设置的inbox.org文件中，需要选择
C-u C-u C-c c 直接到我设置的index.org文件中，不需要选择


## agenda {#agenda}

C-c [ add current file to the agenda file list
C-c ] remvoe current file from the agenda file list


## <span class="org-todo done CLOSED_TODO">CLOSED-TODO</span> For Test {#for-test}

-   [ ] job1 <code>[0%]</code>
    -   [ ] job2
    -   [ ] job3
    -   [ ] job4


## org-agenda {#org-agenda}

这里指的是在org agenda 的 buffer中的快捷键
&lt; filter by category


## rich type {#rich-type}


### code {#code}

hello `M-x eww`

`M-x eww`

```nil

```


## Source Code {#source-code}


### 快速插入#+BEGIN\_ {#快速插入-plus-begin}

C-c C-,
They changed the template system in orgmode 9.2.

The new mechanism is called structured template. The command org-insert-structure-templatebound to C-c C-,
gives you a list of #+begin_-#+end\_ pairs that narrows down while you type and you can use completion.


## lisp 代码执行 {#lisp-代码执行}

C-M-x 在.el文件中 绑定的是 eval-defun ，用于执行当前光标所在的函数定义。


## anki demo {#anki-demo}


### 正面 {#正面}

anki-editor-mode
anki-editor-insert-note


### 背面 {#背面}

需要先打开anki
