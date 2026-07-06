# OH_Archive_StreamInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} OH_Archive_StreamInfo
```

## 概述

流式压缩/解压信息结构体。

**起始版本：** 26.0.0

**相关模块：** [Archive](capi-archive.md)

**所在头文件：** [oh_archive.h](capi-oh-archive-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t totalInSize | 压缩/解压前输入数据大小，单位为bytes。<br>**起始版本：** 26.0.0 |
| uint64_t totalOutSize | 压缩/解压后输出数据大小，单位为bytes。<br>**起始版本：** 26.0.0 |
| uint32_t checksum | 未压缩数据的校验和。当[OH_Archive_StreamChecksumAlg](capi-oh-archive-h.md#oh_archive_streamchecksumalg)设置为OH_ARCHIVE_NO_CHECKSUM时，checksum为0。<br>**起始版本：** 26.0.0 |


