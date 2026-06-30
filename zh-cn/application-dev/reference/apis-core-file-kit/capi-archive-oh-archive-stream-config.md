# OH_Archive_Stream_Config
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} OH_Archive_Stream_Config
```

## 概述

流压缩配置结构体。

**起始版本：** 26.0.0

**相关模块：** [Archive](capi-archive.md)

**所在头文件：** [oh_archive.h](capi-oh-archive-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t blockSize | 内存块大小，单位为bytes。当[OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod)设置为OH_ARCHIVE_COMPRESS_DEFLATE时，blockSize需不小于32768bytes。<br>**起始版本：** 26.0.0 |
| int32_t threadNum | 线程数。<br>**起始版本：** 26.0.0 |
| [OH_Archive_StreamChecksumAlg](capi-oh-archive-h.md#oh_archive_streamchecksumalg) checksum | 用于校验和的哈希算法。<br>**起始版本：** 26.0.0 |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | 压缩方法。<br>**起始版本：** 26.0.0 |


