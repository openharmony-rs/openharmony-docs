# custom_attributes.h

## 概述

为NativeNode API提供自定义节点事件定义。

**库：** libace_ndk.z.so

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | 定义自定义组件事件类型。 |

## 枚举类型说明

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**描述：**

定义自定义组件事件类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5 |  |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6 |  |


