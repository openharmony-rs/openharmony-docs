# RawDir

```c
typedef struct RawDir RawDir
```

## 概述

RawDir表示一个已打开的rawfile目录对象，可用于遍历目录和目录下文件。通过{@link OH_ResourceManager_OpenRawDir}函数获取，使用完后须调用<br>{@link OH_ResourceManager_CloseRawDir}关闭并释放。

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 8

**相关模块：** [rawfile](capi-rawfile.md)

**所在头文件：** [raw_dir.h](capi-raw-dir-h.md)

