# slider.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines **Slider** node types for **NativeNode** APIs.

**File to include:** <arkui/node_attributes/slider.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle) | ArkUI_SliderBlockStyle | Enumerates the styles of the slider in the block direction.|
| [ArkUI_SliderDirection](#arkui_sliderdirection) | ArkUI_SliderDirection | Enumerates the scroll directions of the slider.|
| [ArkUI_SliderStyle](#arkui_sliderstyle) | ArkUI_SliderStyle | Enumerates the slider styles.|

## Enum Description

### ArkUI_SliderBlockStyle

```c
enum ArkUI_SliderBlockStyle
```

**Description**

Enumerates the styles of the slider in the block direction.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0 | Round slider.|
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE = 1 | Slider with an image background.|
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE = 2 | Slider in a custom shape.|

### ArkUI_SliderDirection

```c
enum ArkUI_SliderDirection
```

**Description**

Enumerates the scroll directions of the slider.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_DIRECTION_VERTICAL = 0 | Vertical direction.|
| ARKUI_SLIDER_DIRECTION_HORIZONTAL = 1 | Horizontal direction.|

### ArkUI_SliderStyle

```c
enum ArkUI_SliderStyle
```

**Description**

Enumerates the slider styles.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_STYLE_OUT_SET = 0 | The slider is on the slider rail.|
| ARKUI_SLIDER_STYLE_IN_SET = 1 | The slider is in the slider rail.|
| ARKUI_SLIDER_STYLE_NONE = 2 | There is no slider.|
