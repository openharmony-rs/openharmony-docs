# hiappevent_cfg.h

## 概述

定义事件打点配置函数的所有配置项名称。如果开发者想要配置事件打点功能，可以直接使用配置项常量。示例代码:<pre>bool res = OH_HiAppEvent_Configure(MAX_STORAGE, "100M");</pre>

**库：** libhiappevent_ndk.z.so

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**起始版本：** 8

**相关模块：** [HiAppEvent](capi-hiappevent.md)

## 汇总

### 宏定义

| 名称 | 描述 |
| -- | -- |
| DISABLE "disable" | 事件打点开关。默认值为false。true：关闭打点功能，false：不关闭打点功能。<br>**起始版本：** 8 |
| MAX_STORAGE "max_storage" | 事件文件目录存储配额大小。默认值为“10MB”。<br>**起始版本：** 8 |

