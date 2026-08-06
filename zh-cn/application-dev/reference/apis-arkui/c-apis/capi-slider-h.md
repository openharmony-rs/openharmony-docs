# slider.h

## 概述

Provides Slider node type definitions for <b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle) | ArkUI_SliderBlockStyle | 定义滑块形状。 |
| [ArkUI_SliderDirection](#arkui_sliderdirection) | ArkUI_SliderDirection | 定义滑动条滑动方向。 |
| [ArkUI_SliderStyle](#arkui_sliderstyle) | ArkUI_SliderStyle | 定义滑块与滑轨显示样式。 |

## 枚举类型说明

### ArkUI_SliderBlockStyle

```c
enum ArkUI_SliderBlockStyle
```

**描述**

定义滑块形状。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0 |  |
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE |  |
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE |  |

### ArkUI_SliderDirection

```c
enum ArkUI_SliderDirection
```

**描述**

定义滑动条滑动方向。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_DIRECTION_VERTICAL = 0 |  |
| ARKUI_SLIDER_DIRECTION_HORIZONTAL |  |

### ArkUI_SliderStyle

```c
enum ArkUI_SliderStyle
```

**描述**

定义滑块与滑轨显示样式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_STYLE_OUT_SET = 0 |  |
| ARKUI_SLIDER_STYLE_IN_SET |  |
| ARKUI_SLIDER_STYLE_NONE |  |


