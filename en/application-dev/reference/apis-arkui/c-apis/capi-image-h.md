# image.h

## Overview

Defines **Image** node types for **NativeNode** APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | Enumerates the image repeat patterns. |
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | Enumerates the image sizes. |
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | Enumerates the image filling effects of the {@link Image} component. |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images. |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut. |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | Enumerates image rotation directions. |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | Enumerates the image rendering modes. |

## Enum type description

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**Description**

Enumerates the image repeat patterns.

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

Enumerates the image sizes.

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

Enumerates the image filling effects of the {@link Image} component.

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

Enumerates the image interpolation effects. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images.

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

Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut.

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

Enumerates image rotation directions.

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

Enumerates the image rendering modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 |  |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 |  |


