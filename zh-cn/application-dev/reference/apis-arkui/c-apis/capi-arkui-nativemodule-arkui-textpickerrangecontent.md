# ARKUI_TextPickerRangeContent

```c
typedef struct ARKUI_TextPickerRangeContent {...} ARKUI_TextPickerRangeContent
```

## 概述

定义单列滑动数据选择器支持的图片资源结构体。该结构体用于在TextPicker组件中同时显示图片和文本内容，适用于需要在单列滑动选择器中展示图标和文本组合的场景。支持自定义图标路径和文本内容， 每项可设置独立的图标和文本或仅设置其中之一，帮助开发者实现灵活的图文选择器配置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* icon |  |
| const char* text |  |


