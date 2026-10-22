# OH_HiAppEvent_ExternalLog

```c
struct OH_HiAppEvent_ExternalLog {...}
```

## 概述

The OH_HiAppEvent_ExternalLog 结构体用于描述外部日志信息，包括 文件路径、生成时间戳、文件大小、系统事件类型。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**起始版本：** 26.0.1

**相关模块：** [HiAppEvent](capi-hiappevent.md)

**所在头文件：** [hiappevent.h](capi-hiappevent-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* filePath |  |
| long long generationTs |  |
| long fileSize |  |
| enum OH_HiAppEvent_SysEvent event |  |


