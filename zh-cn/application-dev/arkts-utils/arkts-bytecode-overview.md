---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "概述方舟字节码作为ArkTS/TS/JS编译后二进制产物的定位，并索引字节码文件格式、基本原理、函数命名规则及编译期自定义修改等子主题，帮助开发者快速进入字节码学习。"
keywords: [方舟字节码, 字节码概述, 字节码文件格式, 字节码基本原理, 函数命名规则, 编译期修改字节码, abc]
doctype: guide
status: active
---

# 方舟字节码概述

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @huyunhui1; @zmw1; @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

方舟字节码文件是ArkTS/TS/JS源码编译后的二进制产物。本章节介绍方舟字节码文件的各个部分，以帮助开发者深入了解字节码文件内容，进行字节码的分析和修改。

- [方舟字节码文件格式](arkts-bytecode-file-format.md)：介绍字节码文件中包含的各个部分的结构信息，以及各种结构的存储方式和映射关系。

- [方舟字节码基本原理](arkts-bytecode-fundamentals.md)：介绍字节码中构成指令的重要概念和具体的指令格式及含义，帮助开发者了解方舟字节码指令，进行指令相关的特性开发工作。

- [方舟字节码函数命名规则](arkts-bytecode-function-name.md)：介绍字节码文件中函数名字的字符串的命名规则。

- [编译期自定义修改方舟字节码](customize-bytecode-during-compilation.md)：介绍如何修改字节码文件的内容。
