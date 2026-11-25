# ArkUI_PickerComponentTextStyle

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=99d5d62217fd41ea373fb23731dda68d62ff2608 translatedAt=2026-11-23T03:41:59.317Z pushedAt=2026-11-23T03:44:59.942Z nl=1 -->

```c
typedef struct {...} ArkUI_PickerComponentTextStyle
```

## Overview

Defines the text style parameter of the picker component. This struct is used to set the text appearance in **DatePickerComponent** and **UIPickerComponent**, including the font color, font size, font weight, minimum font size, maximum font size, and text overflow handling mode.

**Since**: 26.1.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t color | Font color, in the 0xARGB format, for example, **0xFF182431**. |
| float fontSize | Font size, in fp. |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) fontWeight | Font weight. The value is an enumerated value of **ArkUI_FontWeight**. |
| float minFontSize | Minimum font size, in fp. It is used together with **maxFontSize** to enable font size scaling. When both **minFontSize** and **maxFontSize** are set, **fontSize** does not take effect. |
| float maxFontSize | Maximum font size, in fp. |
| [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow) overflow | Text overflow handling mode. It does not take effect when set to **ARKUI_TEXT_OVERFLOW_MARQUEE**. |
