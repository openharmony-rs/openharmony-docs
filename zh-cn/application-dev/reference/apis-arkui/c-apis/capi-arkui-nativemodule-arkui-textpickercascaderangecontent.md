# ARKUI_TextPickerCascadeRangeContent

```c
typedef struct ARKUI_TextPickerCascadeRangeContent {...} ARKUI_TextPickerCascadeRangeContent
```

## 概述

定义多列联动滑动数据选择器的结构体，用于描述多列联动选择器的层级数据结构。该结构体通过children成员形成树状结构，支持多级联动选择，适用于需要展示省市区、年月日等分级数据的场景，可简化多级联动选择器的开发。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* text |  |
| [const ARKUI_TextPickerRangeContent*](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) children |  |
| int32_t size |  |


