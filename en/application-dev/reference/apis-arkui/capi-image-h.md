# image.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines **Image** node types for **NativeNode** APIs, which are used to create and configure **Image** components in native applications, including image repetition patterns, width and height styles, filling effects, interpolation optimization, dynamic ranges, rotation directions, and render modes.

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
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | Enumerates the dynamic range modes (for example, SDR/HDR).|
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | Enumerates image rotation directions.|
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | Enumerates the image rendering modes.|

## Enumeration Description

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**Description**

Enumerates the image repeat patterns. This enumeration is used to control how an image is repeatedly drawn in scenarios such as backgrounds and patterns. For example, a small pattern can be used to fill the entire background in a wallpaper application.

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

Enumerates the image sizes. This enumeration is used to control how an image is scaled in a display area: **ARKUI_IMAGE_SIZE_AUTO** retains the original image aspect ratio. **ARKUI_IMAGE_SIZE_COVER** is suitable for scenarios where the image needs to fully occupy the container (such as album thumbnails). **ARKUI_IMAGE_SIZE_CONTAIN** is used in scenarios where the image needs to be displayed completely (such as preview on a details page).

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | The original image aspect ratio is retained.|
| ARKUI_IMAGE_SIZE_COVER = 1 | The image is scaled with its aspect ratio retained for the width and height to be greater than or equal to the display boundaries (the part that exceeds the boundaries may be clipped).|
| ARKUI_IMAGE_SIZE_CONTAIN = 2 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**Description**

Enumerates the image filling effects of the [Image](arkui-ts/ts-basic-components-image.md) component. **ARKUI_OBJECT_FIT_CONTAIN** is applicable to scenarios where the image needs to be displayed completely. **ARKUI_OBJECT_FIT_COVER** is applicable to scenarios where the image needs to fully occupy the container. **ARKUI_OBJECT_FIT_SCALE_DOWN** is applicable to scenarios where the image needs to be scaled down when it is too large.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|
| ARKUI_OBJECT_FIT_COVER = 1 | The image is scaled with its aspect ratio retained for the width and height to be greater than or equal to the display boundaries (the part that exceeds the boundaries may be clipped).|
| ARKUI_OBJECT_FIT_AUTO = 2 | The image is scaled automatically to fit the display area.|
| ARKUI_OBJECT_FIT_FILL = 3 | The image is scaled to fill the display area, and its aspect ratio is not retained.|
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 | The image is displayed with its aspect ratio retained, in a size less than or equal to the original size.|
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
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 | The original image size is retained. This value must be used together with **NODE_IMAGE_IMAGE_MATRIX** in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) in the **Image** component to control the image display effect (such as scaling, rotation, and translation) through matrix transformation.<br>**Since:** 21|

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**Description**

Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images. **ARKUI_IMAGE_INTERPOLATION_LOW** is suitable for performance-sensitive scenarios with low image quality requirements (such as quick scrolling of list thumbnails). **ARKUI_IMAGE_INTERPOLATION_MEDIUM** is suitable for most common scenarios. **ARKUI_IMAGE_INTERPOLATION_HIGH** is suitable for scenarios with high image quality requirements (such as image viewers).

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | No image interpolation.|
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 | Low-quality image interpolation. It provides low computing workload and fast rendering speed, which is suitable for scenarios that do not require high image quality or need to quickly render a large number of images.|
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 | Medium-quality image interpolation. It strikes a balance between computing workload and image quality, which is suitable for most common display scenarios.|
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 | High-quality image interpolation. This mode produces scaled images of the highest possible quality. It involves a large amount of computing workload and high resource consumption, which is suitable for display scenarios that require high image quality.|

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**Description**

Enumerates the dynamic range modes (for example, SDR/HDR). **ARKUI_DYNAMIC_RANGE_MODE_HIGH** is applicable to high-end devices that support HDR display and HDR content. **ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT** is applicable to transition scenarios where SDR needs to be compatible with. **ARKUI_DYNAMIC_RANGE_MODE_STANDARD** is applicable to common display devices.

**Since:** 21

| Value| Description|
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | High dynamic range (HDR), representing the range between minimum and maximum brightness values in an image (typically, the maximum brightness may be greater than 1,000 nits). A wider range makes image brightness closer to a perception range of human eyes in real-world conditions, preventing overexposure (all white) in bright environments and loss of detail (all black) in dark environments.|
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 | Constrained high dynamic range, offering richer brightness and color than SDR while maintaining SDR compatibility. Typically used in scenarios requiring SDR backward compatibility.|
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 | Standard dynamic range (SDR), featuring a limited brightness range (typically 0-100 nits) with reduced contrast between bright and dark areas. Dark areas may lose detail to black, while bright areas may become overexposed.|

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**Description**

Enumerates image rotation directions. It is used to adjust the display orientation of an image based on its Exif metadata or a manually specified value, which is suitable for processing the orientation of photos taken by users or correcting the display of photos.

**Since:** 21

| Value| Description|
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | Use Exif metadata for display orientation, with support for rotation and mirroring.|
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

Enumerates the image rendering modes. **ARKUI_IMAGE_RENDER_MODE_ORIGINAL** is applicable to scenarios where the original image color needs to be retained. **ARKUI_IMAGE_RENDER_MODE_TEMPLATE** is applicable to scenarios where a monochrome or black-and-white display is required (such as selected icons and colored icons).

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | Render image pixels as they are in the original source image.|
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 | Render image pixels to create a monochrome template image.|
