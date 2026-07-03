# image.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines **Image** node types for **NativeNode** APIs.

**File to include:** <arkui/node_attributes/image.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | Enumerates the image repeat patterns.|
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | Enumerates the image sizes.|
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | Enumerates the image filling effects of the [Image](arkui-ts/ts-basic-components-image.md) component.|
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images.|
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut.|
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | Enumerates image rotation directions.|
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | Enumerates the image rendering modes.|

## Enumeration Description

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**Description**

Enumerates the image repeat patterns.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 | The image is not repeatedly drawn.|
| ARKUI_IMAGE_REPEAT_X = 1 | The image is repeatedly drawn only along the x-axis.|
| ARKUI_IMAGE_REPEAT_Y = 2 | The image is repeatedly drawn only along the y-axis.|
| ARKUI_IMAGE_REPEAT_XY = 3 | The image is repeatedly drawn along both axes.|

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**Description**

Enumerates the image sizes.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | The original image aspect ratio is retained.|
| ARKUI_IMAGE_SIZE_COVER = 1 | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.|
| ARKUI_IMAGE_SIZE_CONTAIN = 2 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**Description**

Enumerates the image filling effects of the [Image](arkui-ts/ts-basic-components-image.md) component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|
| ARKUI_OBJECT_FIT_COVER = 1 | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.|
| ARKUI_OBJECT_FIT_AUTO = 2 | The image is scaled automatically to fit the display area.|
| ARKUI_OBJECT_FIT_FILL = 3 | The image is scaled to fill the display area, and its aspect ratio is not retained.|
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 | The image is displayed with its aspect ratio retained, in a size smaller than or equal to the original size.|
| ARKUI_OBJECT_FIT_NONE = 5 | The original size is retained.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START = 6 | Not resized, the image is aligned with the start edge of the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP = 7 | Not resized, the image is horizontally centered at the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END = 8 | Not resized, the image is aligned with the end edge at the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START = 9 | Not resized, the image is vertically centered on the start edge of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER = 10 | Not resized, the image is horizontally and vertically centered in the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END = 11 | Not resized, the image is vertically centered on the end edge of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START = 12 | Not resized, the image is aligned with the start edge at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM = 13 | Not resized, the image is horizontally centered at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END = 14 | Not resized, the image is aligned with the end edge at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 | The image maintains its original size. Must be used with **NODE_IMAGE_IMAGE_MATRIX** in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype).<br>**Since:** 21|

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**Description**

Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | No image interpolation.|
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 | Low quality interpolation.|
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 | Medium quality interpolation.|
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 | High quality interpolation. This mode produces scaled images of the highest possible quality.|

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**Description**

Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut.

**Since:** 21

| Value| Description|
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | High dynamic range (HDR), representing the range between minimum and maximum brightness values in an image. A wider range makes image brightness closer to real-world conditions, preventing overexposure (all white) in bright environments and loss of detail (all black) in dark environments.|
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 | Constrained high dynamic range, offering richer brightness and color than SDR while maintaining SDR compatibility. Typically used in scenarios requiring SDR backward compatibility.|
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 | Standard dynamic range (SDR), featuring a limited brightness range (typically 0-100 nits) with reduced contrast between bright and dark areas. Dark areas may lose detail to black, while bright areas may become overexposed.|

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**Description**

Enumerates image rotation directions.

**Since:** 21

| Value| Description|
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | Use Exif metadata for display orientation, with support for rotation and mirroring. Exif is a file format dedicated for photos taken by digital cameras and is used to record attributes and shooting data of the photos.|
| ARKUI_ORIENTATION_UP = 1 | Display original pixel data without transformation.|
| ARKUI_ORIENTATION_RIGHT = 2 | Display the image after rotating it 90 degrees clockwise.|
| ARKUI_ORIENTATION_DOWN = 3 | Display the image after rotating it 180 degrees clockwise.|
| ARKUI_ORIENTATION_LEFT = 4 | Display the image after rotating it 270 degrees clockwise.|
| ARKUI_ORIENTATION_UP_MIRRORED = 5 | Display the image after flipping it horizontally.|
| ARKUI_ORIENTATION_RIGHT_MIRRORED = 6 | Display the image after flipping it horizontally and then rotating it 90 degrees clockwise.|
| ARKUI_ORIENTATION_DOWN_MIRRORED = 7 | Display the image after flipping it vertically.|
| ARKUI_ORIENTATION_LEFT_MIRRORED = 8 | Display the image after flipping it horizontally and then rotating it 270 degrees clockwise.|

### ArkUI_ImageRenderMode

```c
enum ArkUI_ImageRenderMode
```

**Description**

Enumerates the image rendering modes.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | Render image pixels as they are in the original source image.|
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 | Render image pixels to create a monochrome template image.|
