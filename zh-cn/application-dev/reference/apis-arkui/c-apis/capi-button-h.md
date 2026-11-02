# button.h

## 概述

Provides Button node type definitions for <b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ButtonType](#arkui_buttontype) | ArkUI_ButtonType | 定义按钮样式枚举值。 |

## 枚举类型说明

### ArkUI_ButtonType

```c
enum ArkUI_ButtonType
```

**描述：**

定义按钮样式枚举值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BUTTON_TYPE_NORMAL = 0 | 普通按钮，默认不带圆角。<br>**起始版本：** 12 |
| ARKUI_BUTTON_TYPE_CAPSULE | 胶囊型按钮，圆角默认为高度的一半。<br>**起始版本：** 12 |
| ARKUI_BUTTON_TYPE_CIRCLE | 圆形按钮。<br>**起始版本：** 12 |
| ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 | 圆角矩形按钮。<br>**起始版本：** 19 |


