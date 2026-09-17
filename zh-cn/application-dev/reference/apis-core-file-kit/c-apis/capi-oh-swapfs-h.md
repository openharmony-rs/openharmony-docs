# oh_swapfs.h

## 概述

定义swapfs（交换文件系统）的native API，提供文件系统交换空间的创建、挂载、卸载等操作接口。 swapfs模块用于管理和监控应用的swap分区使用情况。 该模块支持交换空间的创建、挂载、卸载等操作，适用于需要优化内存管理、提升应用运行性能的场景。 支持将数据换出到磁盘并进行管理，在后续需要取回时换入，来实现对内存的灵活管理与性能提升。 该模块能够帮助开发者有效利用系统swap资源，改善内存不足情况下的应用体验。

**引用文件：** <filemanagement/swapfs/oh_swapfs.h>

**库：** libohswapfs.so

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

