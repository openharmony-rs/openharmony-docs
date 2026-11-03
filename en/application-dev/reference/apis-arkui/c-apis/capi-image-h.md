# image.h

## Overview

Defines **Image** node types for **NativeNode** APIs, which are used to create and configure **Image**<br>components in native applications, including image repetition patterns, width and height styles, filling effects, interpolation optimization, dynamic ranges, rotation directions, and render modes.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | Enumerates the image repeat patterns. This enumeration is used to control how an image is repeatedly drawn in scenarios such as backgrounds and patterns. For example, a small pattern can be used to fill the entire background in a wallpaper application. |
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | Enumerates the image sizes. This enumeration is used to control how an image is scaled in a display area: **<br>ARKUI_IMAGE_SIZE_AUTO** retains the original image aspect ratio. **ARKUI_IMAGE_SIZE_COVER** is suitable for scenarios where the image needs to fully occupy the container (such as album thumbnails). **ARKUI_IMAGE_SIZE_CONTAIN*<br> is used in scenarios where the image needs to be displayed completely (such as preview on a details page). |
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | Enumerates the image filling effects of the Image component. **ARKUI_OBJECT_FIT_CONTAIN** is applicable to scenarios where the image needs to be displayed completely. **ARKUI_OBJECT_FIT_COVER** is applicable to scenarios where the image needs to fully occupy the container. **ARKUI_OBJECT_FIT_SCALE_DOWN** is applicable to scenarios where the image needs to be scaled down when it is too large. |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images. **ARKUI_IMAGE_INTERPOLATION_LOW** is suitable for performance-sensitive scenarios with low image quality requirements (such as quick scrolling of list thumbnails). **<br>ARKUI_IMAGE_INTERPOLATION_MEDIUM** is suitable for most common scenarios. **ARKUI_IMAGE_INTERPOLATION_HIGH** is suitable for scenarios with high image quality requirements (such as image viewers). |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | Enumerates the dynamic range modes (for example, SDR/HDR). **ARKUI_DYNAMIC_RANGE_MODE_HIGH** is applicable to high-end devices that support HDR display and HDR content. **ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT** is applicable to transition scenarios where SDR needs to be compatible with. **ARKUI_DYNAMIC_RANGE_MODE_STANDARD** is applicable to common display devices. |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | Enumerates image rotation directions. It is used to adjust the display orientation of an image based on its Exif metadata or a manually specified value, which is suitable for processing the orientation of photos taken by users or correcting the display of photos. |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | Enumerates the image rendering modes. **ARKUI_IMAGE_RENDER_MODE_ORIGINAL** is applicable to scenarios where the original image color needs to be retained. **ARKUI_IMAGE_RENDER_MODE_TEMPLATE** is applicable to scenarios where a monochrome or black-and-white display is required (such as selected icons and colored icons). |

## Enum type description

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**Description**

Enumerates the image repeat patterns. This enumeration is used to control how an image is repeatedly drawn in scenarios such as backgrounds and patterns. For example, a small pattern can be used to fill the entire background in a wallpaper application.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 | The image is not repeatedly drawn.<br>**Since**: 12 |
| ARKUI_IMAGE_REPEAT_X = 1 | The image is repeatedly drawn only along the x-axis.<br>**Since**: 12 |
| ARKUI_IMAGE_REPEAT_Y = 2 | The image is repeatedly drawn only along the y-axis.<br>**Since**: 12 |
| ARKUI_IMAGE_REPEAT_XY = 3 | The image is repeatedly drawn along both axes.<br>**Since**: 12 |

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**Description**

Enumerates the image sizes. This enumeration is used to control how an image is scaled in a display area: **<br>ARKUI_IMAGE_SIZE_AUTO** retains the original image aspect ratio. **ARKUI_IMAGE_SIZE_COVER** is suitable for scenarios where the image needs to fully occupy the container (such as album thumbnails). **ARKUI_IMAGE_SIZE_CONTAIN*
* is used in scenarios where the image needs to be displayed completely (such as preview on a details page).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | The original image aspect ratio is retained.<br>**Since**: 12 |
| ARKUI_IMAGE_SIZE_COVER = 1 | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.<br>**Since**: 12 |
| ARKUI_IMAGE_SIZE_CONTAIN = 2 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.<br>**Since**: 12 |

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**Description**

