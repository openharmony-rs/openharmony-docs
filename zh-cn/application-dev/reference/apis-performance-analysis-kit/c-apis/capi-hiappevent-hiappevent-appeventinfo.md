# HiAppEvent_AppEventInfo

```c
typedef struct HiAppEvent_AppEventInfo {...} HiAppEvent_AppEventInfo
```

## 概述

单个事件信息，包含事件领域、事件名称、事件类型和事件携带的用JSON格式字符串表示的自定义参数列表。

**起始版本：** 12

**相关模块：** [HiAppEvent](capi-hiappevent.md)

**所在头文件：** [hiappevent.h](capi-hiappevent-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* domain | 事件的域。 |
| const char* name | 事件的名称。 |
| enum EventType type | 事件的类型。 |
| const char* params | 参数的JSON字符串。 |


