# memory

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @sagittary-->
<!--Designer: @OH-wxy-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @fang-jinxu-->

## 概述

提供内存管理功能。提供的功能包括内存分配、内存释放等操作。

**起始版本：** 10
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [purgeable_memory.h](capi-purgeable-memory-h.md) | 提供可丢弃内存的内存管理功能。提供的功能包括创建、开始读取、结束读取、开始写入、结束写入、重建等。<br> 使用时需要链接libpurgeable_memory_ndk.z.so。 |
