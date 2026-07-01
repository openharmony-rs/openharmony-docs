# button.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

为NativeNode API提供Button节点类型定义。

**引用文件：** <arkui/button.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

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

**起始版本：** 12

| 枚举项 | 描述                      |
| -- |-------------------------|
| ARKUI_BUTTON_TYPE_NORMAL = 0 | 普通按钮，默认不带圆角。            |
| ARKUI_BUTTON_TYPE_CAPSULE = 1 | 胶囊型按钮，圆角默认为高度的一半。       |
| ARKUI_BUTTON_TYPE_CIRCLE = 2 | 圆形按钮。                   |
| ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 | 圆角矩形按钮。<br>**起始版本：** 19 |


