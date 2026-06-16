# ARKUI_TextPickerCascadeRangeContent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ARKUI_TextPickerCascadeRangeContent
```

## Overview

Defines a struct for the multi-column cascade picker.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name                                              | How to Emulate|
|--------------------------------------------------| -- |
| const char* text                                 | Text information.|
| const [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md)* children | Cascade data.|
| int32_t size                                     | Size of the cascade data array.|
