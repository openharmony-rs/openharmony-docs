# OH_HiAppEvent_ExternalLog

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_HiAppEvent_ExternalLog {...} OH_HiAppEvent_ExternalLog
```

## 概述

OH_HiAppEvent_ExternalLog结构体用于描述external_log故障文件信息，包含文件路径，文件生成时间戳，文件大小和系统事件类型。

**起始版本：** 26.0.1

**相关模块：** [HiAppEvent](capi-hiappevent.md)

**所在头文件：** [hiappevent.h](capi-hiappevent-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* filePath | 故障文件路径。 |
| long long generationTs | 故障文件生成时间戳。 |
| long fileSize | 故障文件大小，单位KB。 |
| [OH_HiAppEvent_SysEvent](./capi-hiappevent-h.md#oh_hiappevent_sysevent) event | 系统事件类型。 |
