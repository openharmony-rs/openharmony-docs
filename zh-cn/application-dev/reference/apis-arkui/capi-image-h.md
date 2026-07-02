# image.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

为NativeNode API提供Image节点类型定义。

**引用文件：** <arkui/node_attributes/image.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | 定义图片重复铺设枚举值。 |
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | 定义图片宽高样式。 |
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | 定义[Image](arkui-ts/ts-basic-components-image.md)组件的图片填充效果。 |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | 定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。 |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | 定义图像动态范围模式（例如：SDR/HDR），用于控制图像的明暗与色彩显示范围。 |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | 定义图像旋转方向。 |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | 定义图片渲染模式。 |

## 枚举类型说明

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**描述**

定义图片重复铺设枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 | 不重复。 |
| ARKUI_IMAGE_REPEAT_X = 1 | 在X轴方向重复。 |
| ARKUI_IMAGE_REPEAT_Y = 2 | 在Y轴方向重复。 |
| ARKUI_IMAGE_REPEAT_XY = 3 | 在X轴和Y轴方向重复。 |

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**描述**

定义图片宽高样式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | 保持原图的比例不变。 |
| ARKUI_IMAGE_SIZE_COVER = 1 | 保持宽高比进行缩小或者放大，使得图片两边都大于或等于显示边界。 |
| ARKUI_IMAGE_SIZE_CONTAIN = 2 | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。 |

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**描述**

定义[Image](arkui-ts/ts-basic-components-image.md)组件的图片填充效果。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。 |
| ARKUI_OBJECT_FIT_COVER = 1 | 保持宽高比进行缩小或者放大，使得图片两边都大于或等于显示边界。 |
| ARKUI_OBJECT_FIT_AUTO = 2 | 自适应显示。 |
| ARKUI_OBJECT_FIT_FILL = 3 | 不保持宽高比进行放大缩小，使得图片充满显示边界。 |
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 | 保持宽高比显示，图片缩小或者保持不变。 |
| ARKUI_OBJECT_FIT_NONE = 5 | 保持原有尺寸显示。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START = 6 | 图片大小不变，在image组件中顶部起始端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP = 7 | 图片大小不变，在image组件中顶部横向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END = 8 | 图片大小不变，在image组件中顶部尾端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START = 9 | 图片大小不变，在image组件中起始端纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER = 10 | 图片大小不变，在image组件中横向和纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END = 11 | 图片大小不变，在image组件中尾端纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START = 12 | 图片大小不变，在image组件中底部起始端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM = 13 | 图片大小不变，在image组件中底部横向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END = 14 | 图片大小不变，在image组件中底部尾端对齐。 |
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 | 不改变图像原始大小，需要配合[ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype)中的NODE_IMAGE_IMAGE_MATRIX使用。<br/>**起始版本：** 21 |

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**描述**

定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | 不使用图片插值。 |
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 | 低图片插值。 |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 | 中图片插值。 |
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 | 高图片插值，插值质量最高。 |

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**描述**

定义图像动态范围模式（例如：SDR/HDR），用于控制图像的明暗与色彩显示范围。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | 高动态范围（High Dynamic Range，简称HDR），表示图片中显示亮度（brightness）的最小值和最大值的范围，范围越大图像的亮度表达更逼近真实环境，在太亮的环境下不会产生过曝（一片白），太暗的环境下不会产生过暗的效果（一片黑）。 |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 | 受限的高动态范围，包含比SDR更丰富的亮度和色彩，但不是完整的HDR，一般用于需要兼容SDR的情况。 |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 | 标准动态范围（Standard Dynamic Range，简称SDR），表示亮度范围有限，一般在0~100尼特（亮度单位）左右，明暗对比度较小，暗部容易糊成黑，亮部容易过曝。 |

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**描述**

定义图像旋转方向。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | 读取图片携带的EXIF元数据作为显示方向，支持旋转和镜像。EXIF（Exchangeable image file format）是专门为数码相机的照片设定的文件格式，可以记录数码照片的属性信息和拍摄数据。 |
| ARKUI_ORIENTATION_UP = 1 | 默认按照当前图片的像素数据进行显示，不做任何处理。 |
| ARKUI_ORIENTATION_RIGHT = 2 | 将当前图片顺时针旋转90度后显示。 |
| ARKUI_ORIENTATION_DOWN = 3 | 将当前图片顺时针旋转180度后显示。 |
| ARKUI_ORIENTATION_LEFT = 4 | 将当前图片顺时针旋转270度后显示。 |
| ARKUI_ORIENTATION_UP_MIRRORED = 5 | 将当前图片水平翻转后显示。 |
| ARKUI_ORIENTATION_RIGHT_MIRRORED = 6 | 将当前图片水平翻转再顺时针旋转90度后显示。 |
| ARKUI_ORIENTATION_DOWN_MIRRORED = 7 | 将当前图片垂直翻转后显示。 |
| ARKUI_ORIENTATION_LEFT_MIRRORED = 8 | 将当前图片水平翻转再顺时针旋转270度后显示。 |

### ArkUI_ImageRenderMode

```c
enum ArkUI_ImageRenderMode
```

**描述**

定义图片渲染模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | 原色渲染模式。 |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 | 黑白渲染模式。 |
