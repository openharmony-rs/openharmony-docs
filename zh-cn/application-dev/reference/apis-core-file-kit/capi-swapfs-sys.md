# Swapfs (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## 概述

Swapfs模块提供swap文件系统相关的错误码定义，用于管理和监控应用的swap分区使用情况。<br> 该模块支持swap分区的创建、挂载、卸载等操作，适用于需要优化内存管理、提升应用运行性能的场景。<br> 该模块能够帮助开发者有效利用系统swap资源，改善内存不足情况下的应用体验。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [swapfs_errcode.h (系统接口)](capi-swapfs-errcode-h-sys.md) | 声明swapfs模块的错误码，包括文件系统操作过程中的各类错误状态定义。 |
| [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md) | 定义swapfs（交换文件系统）的native API，提供文件系统交换空间的创建、挂载、卸载等操作接口。<br> swapfs模块用于管理和监控应用的swap分区使用情况。<br> 该模块支持交换空间的创建、挂载、卸载等操作，适用于需要优化内存管理、提升应用运行性能的场景。<br> 支持将数据换出到磁盘并进行管理，在后续需要取回时换入，来实现对内存的灵活管理与性能提升。<br> 该模块能够帮助开发者有效利用系统swap资源，改善内存不足情况下的应用体验。 |