Enumerates the image filling effects of the Image component. **ARKUI_OBJECT_FIT_CONTAIN** is applicable to scenarios where the image needs to be displayed completely. **ARKUI_OBJECT_FIT_COVER** is applicable to scenarios where the image needs to fully occupy the container. **ARKUI_OBJECT_FIT_SCALE_DOWN** is applicable to scenarios where the image needs to be scaled down when it is too large.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_COVER = 1 | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_AUTO = 2 | The image is scaled automatically to fit the display area.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_FILL = 3 | The image is scaled to fill the display area, and its aspect ratio is not retained.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 | The image content is displayed with its aspect ratio retained. The size is smaller than or equal to the original size.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE = 5 | The original size is retained.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START = 6 | Not resized, the image is aligned with the start edge of the top of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP = 7 | Not resized, the image is horizontally centered at the top of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END = 8 | Not resized, the image is aligned with the end edge at the top of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START = 9 | Not resized, the image is vertically centered on the start edge of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER = 10 | Not resized, the image is horizontally and vertically centered in the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END = 11 | Not resized, the image is vertically centered on the end edge of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START = 12 | Not resized, the image is aligned with the start edge at the bottom of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM = 13 | Not resized, the image is horizontally centered at the bottom of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END = 14 | Not resized, the image is aligned with the end edge at the bottom of the container.<br>**Since**: 12 |
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 | Not resized, and is used in conjunction with NODE_IMAGE_IMAGE_MATRIX.<br>**Since**: 21 |

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**Description**

Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images. **ARKUI_IMAGE_INTERPOLATION_LOW** is suitable for performance-sensitive scenarios with low image quality requirements (such as quick scrolling of list thumbnails). **<br>ARKUI_IMAGE_INTERPOLATION_MEDIUM** is suitable for most common scenarios. **ARKUI_IMAGE_INTERPOLATION_HIGH** is suitable for scenarios with high image quality requirements (such as image viewers).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | No image interpolation.<br>**Since**: 12 |
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 | Low quality interpolation.<br>**Since**: 12 |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 | Medium quality interpolation.<br>**Since**: 12 |
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 | High quality interpolation. This mode produces scaled images of the highest possible quality.<br>**Since**: 12 |

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**Description**

Enumerates the dynamic range modes (for example, SDR/HDR). **ARKUI_DYNAMIC_RANGE_MODE_HIGH** is applicable to high-end devices that support HDR display and HDR content. **ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT** is applicable to transition scenarios where SDR needs to be compatible with. **ARKUI_DYNAMIC_RANGE_MODE_STANDARD** is applicable to common display devices.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | high dynamic range mode.<br>**Since**: 21 |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 | constraint dynamic range mode.<br>**Since**: 21 |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 | standard dynamic range mode.<br>**Since**: 21 |

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**Description**

Enumerates image rotation directions. It is used to adjust the display orientation of an image based on its Exif metadata or a manually specified value, which is suitable for processing the orientation of photos taken by users or correcting the display of photos.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | Use EXIF metadata for display orientation, with support for rotation and mirroring.<br>**Since**: 21 |
| ARKUI_ORIENTATION_UP = 1 | Display original pixel data without transformation.<br>**Since**: 21 |
| ARKUI_ORIENTATION_RIGHT = 2 | Display the image after rotating it 90 degrees clockwise.<br>**Since**: 21 |
| ARKUI_ORIENTATION_DOWN = 3 | Display the image after rotating it 180 degrees clockwise.<br>**Since**: 21 |
| ARKUI_ORIENTATION_LEFT = 4 | Display the image after rotating it 270 degrees clockwise.<br>**Since**: 21 |
| ARKUI_ORIENTATION_UP_MIRRORED = 5 | Display the image after flipping it horizontally.<br>**Since**: 21 |
| ARKUI_ORIENTATION_RIGHT_MIRRORED = 6 | Display the image after flipping it horizontally and then rotating it 90 degrees clockwise.<br>**Since**: 21 |
| ARKUI_ORIENTATION_DOWN_MIRRORED = 7 | Display the image after flipping it vertically.<br>**Since**: 21 |
| ARKUI_ORIENTATION_LEFT_MIRRORED = 8 | Display the image after flipping it horizontally and then rotating it 270 degrees clockwise.<br>**Since**: 21 |

### ArkUI_ImageRenderMode

```c
enum ArkUI_ImageRenderMode
```

**Description**

Enumerates the image rendering modes. **ARKUI_IMAGE_RENDER_MODE_ORIGINAL** is applicable to scenarios where the original image color needs to be retained. **ARKUI_IMAGE_RENDER_MODE_TEMPLATE** is applicable to scenarios where a monochrome or black-and-white display is required (such as selected icons and colored icons).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | Render image pixels as they are in the original source image.<br>**Since**: 12 |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 | Render image pixels to create a monochrome template image.<br>**Since**: 12 |


