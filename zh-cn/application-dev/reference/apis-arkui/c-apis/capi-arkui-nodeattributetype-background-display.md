# 背景显示

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_BACKGROUND_COLOR

```c
NODE_BACKGROUND_COLOR
```

**描述：**

背景色属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。</li> </ul> **返回：**<br><ul> <li><b>.value[0].u32</b>：背景色数值，0xargb格式，形如 `0xFFFF0000` 表示红色。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_IMAGE

```c
NODE_BACKGROUND_IMAGE
```

**描述：**

背景色图片属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>**参数：**<br><ul><br><li><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和{@link PixelMap}资源，不支持{@link svg}图片、<br>gif和webp等类型的动图。从API version 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。</li><br><li><b>.value[0]?.i32</b>：可选值，repeat参数，参数类型[ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat)，默认值为ARKUI_IMAGE_REPEAT_NONE。</li><br><li><b>.object</b>：PixelMap图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。`.object`参数和`.string`参数二选一，不可同时设置。</li><br></ul><br>**返回：**<br><ul><br><li><b>.string</b>：图片地址。API version 22及之前版本，支持网络图片资源地址、本地图片资源地址、Base64和PixelMap资源，不支持svg图片、gif和webp等类型的动图。从API<br>version 23开始，新增支持webp和gif类型的动图，显示动图第一帧，不支持其他类型的动图。</li><br><li><b>.value[0].i32</b>：repeat参数，参数类型[ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat)。</li><br><li><b>.object</b>：PixelMap图片数据，参数类型为[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_IMAGE_SIZE

```c
NODE_BACKGROUND_IMAGE_SIZE
```

**描述：**

背景图片的宽高属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li><b>.value[0].f32</b>：图片的宽度值，取值范围`[0,+∞)`，单位为vp。</li> <li><b>.value[1].f32</b>：图片的高度值，取值范围`[0,+∞)`，单位为vp。</li> </ul> **返回：**<br><ul> <li><b>.value[0].f32</b>：图片的宽度值，单位为vp。</li> <li><b>.value[1].f32</b>：图片的高度值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE

```c
NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE
```

**描述：**

背景图片的宽高样式属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-image-h.md#arkui_imagesize)枚举值。</li> </ul> **返回：**<br><ul> <li><b>.value[0].i32</b>：背景图片的宽高样式，取[ArkUI_ImageSize](capi-image-h.md#arkui_imagesize)枚举值。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_BLUR_STYLE

```c
NODE_BACKGROUND_BLUR_STYLE
```

**描述：**

设置组件背景模糊样式，模糊效果应用于组件背景层与内容层之间，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li>.value[0].i32：表示模糊类型，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。</li> <li>.value[1]?.i32：表示深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。不传入时默认跟随系统深浅色模式设置。</li> <li>.value[2]?.i32：表示取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。不传入时默认取色模式为自适应取色，当需要指定固定取色方式时传入此参数。</li> <li>.value[3]?.f32：表示模糊效果程度，取[0.0,1.0]范围内的值。0.0表示无模糊，1.0表示最大模糊效果。不传入时默认值为1.0，当需要调整内容模糊强度时传入此参数。</li> <li>.value[4]?.f32：表示灰阶模糊起始边界，对黑色提亮到哪个位置，有效值范围0-127。参数值越大调整效果越明显。</li> <li>.value[5]?.f32：表示灰阶模糊终点边界，对白色压暗到哪个位置，有效值范围0-127。参数值越大调整效果越明显。</li> </ul> **返回：**<br><ul> <li>.value[0].i32：表示模糊类型，取[ArkUI_BlurStyle](capi-native-type-h.md#arkui_blurstyle)枚举值。</li> <li>.value[1].i32：表示深浅色模式，取[ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode)枚举值。枚举值包括：ARKUI_COLOR_MODE_LIGHT（浅色模式）、ARKUI_COLOR_MODE_DARK（深色模式）。</li> <li>.value[2].i32：表示取色模式，取[ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor)枚举值。</li> <li>.value[3].f32：表示模糊效果程度，取[0.0,1.0]范围内的值。</li> <li>.value[4].f32：表示灰阶模糊起始边界。</li> <li>.value[5].f32：表示灰阶模糊终点边界。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_IMAGE_POSITION

```c
NODE_BACKGROUND_IMAGE_POSITION
```

**描述：**

背景图在组件中显示位置，即相对于组件左上角的坐标，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li>.value[0].f32</b>：x轴位置，单位为px。</li> <li>.value[1].f32</b>：y轴位置，单位为px。</li> <li>.value[2]?.i32</b>：可选值，对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_TOP_START。该参数从API version 21开始支持。</li> <li>.value[3]?.i32</b>：可选值，布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。多数场景下建议设置为AUTO， 由系统自动处理布局方向；若需要固定方向，可设置为LTR或RTL。该参数从API version 21开始支持。</li> </ul> **返回：**<br><ul> <li>.value[0].f32</b>：x轴位置，单位为px。</li> <li>.value[1].f32</b>：y轴位置，单位为px。</li> <li>.value[2].i32</b>：对齐方式，参数类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。该返回值从API version 21开始支持。</li> <li>.value[3].i32</b>：布局方向，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)。该返回值从API version 21开始支持。</li> </ul>

**起始版本：** 12

### NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE

```c
NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100
```

**描述：**

设置背景图在拉伸时可调整大小的属性，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li>.value[0].f32：图片左部拉伸时，图片的像素值保持不变，单位为vp，默认值0。</li> <li>.value[1].f32：图片顶部拉伸时，图片的像素值保持不变，单位为vp，默认值0。</li> <li>.value[2].f32：图片右部拉伸时，图片的像素值保持不变，单位为vp，默认值0。</li> <li>.value[3].f32：图片底部拉伸时，图片的像素值保持不变，单位为vp，默认值0。</li> </ul> **返回：**<br><ul> <li>.value[0].f32：图片左部拉伸时，图片的像素值保持不变，单位为vp。</li> <li>.value[1].f32：图片顶部拉伸时，图片的像素值保持不变，单位为vp。</li> <li>.value[2].f32：图片右部拉伸时，图片的像素值保持不变，单位为vp。</li> <li>.value[3].f32：图片底部拉伸时，图片的像素值保持不变，单位为vp。</li> </ul>

**起始版本：** 19


