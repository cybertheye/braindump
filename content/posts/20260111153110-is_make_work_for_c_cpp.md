+++
title = "is make work only for c/cpp?"
author = ["Cyven Chaney"]
draft = false
+++

-   belong: [make]({{< relref "20260111140058-make.md" >}})

结论是:不是

因为 make 诞生于 70 年代的 C 语言开发环境，并因此在 C/C++ 领域最为流行

理论上 make 可以用于管理任何可以通过命令行执行编译,链接的项目,比如编译型语言 Java,Rust等

但是往往后者有专属于自己的高级的构建工具,比如 [maven]({{< relref "20260111160234-maven.md" >}}), [gradle]({{< relref "20260111160247-gradle.md" >}}),[cargo]({{< relref "20260111160256-cargo.md" >}})

但不是不可以.

java项目使用make构建demo

项目目录:

```nil
  my-java-project/
├── src/
│   └── com/
│       └── example/
│           ├── Main.java
│           └── Utils.java
├── Makefile
└── bin/          (构建后生成的字节码)

```

Makefile 文件:

```nil
  # 定义变量
JC = javac
JVM = java
JAR = jar
BIN_DIR = bin
SRC_DIR = src
MAIN_CLASS = com.example.Main
TARGET_JAR = MyProgram.jar

# 默认目标
all: compile

# 1. 编译规则
# 它会寻找所有 .java 文件，并编译到 bin 目录下
compile:
        @echo "正在编译 Java 源文件..."
        @mkdir -p $(BIN_DIR)
        $(JC) -d $(BIN_DIR) $(SRC_DIR)/com/example/*.java

# 2. 运行规则
# 依赖于 compile，确保运行前是最新的代码
run: compile
        @echo "正在启动程序..."
        @$(JVM) -cp $(BIN_DIR) $(MAIN_CLASS)

# 3. 打包规则
# 将编译好的 .class 文件打包成可执行的 JAR
jar: compile
        @echo "正在生成 JAR 文件..."
        $(JAR) cfe $(TARGET_JAR) $(MAIN_CLASS) -C $(BIN_DIR) .

# 4. 清理规则
clean:
        @echo "清理构建文件..."
        rm -rf $(BIN_DIR) *.jar

.PHONY: all compile run jar clean

```

执行 make &amp;&amp; make run 也是可以的

{{< figure src="/ox-hugo/2026-01-11_17-51-07_screenshot.png" >}}

-   [what extra things did maven/gradle do compared to make]({{< relref "20260111213148-what_extra_things_did_maven_gradle_do_compared_to_make.md" >}})
