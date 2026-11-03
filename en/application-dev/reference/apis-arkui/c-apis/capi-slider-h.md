# slider.h

## Overview

Provides Slider node type definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle) | ArkUI_SliderBlockStyle | Enumerates the styles of the slider in the block direction. |
| [ArkUI_SliderDirection](#arkui_sliderdirection) | ArkUI_SliderDirection | Enumerates the scroll directions of the slider. |
| [ArkUI_SliderStyle](#arkui_sliderstyle) | ArkUI_SliderStyle | Enumerates the slider styles. |

## Enum type description

### ArkUI_SliderBlockStyle

```c
enum ArkUI_SliderBlockStyle
```

**Description**

Enumerates the styles of the slider in the block direction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0 | Round slider.<br>**Since**: 12 |
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE | Slider with an image background.<br>**Since**: 12 |
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE | Slider in a custom shape.<br>**Since**: 12 |

### ArkUI_SliderDirection

```c
enum ArkUI_SliderDirection
```

**Description**

Enumerates the scroll directions of the slider.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SLIDER_DIRECTION_VERTICAL = 0 | Vertical direction.<br>**Since**: 12 |
| ARKUI_SLIDER_DIRECTION_HORIZONTAL | Horizontal direction.<br>**Since**: 12 |

### ArkUI_SliderStyle

```c
enum ArkUI_SliderStyle
```

**Description**

Enumerates the slider styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SLIDER_STYLE_OUT_SET = 0 | The slider is on the slider rail.<br>**Since**: 12 |
| ARKUI_SLIDER_STYLE_IN_SET | The slider is in the slider rail.<br>**Since**: 12 |
| ARKUI_SLIDER_STYLE_NONE | There is no thumb.<br>**Since**: 12 |


