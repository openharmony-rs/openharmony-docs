# ARKUI_TextPickerRangeContent

```c
typedef struct ARKUI_TextPickerRangeContent {...} ARKUI_TextPickerRangeContent
```

## 概述

定义单列滑动数据选择器支持的图片资源结构体。该结构体用于在TextPicker组件中同时显示图片和文本内容，适用于需要在单列滑动选择器中展示图标和文本组合的场景。支持自定义图标路径和文本内容，每项可设置独立的图标和文本或仅设置其中之一，帮助开发者实现灵活的图文选择器配置。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* icon | 图标路径。以\0结尾的C字符串。可为NULL。未通过API设置时，字段保持默认值nullptr；通过<br> [OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_seticonatindex)设置为nullptr时不生效（API会忽略此设置）。<br> 空字符串""合法，表示不显示图标。具体路径用于显示自定义图标（当需要图标提示时选择），<br> 空字符串用于明确不显示图标（当仅显示文本时选择），NULL为默认值（应通过Set方法设置为具体值或空字符串， 不建议保留NULL）。<br> 路径格式为应用内资源路径，例如"/common/hello.png"，与ArkTS TextPickerRangeContent一致；亦支持URI。<br> 图片格式未做专门限制，通过ImageSourceInfo加载，与Image组件支持的格式一致（如png、jpg、webp等）。<br> 显示尺寸固定为24vp × 24vp，不可通过本结构体配置。源码中未规定文件大小上限。 |
| const char* text | 文本内容。以\0结尾的C字符串。可为NULL，默认为nullptr；通过<br> [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_settextatindex)传入nullptr时不生效。<br> 空字符串""合法，表示不显示文本。具体文本内容用于显示提示信息（当需要文本说明时选择），<br> 空字符串用于明确不显示文本（当仅显示图标时选择），NULL为默认值（应通过Set方法设置为具体值或空字符串， 不建议保留NULL）。<br> 若未通过Set方法设置，则默认显示为空字符串，与ArkTS文档一致。 |


