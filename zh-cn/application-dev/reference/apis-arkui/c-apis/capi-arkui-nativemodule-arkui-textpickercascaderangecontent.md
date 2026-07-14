# ARKUI_TextPickerCascadeRangeContent

```c
typedef struct ARKUI_TextPickerCascadeRangeContent {...} ARKUI_TextPickerCascadeRangeContent
```

## 概述

Defines the input structure of the interconnected multi-column text picker.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* text | Text information. |
| const [ARKUI_TextPickerRangeContent*](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) children | Interconnected data. |
| int32_t size | Size of the interconnected data array. |


