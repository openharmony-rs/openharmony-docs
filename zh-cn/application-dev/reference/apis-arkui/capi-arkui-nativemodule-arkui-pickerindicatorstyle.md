# ArkUI_PickerIndicatorStyle
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_PickerIndicatorStyle
```

## 概述

选中项指示器的样式。包含指示器的颜色、大小等属性配置，用于增强Picker组件的选中项视觉效果，提升用户交互体验。该结构体为不透明句柄类型，须通过Create/Configure API配置样式，具体参数说明见下方「汇总」。注意：使用完毕后须调用相应的销毁函数释放资源，避免内存泄漏。

**起始版本：** 23

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

## 汇总

不透明句柄类型，不可直接访问成员。须通过 [OH_ArkUI_PickerIndicatorStyle_Create](capi-picker-h.md#oh_arkui_pickerindicatorstyle_create) 创建并指定指示器类型，再根据指示器类型调用对应的配置API：`ARKUI_PICKER_INDICATOR_BACKGROUND`类型调用 [OH_ArkUI_PickerIndicatorStyle_ConfigureBackground](capi-native-type-h.md#oh_arkui_pickerindicatorstyle_configurebackground)，`ARKUI_PICKER_INDICATOR_DIVIDER`类型调用 [OH_ArkUI_PickerIndicatorStyle_ConfigureDivider](capi-native-type-h.md#oh_arkui_pickerindicatorstyle_configuredivider)。

### 指示器类型

| 枚举值 | 值 | 说明 |
| -- | -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND | 0 | 以背景色和圆角高亮选中项 |
| ARKUI_PICKER_INDICATOR_DIVIDER | 1 | 以上下分割线标识选中项 |

### 类型与参数结构体

| 指示器类型 | 样式参数结构体 |
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND | [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) |
| ARKUI_PICKER_INDICATOR_DIVIDER | [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) |
