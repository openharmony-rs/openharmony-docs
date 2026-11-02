# HiAppEvent_AppEventInfo

```c
struct HiAppEvent_AppEventInfo {...}
```

## 概述

单个事件信息，包含事件领域、事件名称、事件类型和事件携带的用JSON格式字符串表示的自定义参数列表。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**起始版本：** 12

**相关模块：** [HiAppEvent](capi-others-hiappevent.md)

**所在头文件：** [hiappevent.h](capi-hiappevent-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| /* 事件领域。表示事件所属的业务领域或功能模块，用于事件分类和管理。 */
    const char* domain |  |
| /* 事件名称。与domain配合使用唯一标识具体的事件。 */
    const char* name |  |
| /* 事件的类型。*/
    enum EventType type |  |
| /* JSON格式字符串类型的事件参数列表。 */
    const char* params |  |


