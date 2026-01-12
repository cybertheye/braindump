+++
title = "what extra things did maven/gradle do compared to make"
author = ["Cyven Chaney"]
tags = ["question"]
draft = false
+++

-   belong: TODO

<!--listend-->

1.  **自动化依赖管理**
    比如需要使用一些第三方库
    如果使用make,许先手动去往上下载,然后再Makefile配置冗长的 -classpath
    那么 Maven/gradle 帮你做了这部分工作,主需要配置 artifactId和版本号就可以了
2.  **标准化的项目结构（约定优于配置）**
    Make：每个人写的 Makefile 结构都不一样。新手拿到项目后，需要先读懂 Makefile 才知道源码在哪、输出在哪。
    Maven/Gradle：遵循“约定优于配置”（Convention over Configuration）。所有的 Java 项目默认结构都是 src/main/java。这意味着任何 Java 开发者接手项目后，不需要看文档就能直接上手构建。
3.  **生命周期（Lifecycle）的深度集成**
    Make：你定义的 test、compile 只是独立的命令。
    Maven/Gradle：内置了完整的构建生命周期。当你运行 deploy（部署）时，它会自动按顺序触发：validate -&gt; compile -&gt; test -&gt; package -&gt; verify -&gt; install。这种严密的阶段管理在企业级开发中非常安全。
4.  **跨平台的一致性**
    Make：本质上是调用 Shell 指令。如果你的 Makefile 里写了 rm -rf 或 ls，那么在 Windows 系统的原生 CMD 下就会报错。
    Maven/Gradle：基于 Java 运行。它们内部封装了文件操作逻辑。无论在 Windows、Linux 还是 macOS 上，运行 mvn clean 的效果完全一致，具备极强的可移植性。
5.  **生态插件系统**
    Make：如果你想做静态代码分析、生成单元测试覆盖率报告，你需要自己写复杂的脚本并集成到 Makefile。
    Maven/Gradle：拥有海量的插件。只需添加几行配置，就能自动集成 Checkstyle（规范检查）、Jacoco（覆盖率测试）或 Docker 镜像打包。

如果是 Java/Kotlin 生态，Maven 是工业标准（稳重），Gradle 是性能巅峰（灵活、构建快），
它们解决了 make 无法处理的工程化难题。
