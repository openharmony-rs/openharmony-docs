# 图片

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_SRC

```c
NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE
```

**描述：**

Defines the image source of the <Image> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_OBJECT_FIT

```c
NODE_IMAGE_OBJECT_FIT
```

**描述：**

Defines how the image is resized to fit its container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of<br>{@link ArkUI_ObjectFit}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of<br>{@link ArkUI_ObjectFit}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_INTERPOLATION

```c
NODE_IMAGE_INTERPOLATION
```

**描述：**

Defines the interpolation effect of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: interpolation effect of the image. The value is an enum of<br>{@link ArkUI_ImageInterpolation}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: interpolation effect of the image. The value is an enum of<br>{@link ArkUI_ImageInterpolation}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_OBJECT_REPEAT

```c
NODE_IMAGE_OBJECT_REPEAT
```

**描述：**

Defines how the image is repeated. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: how the image is repeated. The value is an enum of {@link ArkUI_ImageRepeat}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: how the image is repeated. The value is an enum of {@link ArkUI_ImageRepeat}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_COLOR_FILTER

```c
NODE_IMAGE_COLOR_FILTER
```

**描述：**

Defines the color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32 to .value[19].f32: filter matrix array.</li><br><li>.size: 5 x 4 filter array size.</li><br><li>.object: the pointer to OH_Drawing_ColorFilter. Either .value or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_AUTO_RESIZE

```c
NODE_IMAGE_AUTO_RESIZE
```

**描述：**

Defines the auto resize attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to resize the image source.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to resize the image source.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ALT

```c
NODE_IMAGE_ALT
```

**描述：**

Defines the placeholder image source. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_DRAGGABLE

```c
NODE_IMAGE_DRAGGABLE
```

**描述：**

Defines whether the image is draggable. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the image is draggable. The value <b>true</b> means that the image is draggable.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the image is draggable.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_RENDER_MODE

```c
NODE_IMAGE_RENDER_MODE
```

**描述：**

Defines the image rendering mode. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_ImageRenderMode}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_ImageRenderMode}.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_FIT_ORIGINAL_SIZE

```c
NODE_IMAGE_FIT_ORIGINAL_SIZE
```

**描述：**

Defines whether the image display size follows the image source size. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_FILL_COLOR

```c
NODE_IMAGE_FILL_COLOR
```

**描述：**

Defines the fill color of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: fill color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: fill color, in 0xARGB format.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_RESIZABLE

```c
NODE_IMAGE_RESIZABLE
```

**描述：**

图片拉伸时，支持通过设置边框大小或者使用矩阵方格对象调整其大小，1）设置边框大小可以设置left/top/right/bottom宽度，2）设置矩阵方格对象：该对象是通过图形侧的接口创建，并将对象地址传入。 接口调用时需要保证设置和获取的参数类型是相同的。

**起始版本：** 12

### NODE_IMAGE_SYNC_LOAD

```c
NODE_IMAGE_SYNC_LOAD = 4012
```

**描述：**

定义Image是否同步加载 这个属性包含设置，重置，获取接口

**起始版本：** 20

### NODE_IMAGE_SOURCE_SIZE

```c
NODE_IMAGE_SOURCE_SIZE = 4013
```

**描述：**

定义图片的解码尺寸属性。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数ArkUI_AttributeItem格式：<br> .value[0].i32 表示图片解码的宽，单位px。<br> .value[1].i32 表示图片解码的高，单位px。<br> 属性获取方法返回值ArkUI_AttributeItem格式：<br> .value[0].i32 表示图片解码的宽，单位px。<br> .value[1].i32 表示图片解码的高，单位px。

**起始版本：** 21

### NODE_IMAGE_IMAGE_MATRIX

```c
NODE_IMAGE_IMAGE_MATRIX = 4014
```

**描述：**

