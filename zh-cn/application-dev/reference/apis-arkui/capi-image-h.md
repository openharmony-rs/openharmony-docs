# image.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

为NativeNode API提供Image节点类型定义，用于在Native应用中创建和配置Image组件，支持图片重复铺设、宽高样式、填充效果、插值优化、动态范围、旋转方向和渲染模式等多种属性配置。

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
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | 定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。|
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | 定义图像动态范围模式（例如：SDR/HDR）。 |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | 定义图像旋转方向。 |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | 定义图片渲染模式。 |

## 枚举类型说明

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**描述**

定义图片重复铺设枚举值。用于控制图片在背景、图案等场景下的重复铺设方式，例如壁纸应用中以小图案铺满背景。

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

定义图片宽高样式。用于控制图片在显示区域内的缩放方式：ARKUI_IMAGE_SIZE_AUTO保持原图比例；ARKUI_IMAGE_SIZE_COVER适用于需要充满容器的场景（如相册缩略图）；ARKUI_IMAGE_SIZE_CONTAIN适用于需要完整显示图片的场景（如详情页预览）。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | 保持原图的比例不变。 |
| ARKUI_IMAGE_SIZE_COVER = 1 | 保持宽高比进行缩小或者放大，使得图片的宽度和高度都大于或等于显示边界的宽度和高度（可能超出边界部分被裁剪）。 |
| ARKUI_IMAGE_SIZE_CONTAIN = 2 | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。 |

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**描述**

定义[Image](arkui-ts/ts-basic-components-image.md)组件的图片填充效果。ARKUI_OBJECT_FIT_CONTAIN适用于需要完整显示图片的场景，ARKUI_OBJECT_FIT_COVER适用于需要充满容器的场景，ARKUI_OBJECT_FIT_SCALE_DOWN适用于图片过大时缩小显示的场景。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | 保持宽高比进行缩小或者放大，使得图片完全显示在显示边界内。 |
| ARKUI_OBJECT_FIT_COVER = 1 | 保持宽高比进行缩小或者放大，使得图片的宽度和高度都大于或等于显示边界的宽度和高度（可能超出边界部分被裁剪）。 |
| ARKUI_OBJECT_FIT_AUTO = 2 | 自适应显示。 |
| ARKUI_OBJECT_FIT_FILL = 3 | 不保持宽高比进行放大缩小，使得图片充满显示边界。 |
| ARKUI_OBJECT_FIT_SCALE_DOWN = 4 | 保持宽高比显示，图片缩小或者保持不变。 |
| ARKUI_OBJECT_FIT_NONE = 5 | 保持原有尺寸显示。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START = 6 | 图片大小不变，在Image组件中顶部起始端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP = 7 | 图片大小不变，在Image组件中顶部横向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END = 8 | 图片大小不变，在Image组件中顶部尾端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START = 9 | 图片大小不变，在Image组件中起始端纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER = 10 | 图片大小不变，在Image组件中横向和纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END = 11 | 图片大小不变，在Image组件中尾端纵向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START = 12 | 图片大小不变，在Image组件中底部起始端对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM = 13 | 图片大小不变，在Image组件中底部横向居中对齐。 |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END = 14 | 图片大小不变，在Image组件中底部尾端对齐。 |
| ARKUI_OBJECT_FIT_NONE_MATRIX = 15 | 不改变图像原始大小，在Image组件中需要配合[ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype)中的NODE_IMAGE_IMAGE_MATRIX使用，通过矩阵变换控制图像的显示效果（如缩放、旋转、平移等）。<br/>**起始版本：** 21 |

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**描述**

定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。ARKUI_IMAGE_INTERPOLATION_LOW适用于性能敏感、对画质要求不高的场景（如列表缩略图快速滑动），ARKUI_IMAGE_INTERPOLATION_MEDIUM适用于大多数常规场景，ARKUI_IMAGE_INTERPOLATION_HIGH适用于对画质要求高的场景（如图片查看器）。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | 不使用图片插值。 |
| ARKUI_IMAGE_INTERPOLATION_LOW = 1 | 低质量图片插值。计算量小、渲染速度快，适用于对画质要求不高或需要快速渲染大量图片的场景。 |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM = 2 | 中等质量图片插值。在计算量与图像质量之间取得平衡，适用于大多数常规显示场景。 |
| ARKUI_IMAGE_INTERPOLATION_HIGH = 3 | 高质量图片插值，插值质量最高。计算量较大、资源消耗较高，适用于对图像质量要求较高的展示场景。 |

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**描述**

定义图像动态范围模式（例如：SDR/HDR）。ARKUI_DYNAMIC_RANGE_MODE_HIGH适用于支持HDR显示的高端设备及HDR内容，ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT适用于需要兼容SDR的过渡场景，ARKUI_DYNAMIC_RANGE_MODE_STANDARD适用于普通显示设备。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | 高动态范围（High Dynamic Range，简称HDR），表示图片中显示亮度（brightness）的最小值和最大值的范围（典型最大亮度可达1000尼特以上），范围越大，图像的亮度动态范围越接近人眼在真实环境中的感知范围，在太亮的环境下不会产生过曝（一片白），太暗的环境下不会产生过暗的效果（一片黑）。 |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT = 1 | 受限的高动态范围，包含比SDR更丰富的亮度和色彩，但不是完整的HDR，一般用于需要兼容SDR的情况。 |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD = 2 | 标准动态范围（Standard Dynamic Range，简称SDR），表示亮度范围有限，一般在0~100尼特（亮度单位）左右，明暗对比度较小，暗部容易糊成黑，亮部容易过曝。 |

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**描述**

定义图像旋转方向。用于根据图片EXIF元数据或手动指定来调整图片显示方向，适用于处理用户拍摄照片方向、校正照片显示等场景。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | 读取图片携带的EXIF元数据作为显示方向，支持旋转和镜像。 |
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

定义图片渲染模式。ARKUI_IMAGE_RENDER_MODE_ORIGINAL适用于需要保留原图颜色的场景，ARKUI_IMAGE_RENDER_MODE_TEMPLATE适用于需要单色/黑白显示的场景（如选中态图标、着色图标）。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | 原色渲染模式。 |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE = 1 | 黑白渲染模式。 |
