# ArkUI_PickerComponentTextStyle

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_PickerComponentTextStyle
```

## 概述

选择器组件的文本样式参数。用于设置DatePickerComponent和UIPickerComponent中的文本外观，包括字体颜色、字号、字体粗细、最小字号、最大字号和文本溢出处理方式。

**起始版本：** 26.1.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t color | 字体颜色，采用0xARGB格式。例如0xFF182431。 |
| float fontSize | 字号，单位为fp。 |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) fontWeight | 字体粗细。取值为ArkUI_FontWeight的枚举值。 |
| float minFontSize | 最小字号，单位为fp。与maxFontSize配合使用以启用字号缩放。当minFontSize与maxFontSize同时设置时，fontSize不生效。 |
| float maxFontSize | 最大字号，单位为fp。 |
| [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow) overflow | 文本溢出处理方式。设置为ARKUI_TEXT_OVERFLOW_MARQUEE时不生效。 |