支持使用浮点数实现仿射图像变换。 该属性可以通过API根据需要设置、重置和获取。 set和get的参数类型应该是相同的。<br> 设置属性{@link ArkUI_AttributeItem}格式：<br>.value[0....f32表示16个浮点数。<br>返回值{@link ArkUI_AttributeItem}的格式为： .value[0....f32表示16个浮点数。

**起始版本：** 21

### NODE_IMAGE_MATCH_TEXT_DIRECTION

```c
NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015
```

**描述：**

Defines the image follow text direction attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the image follows the text direction.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the image follows the text direction.</li> </ul>

**起始版本：** 21

### NODE_IMAGE_COPY_OPTION

```c
NODE_IMAGE_COPY_OPTION = 4016
```

**描述：**

定义图片复制粘贴属性。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数ArkUI_AttributeItem格式：<br> .value[0].i32：复制粘贴方式ArkUI_CopyOptions，默认值为ARKUI_COPY_OPTIONS_NONE；<br> 属性获取方法返回值ArkUI_AttributeItem格式：<br> .value[0].i32：复制粘贴方式ArkUI_CopyOptions。

**起始版本：** 21

### NODE_IMAGE_ENABLE_ANALYZER

```c
NODE_IMAGE_ENABLE_ANALYZER = 4017
```

**描述：**

Defines the image AI analysis enable attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable AI analysis for the image.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable AI analysis for the image.</li> </ul>

**起始版本：** 21

### NODE_IMAGE_DYNAMIC_RANGE_MODE

```c
NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018
```

**描述：**

定义图片显示动态范围属性。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数ArkUI_AttributeItem格式：<br> .value[0].i32：动态范围类型ArkUI_DynamicRangeMode，默认值为<br> ARKUI_DYNAMIC_RANGE_MODE_STANDARD；<br> 属性获取方法返回值ArkUI_AttributeItem格式：<br> .value[0].i32：动态范围类型ArkUI_DynamicRangeMode。

**起始版本：** 21

### NODE_IMAGE_HDR_BRIGHTNESS

```c
NODE_IMAGE_HDR_BRIGHTNESS = 4019
```

**描述：**

定义图片显示动态范围的亮度属性。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数ArkUI_AttributeItem格式：<br> .value[0].f32：动态范围亮度，值的范围[0, 1]。<br> 属性获取方法返回值ArkUI_AttributeItem格式：<br> .value[0].f32：动态范围亮度，值的范围[0, 1]。

**起始版本：** 21

### NODE_IMAGE_ORIENTATION

```c
NODE_IMAGE_ORIENTATION = 4020
```

**描述：**

定义图片显示方向属性。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数ArkUI_AttributeItem格式：<br> .value[0].i32：动态范围类型ArkUI_Orientation，默认值为ARKUI_ORIENTATION_UP；<br> 属性获取方法返回值ArkUI_AttributeItem格式：<br> .value[0].i32：动态范围类型ArkUI_Orientation。

**起始版本：** 21

### NODE_IMAGE_SUPPORT_SVG2

```c
NODE_IMAGE_SUPPORT_SVG2 = 4021
```

**描述：**

Defines the range of SVG parsing capabilities supported through an enable switch. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: enable switch.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: enable switch.</li> </ul>

**起始版本：** 21

### NODE_IMAGE_CONTENT_TRANSITION

```c
NODE_IMAGE_CONTENT_TRANSITION = 4022
```

**描述：**

Set the animation effect for the image content transformation. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:<br>.object: The parameter type is {@link ArkUI_ContentTransitionEffect}.<br>Format of the return value {@link ArkUI_AttributeItem}:<br>.object: The parameter type is {@link ArkUI_ContentTransitionEffect}.

**起始版本：** 21

### NODE_IMAGE_ALT_PLACEHOLDER

```c
NODE_IMAGE_ALT_PLACEHOLDER = 4023
```

**描述：**

Defines the placeholder image during loading process. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**起始版本：** 22

### NODE_IMAGE_ALT_ERROR

```c
NODE_IMAGE_ALT_ERROR = 4024
```

**描述：**

Defines the placeholder image when loading fails. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**起始版本：** 22

### NODE_IMAGE_ANTIALIASED

```c
NODE_IMAGE_ANTIALIASED = 4025
```

**描述：**

通过开关配置图片边缘抗锯齿使能；true-开启抗锯齿，false-不开启，默认不开启抗锯齿。

**起始版本：** 23


