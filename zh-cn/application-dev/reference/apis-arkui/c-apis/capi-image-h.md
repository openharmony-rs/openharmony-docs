# image.h

## 概述

为NativeNode API提供Image节点类型定义。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | 定义图片重复铺设枚举值。用于控制图片在背景、图案等场景下的重复铺设方式，例如壁纸应用中以小图案铺满背景。 |
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | 定义图片宽高样式。 |
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | 定义Image组件的图片填充效果。ARKUI_OBJECT_FIT_CONTAIN适用于需要完整显示图片的场景，ARKUI_OBJECT_FIT_COVER适用于需要充满容器的场景，ARKUI_OBJECT_FIT_SCALE_DOWN适用于图片过大时缩小显示的场景。 |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | 定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。ARKUI_IMAGE_INTERPOLATION_LOW适用于性能敏感、对画质要求不高的场景（如列表缩略图快速滑动），ARKUI_IMAGE_INTERPOLATION_MEDIUM适用于大多数常规场景，ARKUI_IMAGE_INTERPOLATION_HIGH适用于对画质要求高的场景（如图片查看器）。 |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | 定义图像动态范围模式（例如：SDR/HDR）。ARKUI_DYNAMIC_RANGE_MODE_HIGH适用于支持HDR显示的高端设备及HDR内容，ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT适用于需要兼容SDR的过渡场景，ARKUI_DYNAMIC_RANGE_MODE_STANDARD适用于普通显示设备。 |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | 定义图像旋转方向。用于根据图片EXIF元数据或手动指定来调整图片显示方向，适用于处理用户拍摄照片方向、校正照片显示等场景。 |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | 定义图片渲染模式。ARKUI_IMAGE_RENDER_MODE_ORIGINAL适用于需要保留原图颜色的场景，ARKUI_IMAGE_RENDER_MODE_TEMPLATE适用于需要单色/黑白显示的场景（如选中态图标、着色图标）。 |

## 枚举类型说明

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**描述：**

定义图片重复铺设枚举值。用于控制图片在背景、图案等场景下的重复铺设方式，例如壁纸应用中以小图案铺满背景。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 |  |
| ARKUI_IMAGE_REPEAT_X = 1 |  |
| ARKUI_IMAGE_REPEAT_Y = 2 |  |
| ARKUI_IMAGE_REPEAT_XY = 3 |  |

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**描述：**

定义图片宽高样式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 |  |
| ARKUI_IMAGE_SIZE_COVER = 1 |  |
| ARKUI_IMAGE_SIZE_CONTAIN = 2 |  |

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**描述：**

定义Image组件的图片填充效果。ARKUI_OBJECT_FIT_CONTAIN适用于需要完整显示图片的场景，ARKUI_OBJECT_FIT_COVER适用于需要充满容器的场景，ARKUI_OBJECT_FIT_SCALE_DOWN适用于图片过大时缩小显示的场景。

**起始版本：** 12

| 枚举项 | 描述 |
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

**描述：**

定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。ARKUI_IMAGE_INTERPOLATION_LOW适用于性能敏感、对画质要求不高的场景（如列表缩略图快速滑动），ARKUI_IMAGE_INTERPOLATION_MEDIUM适用于大多数常规场景，ARKUI_IMAGE_INTERPOLATION_HIGH适用于对画质要求高的场景（如图片查看器）。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 |  |
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 |  |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 |  |
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 |  |

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**描述：**

定义图像动态范围模式（例如：SDR/HDR）。ARKUI_DYNAMIC_RANGE_MODE_HIGH适用于支持HDR显示的高端设备及HDR内容，ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT适用于需要兼容SDR的过渡场景，ARKUI_DYNAMIC_RANGE_MODE_STANDARD适用于普通显示设备。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 |  |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 |  |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 |  |

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**描述：**

定义图像旋转方向。用于根据图片EXIF元数据或手动指定来调整图片显示方向，适用于处理用户拍摄照片方向、校正照片显示等场景。

**起始版本：** 21

| 枚举项 | 描述 |
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

**描述：**

定义图片渲染模式。ARKUI_IMAGE_RENDER_MODE_ORIGINAL适用于需要保留原图颜色的场景，ARKUI_IMAGE_RENDER_MODE_TEMPLATE适用于需要单色/黑白显示的场景（如选中态图标、着色图标）。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 |  |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 |  |


