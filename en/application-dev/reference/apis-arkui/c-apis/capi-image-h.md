# image.h

## Overview

Defines **Image** node types for **NativeNode** APIs, which are used to create and configure **Image**<br>components in native applications, including image repetition patterns, width and height styles, filling effects, interpolation optimization, dynamic ranges, rotation directions, and render modes.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

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
| ARKUI_IMAGE_REPEAT_NONE = 0 |  |
| ARKUI_IMAGE_REPEAT_X = 1 |  |
| ARKUI_IMAGE_REPEAT_Y = 2 |  |
| ARKUI_IMAGE_REPEAT_XY = 3 |  |

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**Description**

Enumerates the image sizes. This enumeration is used to control how an image is scaled in a display area: **<br>ARKUI_IMAGE_SIZE_AUTO** retains the original image aspect ratio. **ARKUI_IMAGE_SIZE_COVER** is suitable for scenarios where the image needs to fully occupy the container (such as album thumbnails). **ARKUI_IMAGE_SIZE_CONTAIN*<br> is used in scenarios where the image needs to be displayed completely (such as preview on a details page).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 |  |
| ARKUI_IMAGE_SIZE_COVER = 1 |  |
| ARKUI_IMAGE_SIZE_CONTAIN = 2 |  |

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
| ARKUI_OBJECT_FIT_CONTAIN = 0 |  |
| ARKUI_OBJECT_FIT_COVER = 1 |  |
| ARKUI_OBJECT_FIT_AUTO = 2 |  |
| ARKUI_OBJECT_FIT_FILL = 3 |  |
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 |  |
| ARKUI_OBJECT_FIT_NONE = 5 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START = 6 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP = 7 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END = 8 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START = 9 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER = 10 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END = 11 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START = 12 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM = 13 |  |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END = 14 |  |
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 |  |

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
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 |  |
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 |  |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 |  |
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 |  |

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
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 |  |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 |  |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 |  |

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
| ARKUI_ORIENTATION_AUTO = 0 |  |
| ARKUI_ORIENTATION_UP = 1 |  |
| ARKUI_ORIENTATION_RIGHT = 2 |  |
| ARKUI_ORIENTATION_DOWN = 3 |  |
| ARKUI_ORIENTATION_LEFT = 4 |  |
| ARKUI_ORIENTATION_UP_MIRRORED = 5 |  |
| ARKUI_ORIENTATION_RIGHT_MIRRORED = 6 |  |
| ARKUI_ORIENTATION_DOWN_MIRRORED = 7 |  |
| ARKUI_ORIENTATION_LEFT_MIRRORED = 8 |  |

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
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 |  |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 |  |


