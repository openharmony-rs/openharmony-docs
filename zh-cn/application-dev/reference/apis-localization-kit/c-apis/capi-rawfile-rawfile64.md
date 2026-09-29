# RawFile64

```c
typedef struct RawFile64 RawFile64
```

## 概述

RawFile64表示一个已打开的rawfile对象，用于访问2GB及以上的大文件。通过OH_ResourceManager_OpenRawFile64函数获取，使用完后须调用 [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64)关闭并释放。

**系统能力：** SystemCapability.Global.ResourceManager

**起始版本：** 11

**相关模块：** [rawfile](capi-rawfile.md)

**所在头文件：** [raw_file.h](capi-raw-file-h.md)

