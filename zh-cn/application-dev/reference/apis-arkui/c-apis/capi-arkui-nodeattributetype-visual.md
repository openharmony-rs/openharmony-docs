# 视效属性

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TRANSLATE

```c
NODE_TRANSLATE
```

**描述：**

设置组件平移，支持属性设置，属性重置和属性获取接口。 与NODE_TRANSLATE_WITH_PERCENT互斥，同一组件只能使用一种平移属性设置方式。 如同时设置NODE_TRANSLATE和NODE_TRANSLATE_WITH_PERCENT，后者设置的值将覆盖前者。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：x轴移动距离，单位vp，默认值0。</li><br><li>.value[1].f32：y轴移动距离，单位vp，默认值0。</li><br><li>.value[2].f32：z轴移动距离，单位vp，默认值0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：x轴移动距离，单位vp。</li><br><li>.value[1].f32：y轴移动距离，单位vp。</li><br><li>.value[2].f32：z轴移动距离，单位vp。</li> </ul>

**起始版本：** 12

### NODE_SCALE

```c
NODE_SCALE
```

**描述：**

设置组件缩放，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：x轴的缩放系数，默认值1。值为0时组件不可见，负值时组件沿x轴翻转显示。</li><br><li>.value[1].f32：y轴的缩放系数，默认值1。值为0时组件不可见，负值时组件沿y轴翻转显示。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：x轴的缩放系数。</li><br><li>.value[1].f32：y轴的缩放系数。</li> </ul>

**起始版本：** 12

### NODE_ROTATE

```c
NODE_ROTATE
```

**描述：**

设置组件旋转，支持属性设置，属性重置和属性获取接口。 与NODE_ROTATE_ANGLE互斥，同一组件只能使用一种旋转属性设置方式。 如同时设置NODE_ROTATE和NODE_ROTATE_ANGLE，后者设置的值将覆盖前者。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：旋转轴向量x坐标，默认值0。</li><br><li>.value[1].f32：旋转轴向量y坐标，默认值0。</li><br><li>.value[2].f32：旋转轴向量z坐标，默认值0。</li><br><li>.value[3].f32：旋转角度，单位为度（°），默认值0。</li><br><li>.value[4].f32：视距，即视点到z=0平面的距离，单位vp，默认值0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：旋转轴向量x坐标。</li><br><li>.value[1].f32：旋转轴向量y坐标。</li><br><li>.value[2].f32：旋转轴向量z坐标。</li><br><li>.value[3].f32：旋转角度，单位为度（°）。</li><br><li>.value[4].f32：视距，即视点到z=0平面的距离，单位vp。</li> </ul>

**起始版本：** 12

### NODE_BRIGHTNESS

```c
NODE_BRIGHTNESS
```

**描述：**

设置组件高光效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：亮度值，默认值1.0，推荐取值范围[0, 2.0]。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：亮度值，1.0表示原始亮度，推荐取值范围[0, 2.0]。</li> </ul>

**起始版本：** 12

### NODE_SATURATION

```c
NODE_SATURATION
```

**描述：**

设置组件饱和度效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：饱和度值，默认值1.0，推荐取值范围[0, 50.0)，传入负值时按0处理。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：饱和度值，1.0表示原始饱和度，推荐取值范围[0, 50.0)。</li> </ul>

**起始版本：** 12

### NODE_BLUR

```c
NODE_BLUR
```

**描述：**

设置组件内容模糊效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：模糊半径，取值范围[0, +∞)，模糊半径越大越模糊，为0时不模糊，小于0时按0处理且不会返回错误码。单位vp，默认值0.0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：模糊半径，模糊半径越大越模糊，为0时不模糊。单位vp。</li> </ul>

**起始版本：** 12

### NODE_LINEAR_GRADIENT

```c
NODE_LINEAR_GRADIENT
```

**描述：**

设置组件颜色渐变效果，支持属性设置，属性重置和属性获取接口。 与NODE_SWEEP_GRADIENT、NODE_RADIAL_GRADIENT互斥，同一组件只能设置一种渐变类型。 如同时设置多种渐变属性，后设置的渐变类型将覆盖先前设置的渐变效果。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：线性渐变的起始角度，单位度（°），0点方向顺时针旋转为正向角度，默认值180。当{@link ArkUI_LinearGradientDirection}为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle属性生效，否则按direction为主要布局方式。</li><br><li>.value[1].i32：线性渐变的方向，参数类型为{@link ArkUI_LinearGradientDirection}。设置为非ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle不生效。</li><br><li>.value[2].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色，默认值0。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li><br><li>colors：渐变色颜色。</li><br><li>stops：渐变位置。</li><br><li>size：颜色个数。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：线性渐变的起始角度，单位为度（°）。当为ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，angle为设置值，其他情况均为默认值。</li><br><li>.value[1].i32：线性渐变的方向，取{@link ArkUI_LinearGradientDirection}枚举值。</li><br><li>.value[2].i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li> <li>colors：渐变色颜色。</li> <li>stops：渐变位置。</li> <li>size：颜色个数。</li> </ul>

**起始版本：** 12

### NODE_OPACITY

```c
NODE_OPACITY
```

**描述：**

透明度属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：透明度数值，默认值为1，取值范围为[0, 1]。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：透明度数值，取值范围为0到1。</li> </ul>

**起始版本：** 12

### NODE_CLIP

```c
NODE_CLIP
```

**描述：**

组件裁剪属性，控制是否对子组件超出当前组件范围外的区域进行裁剪，支持属性设置，属性重置和属性获取接口。 与NODE_CLIP_SHAPE互斥，同一组件只能使用一种裁剪属性设置方式。NODE_CLIP提供简单的布尔裁剪，NODE_CLIP_SHAPE提供指定形状的裁剪，同时设置时后者将覆盖前者。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32：控制是否对子组件超出当前组件范围外的区域进行裁剪，0表示不裁剪，1表示裁剪。默认为不裁剪。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：控制是否对子组件超出当前组件范围外的区域进行裁剪，0表示不裁剪，1表示裁剪。</li> </ul>

**起始版本：** 12

### NODE_CLIP_SHAPE

```c
NODE_CLIP_SHAPE
```

**描述：**

组件上指定形状的裁剪，支持属性设置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br>1.rect类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_RECTANGLE。</li><br><li>.value[1].f32：矩形宽度，单位为vp。</li><br><li>.value[2].f32：矩形高度，单位为vp。</li><br><li>.value[3].f32：矩形圆角宽度，单位为vp。</li><br><li>.value[4].f32：矩形圆角高度，单位为vp。</li><br><li>.value[5]?.f32：矩形形状的左上圆角半径，单位为vp，默认值0。</li><br><li>.value[6]?.f32：矩形形状的左下圆角半径，单位为vp，默认值0。</li><br><li>.value[7]?.f32：矩形形状的右上圆角半径，单位为vp，默认值0。</li><br><li>.value[8]?.f32：矩形形状的右下圆角半径，单位为vp，默认值0。</li><br><li>.object：参数类型为{@link ArkUI_RenderNodeClipOption}，矩形形状的坐标偏移量，在仅传入.object参数时生效。</li><br></ul><br>2.circle类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_CIRCLE。</li><br><li>.value[1].f32：圆形宽度，单位为vp。</li><br><li>.value[2].f32：圆形高度，单位为vp。</li><br><li>.object：参数类型为{@link ArkUI_RenderNodeClipOption}，圆形坐标偏移量，在仅传入.object参数时生效。</li><br></ul><br>3.ellipse类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_ELLIPSE。</li><br><li>.value[1].f32：椭圆形宽度，单位为vp。</li><br><li>.value[2].f32：椭圆形高度，单位为vp。</li><br><li>.object：参数类型为{@link ArkUI_RenderNodeClipOption}，椭圆形坐标偏移量，在仅传入.object参数时生效。</li><br></ul><br>4.path类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_PATH。</li><br><li>.value[1].f32：路径宽度，单位为vp。</li><br><li>.value[2].f32：路径高度，单位为vp。</li><br><li>.string：路径绘制的命令字符串，格式遵循SVG path数据语法，如'M0 0 L100 100 Z'。</li><br><li>.object：参数类型为{@link ArkUI_RenderNodeClipOption}，路径绘制的命令，在仅传入.object参数时生效。</li><br></ul><br>**返回：**<br>1.rect类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_RECTANGLE。</li><br><li>.value[1].f32：矩形宽度，单位为vp。</li><br><li>.value[2].f32：矩形高度，单位为vp。</li><br><li>.value[3].f32：矩形圆角宽度，单位为vp。</li><br><li>.value[4].f32：矩形圆角高度，单位为vp。</li><br><li>.value[5]?.f32：矩形形状的左上圆角半径，单位为vp。</li><br><li>.value[6]?.f32：矩形形状的左下圆角半径，单位为vp。</li><br><li>.value[7]?.f32：矩形形状的右上圆角半径，单位为vp。</li><br><li>.value[8]?.f32：矩形形状的右下圆角半径，单位为vp。</li><br><li>.value[9]?.f32：矩形形状的横坐标偏移，单位为vp。</li><br><li>.value[10]?.f32：矩形形状的纵坐标偏移，单位为vp。</li><br></ul><br>2.circle类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_CIRCLE。</li><br><li>.value[1].f32：圆形宽度，单位为vp。</li><br><li>.value[2].f32：圆形高度，单位为vp。</li><br><li>.value[3]?.f32：圆形横坐标偏移，单位为vp。</li><br><li>.value[4]?.f32：圆形纵坐标偏移，单位为vp。</li><br></ul><br>3.ellipse类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_ELLIPSE。</li><br><li>.value[1].f32：椭圆形宽度，单位为vp。</li><br><li>.value[2].f32：椭圆形高度，单位为vp。</li><br><li>.value[3]?.f32：椭圆形横坐标偏移，单位为vp。</li><br><li>.value[4]?.f32：椭圆形纵坐标偏移，单位为vp。</li><br></ul><br>4.path类型：<br><ul><br><li>.value[0].i32：裁剪类型，参数类型{@link ArkUI_ClipType}，ARKUI_CLIP_TYPE_PATH。</li> <li>.value[1].f32：路径宽度，单位为vp。</li><br><li>.value[2].f32：路径高度，单位为vp。</li> <li>.string：路径绘制的命令字符串。</li> </ul>

**起始版本：** 12

### NODE_TRANSFORM

```c
NODE_TRANSFORM
```

**描述：**

矩阵变换功能，可对图形进行平移、旋转和缩放等，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0...15].f32：4x4变换矩阵的16个浮点数，用于对图形进行平移、旋转和缩放等矩阵变换，按行优先顺序排列。此时{@link ArkUI_AttributeItem}中的size取值不应为0。</li> </ul> **返回：**<br><ul> <li>.value[0...15].f32：4x4矩阵变换的16个浮点数元素值。</li> </ul>

**起始版本：** 12

### NODE_SHADOW

```c
NODE_SHADOW
```

**描述：**

阴影效果属性，支持属性设置，属性重置和属性获取接口。 与NODE_CUSTOM_SHADOW互斥，同一组件只能使用一种阴影属性设置方式，同时设置时后者将覆盖前者。 如需使用预定义阴影样式请使用NODE_SHADOW，如需自定义阴影参数请使用NODE_CUSTOM_SHADOW。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：设置当前组件阴影效果，参数类型{@link ArkUI_ShadowStyle}。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：设置当前组件阴影效果，参数类型{@link ArkUI_ShadowStyle}。</li> </ul>

**起始版本：** 12

### NODE_CUSTOM_SHADOW

```c
NODE_CUSTOM_SHADOW
```

**描述：**

自定义阴影效果，与NODE_SHADOW互斥，同一组件只能使用一种阴影属性设置方式，同时设置时后者将覆盖前者。 如需使用预定义阴影样式请使用NODE_SHADOW，如需自定义阴影参数请使用NODE_CUSTOM_SHADOW。支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0]?.f32：阴影模糊半径，取值范围[0, +∞)，传入负值时返回参数校验失败。单位为px，默认值0.0。</li><br><li>.value[1]?.i32：是否开启智能取色，0代表不开启（使用固定颜色），1代表开启（自动从组件周围取色适配背景），默认不开启。</li><br><li>.value[2]?.f32：阴影X轴偏移量，单位为px，默认值0.0。</li><br><li>.value[3]?.f32：阴影Y轴偏移量，单位为px，默认值0.0。</li><br><li>.value[4]?.i32：阴影类型，参数类型为{@link ArkUI_ShadowType}，默认值为ARKUI_SHADOW_TYPE_COLOR。</li><br><li>.value[5]?.u32：智能取色关闭（.value[1]为0）时表示阴影颜色，0xargb格式，形如0xFFFF0000表示红色，不传入时默认值为0xFF000000（黑色）；智能取色开启（.value[1]为1）时表示颜色策略，取{@link ArkUI_ColorStrategy}枚举值。</li><br><li>.value[6]?.u32：阴影是否内部填充，0表示不填充，1表示填充。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：阴影模糊半径，单位为px。</li><br><li>.value[1].i32：是否开启智能取色，0代表不开启，1代表开启。</li><br><li>.value[2].f32：阴影X轴偏移量，单位为px。</li><br><li>.value[3].f32：阴影Y轴偏移量，单位为px。</li><br><li>.value[4].i32：阴影类型，参数类型为{@link ArkUI_ShadowType}，默认值为ARKUI_SHADOW_TYPE_COLOR。枚举值包括：ARKUI_SHADOW_TYPE_COLOR（颜色阴影）、ARKUI_SHADOW_TYPE_BLUR（模糊阴影）。</li> <li>.value[5].u32：阴影颜色，0xAARRGGBB格式，形如0xFFFF0000表示红色。</li><br><li>.value[6].u32：阴影是否内部填充，0表示不填充，1表示填充。</li> </ul>

**起始版本：** 12

### NODE_TRANSFORM_CENTER

```c
NODE_TRANSFORM_CENTER
```

**描述：**

图形变换和转场的中心点属性，影响旋转（NODE_ROTATE/NODE_ROTATE_ANGLE/NODE_ROTATE_TRANSITION）、缩放（NODE_SCALE/NODE_SCALE_TRANSITION）、 平移（NODE_TRANSLATE/NODE_TRANSLATE_TRANSITION）等变换和转场属性的中心点行为，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0]?.f32：表示中心点X轴坐标值，单位为vp，默认值0.0。</li><br><li>.value[1]?.f32：表示中心点Y轴坐标，单位为vp，默认值0.0。</li><br><li>.value[2]?.f32：表示中心点Z轴坐标，单位为vp，默认值0.0。</li><br><li>.value[3]?.f32：表示中心点X轴坐标的百分比位置，取值范围[0, 1]，如0.2表示百分之20的位置，该属性覆盖value[0].f32，默认值：0.5f。超出范围时返回错误码{@link ARKUI_ERROR_CODE_PARAM_INVALID}。</li><br><li>.value[4]?.f32：表示中心点Y轴坐标的百分比位置，取值范围[0, 1]，如0.2表示百分之20的位置，该属性覆盖value[1].f32，默认值：0.5f。超出范围时返回错误码{@link ARKUI_ERROR_CODE_PARAM_INVALID}。</li><br><li>.value[5]?.f32：表示中心点Z轴坐标的百分比位置，取值范围[0, 1]，如0.2表示百分之20的位置，该属性覆盖value[2].f32，默认值：0.0f。超出范围时返回错误码{@link ARKUI_ERROR_CODE_PARAM_INVALID}。</li> </ul> **返回：**<br><ul> <li>.value[0].f32：表示中心点X轴坐标，单位为vp。</li><br><li>.value[1].f32：表示中心点Y轴坐标，单位为vp。</li><br><li>.value[2].f32：表示中心点Z轴坐标，单位为vp。注：如果设置坐标百分比位置，属性获取方法返回计算后的以vp为单位的值。</li> </ul>

**起始版本：** 12

### NODE_SWEEP_GRADIENT

```c
NODE_SWEEP_GRADIENT
```

**描述：**

角度渐变效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0]?.f32：为角度渐变的中心点，即相对于当前组件左上角的X轴坐标，单位为vp，默认值为组件宽度的50%。</li><br><li>.value[1]?.f32：为角度渐变的中心点，即相对于当前组件左上角的Y轴坐标，单位为vp。不传入时默认为组件垂直中心位置，当需要将渐变中心偏移到特定位置时传入此参数。</li><br><li>.value[2]?.f32：角度渐变的起点，单位为度（°），默认值0。</li><br><li>.value[3]?.f32：角度渐变的终点，单位为度（°），默认值0。</li><br><li>.value[4]?.f32：角度渐变的旋转角度，单位为度（°），默认值0。</li><br><li>.value[5]?.i32：是否对渐变颜色重复着色，0表示不重复着色，1表示重复着色。不传入时默认值为0（不重复着色），当需要颜色循环重复填充时传入1。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li><br><li>colors：渐变色颜色。</li><br><li>stops：渐变位置。</li><br><li>size：颜色个数。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：为角度渐变的中心点，即相对于当前组件左上角的坐标，X轴坐标。</li><br><li>.value[1].f32：为角度渐变的中心点，即相对于当前组件左上角的坐标，Y轴坐标。</li><br><li>.value[2].f32：角度渐变的起点，单位为度（°），默认值0。</li><br><li>.value[3].f32：角度渐变的终点，单位为度（°），默认值0。</li><br><li>.value[4].f32：角度渐变的旋转角度，单位为度（°），默认值0。</li><br><li>.value[5].i32：是否对渐变颜色重复着色，0表示不重复着色，1表示重复着色。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置不符合颜色格式要求的颜色值会被跳过。</li> <li>colors：渐变色颜色。</li> <li>stops：渐变位置。</li> <li>size：颜色个数。</li> </ul>

**起始版本：** 12

### NODE_RADIAL_GRADIENT

```c
NODE_RADIAL_GRADIENT
```

**描述：**

径向渐变效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0]?.f32：为径向渐变的中心点，即相对于当前组件左上角的X轴坐标。</li><br><li>.value[1]?.f32：为径向渐变的中心点，即相对于当前组件左上角的Y轴坐标。</li><br><li>.value[2]?.f32：径向渐变的半径，取值范围[0, +∞)，默认值0。</li><br><li>.value[3]?.i32：为渐变的颜色重复着色，0表示不重复着色，1表示重复着色。不传入时默认值为0（不重复着色）。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li><br><li>colors：渐变色颜色。</li><br><li>stops：渐变位置。</li><br><li>size：颜色个数。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：为径向渐变的中心点，即相对于当前组件左上角的坐标，X轴坐标。</li><br><li>.value[1].f32：为径向渐变的中心点，即相对于当前组件左上角的坐标，Y轴坐标。</li><br><li>.value[2].f32：径向渐变的半径，默认值0。</li><br><li>.value[3].i32：为渐变的颜色重复着色，false（0）表示不重复着色，true（1）表示重复着色。</li><br><li>.object：参数类型为{@link ArkUI_ColorStop}。指定某百分比位置处的渐变色颜色，设置非法颜色直接跳过。</li> <li>colors：渐变色颜色。</li> <li>stops：渐变位置。</li> <li>size：颜色个数。</li> </ul>

**起始版本：** 12

### NODE_MASK

```c
NODE_MASK
```

**描述：**

组件上加上指定形状的遮罩，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br>1.rect类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型，参数类型{@link ArkUI_MaskType}，ARKUI_MASK_TYPE_RECTANGLE。</li><br><li>.value[4].f32：矩形宽度，单位为vp。</li><br><li>.value[5].f32：矩形高度，单位为vp。</li><br><li>.value[6].f32：矩形圆角宽度，单位为vp。</li><br><li>.value[7].f32：矩形圆角高度，单位为vp。</li><br><li>.value[8]?.f32：矩形形状的左上圆角半径，单位为vp，默认值0。</li><br><li>.value[9]?.f32：矩形形状的左下圆角半径，单位为vp，默认值0。</li><br><li>.value[10]?.f32：矩形形状的右上圆角半径，单位为vp，默认值0。</li><br><li>.value[11]?.f32：矩形形状的右下圆角半径，单位为vp，默认值0。</li><br></ul><br>2.circle类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型，参数类型{@link ArkUI_MaskType}，ARKUI_MASK_TYPE_CIRCLE。</li><br><li>.value[4].f32：圆形宽度，单位为vp。</li><br><li>.value[5].f32：圆形高度，单位为vp。</li><br></ul><br>3.ellipse类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型，参数类型{@link ArkUI_MaskType}，ARKUI_MASK_TYPE_ELLIPSE。</li><br><li>.value[4].f32：椭圆形宽度，单位为vp。</li><br><li>.value[5].f32：椭圆形高度，单位为vp。</li><br></ul><br>4.path类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型，参数类型{@link ArkUI_MaskType}，ARKUI_MASK_TYPE_PATH。</li><br><li>.value[4].f32：路径宽度，单位为vp。</li><br><li>.value[5].f32：路径高度，单位为vp。</li><br><li>.string：路径绘制的命令字符串，格式遵循SVG path数据语法，如'M0 0 L100 100 Z'。</li><br></ul><br>5.progress类型：<br><ul><br><li>.value[0].i32：遮罩类型，参数类型{@link ArkUI_MaskType}，ARKUI_MASK_TYPE_PROGRESS。</li> <li>.value[1].f32：进度遮罩的当前值。</li><br><li>.value[2].f32：进度遮罩的最大值。</li><br><li>.value[3].u32：进度遮罩的颜色。</li><br></ul><br>**返回：**<br>1.rect类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型。</li><br><li>.value[4].f32：矩形宽度，单位为vp。</li><br><li>.value[5].f32：矩形高度，单位为vp。</li><br><li>.value[6].f32：矩形圆角宽度，单位为vp。</li><br><li>.value[7].f32：矩形圆角高度，单位为vp。</li><br><li>.value[8]?.f32：矩形形状的左上圆角半径，单位为vp。</li><br><li>.value[9]?.f32：矩形形状的左下圆角半径，单位为vp。</li><br><li>.value[10]?.f32：矩形形状的右上圆角半径，单位为vp。</li><br><li>.value[11]?.f32：矩形形状的右下圆角半径，单位为vp。</li><br></ul><br>2.circle类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型。</li><br><li>.value[4].f32：圆形宽度，单位为vp。</li><br><li>.value[5].f32：圆形高度，单位为vp。</li><br></ul><br>3.ellipse类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型。</li><br><li>.value[4].f32：椭圆形宽度，单位为vp。</li><br><li>.value[5].f32：椭圆形高度，单位为vp。</li><br></ul><br>4.path类型：<br><ul><br><li>.value[0].u32：填充颜色，0xargb类型。</li><br><li>.value[1].u32：描边颜色，0xargb类型。</li><br><li>.value[2].f32：描边宽度，单位为vp。</li><br><li>.value[3].i32：遮罩类型。</li><br><li>.value[4].f32：路径宽度，单位为vp。</li><br><li>.value[5].f32：路径高度，单位为vp。</li><br><li>.string：路径绘制的命令字符串。</li><br></ul><br>5.progress类型：<br><ul><br><li>.value[0].i32：遮罩类型。</li><br><li>.value[1].f32：进度遮罩的当前值。</li><br><li>.value[2].f32：进度遮罩的最大值。</li><br><li>.value[3].u32：进度遮罩的颜色。</li> </ul>

**起始版本：** 12

### NODE_BLEND_MODE

```c
NODE_BLEND_MODE
```

**描述：**

当前控件背景与子节点内容进行混合，用于实现叠加透明效果、颜色混合等视觉合成场景，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：控制当前组件的混合模式类型，参数类型为{@link ArkUI_BlendMode}，默认值为ARKUI_BLEND_MODE_NONE。</li><br><li>.value[1]?.i32：blendMode实现方式是否离屏，参数类型{@link ArkUI_BlendApplyType}，默认值为BLEND_APPLY_TYPE_FAST。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：控制当前组件的混合模式类型，参数类型{@link ArkUI_BlendMode}，默认值为ARKUI_BLEND_MODE_NONE。</li><br><li>.value[1].i32：blendMode实现方式是否离屏，参数类型为{@link ArkUI_BlendApplyType}，默认值为BLEND_APPLY_TYPE_FAST。枚举值包括：BLEND_APPLY_TYPE_FAST（快速实现，非离屏）、BLEND_APPLY_TYPE_OFFSCREEN（离屏实现）。</li> </ul>

**起始版本：** 12

### NODE_GRAY_SCALE

```c
NODE_GRAY_SCALE
```

**描述：**

灰度效果属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：灰度转换比例，范围0-1之间，默认值为0，比如0.5指按照50%进行灰度处理。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：灰度转换比例，范围0-1之间。</li> </ul>

**起始版本：** 12

### NODE_INVERT

```c
NODE_INVERT
```

**描述：**

反转输入的图像比例属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：图像反转比例，范围0-1之间，默认值为0，比如0.5指按照50%进行反转处理。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：图像反转比例，范围0-1之间。</li> </ul>

**起始版本：** 12

### NODE_SEPIA

```c
NODE_SEPIA
```

**描述：**

图像转换为深褐色比例属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：图像转换为深褐色比例，范围0-1之间，默认值为0，比如0.5指按照50%进行深褐色处理。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：图像转换为深褐色比例，范围0-1之间。</li> </ul>

**起始版本：** 12

### NODE_CONTRAST

```c
NODE_CONTRAST
```

**描述：**

对比度属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：对比度，等于1时为原图，越大则对比度越高，默认值为1，取值范围：[0, 10)，超出范围时返回错误码{@link ARKUI_ERROR_CODE_PARAM_INVALID}。</li> </ul> **返回：**<br><ul> <li>.value[0].f32：对比度，取值范围：[0, 10)。</li> </ul>

**起始版本：** 12

### NODE_FOREGROUND_COLOR

```c
NODE_FOREGROUND_COLOR
```

**描述：**

前景颜色属性，支持属性设置和属性获取接口。属性重置接口无效果，因前景颜色为不可自动恢复默认值的属性类型，重置操作不会改变已设置的前景颜色。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].u32：颜色数值，0xAARRGGBB类型，如0xFFFF0000表示红色，默认值为0xFF000000。用于直接指定颜色值。</li><br><li>.value[0].i32：颜色数值枚举{@link ArkUI_ColorStrategy}。</li> </ul> **返回：**<br><ul> <li>.value[0].u32：颜色数值，0xargb类型。</li> </ul>

**起始版本：** 12

### NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH
```

**描述：**

设置元素的外描边宽度，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：左侧外描边宽度，单位为vp。</li><br><li>.value[1].f32：上侧外描边宽度，单位为vp。</li><br><li>.value[2].f32：右侧外描边宽度，单位为vp。</li><br><li>.value[3].f32：下侧外描边宽度，单位为vp。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：左侧外描边宽度，单位为vp。</li><br><li>.value[1].f32：上侧外描边宽度，单位为vp。</li><br><li>.value[2].f32：右侧外描边宽度，单位为vp。</li><br><li>.value[3].f32：下侧外描边宽度，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_RENDER_FIT

```c
NODE_RENDER_FIT
```

**描述：**

设置宽高动画过程中的组件内容填充方式，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：内容填充方式，使用{@link ArkUI_RenderFit}枚举值。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：内容填充方式，使用{@link ArkUI_RenderFit}枚举值。</li> </ul>

**起始版本：** 12

### NODE_OUTLINE_COLOR

```c
NODE_OUTLINE_COLOR
```

**描述：**

外描边颜色属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br>1. 仅传入.value[0]时，统一设置四条边的边框颜色：<br><ul><br><li>.value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br></ul><br>2. 传入.value[0]至.value[3]四个值时，分别设置四条边的边框颜色：<br><ul><br><li>.value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].u32：设置上侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[1].u32：设置右侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[2].u32：设置下侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li><br><li>.value[3].u32：设置左侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li> </ul>

**起始版本：** 12

### NODE_RENDER_GROUP

```c
NODE_RENDER_GROUP
```

**描述：**

设置当前组件和子组件是否先整体离屏渲染绘制后再与父组件融合绘制，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32：参数值为1表示当前组件与子组件需要先整体离屏渲染绘制后再与父控件融合绘制，参数值为0表示不需要整体离屏渲染绘制后再与父控件融合绘制。默认值为0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：参数值为1表示当前组件与子组件完成整体离屏渲染绘制，参数值为0表示当前组件与子组件未完成整体离屏渲染绘制。</li> </ul>

**起始版本：** 12

### NODE_COLOR_BLEND

```c
NODE_COLOR_BLEND
```

**描述：**

为组件添加颜色叠加效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].u32：叠加的颜色，使用0xargb表示，默认值为0x00000000。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].u32：叠加的颜色，使用0xargb表示，如0xFFFF11FF。</li> </ul>

**起始版本：** 12

### NODE_FOREGROUND_BLUR_STYLE

```c
NODE_FOREGROUND_BLUR_STYLE
```

**描述：**

为当前组件提供内容模糊能力，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：表示内容模糊样式，取{@link ArkUI_BlurStyle}枚举值。</li><br><li>.value[1]?.i32：表示内容模糊效果使用的深浅色模式，取{@link ArkUI_ColorMode}枚举值。不传入时默认值为ARKUI_COLOR_MODE_SYSTEM。</li><br><li>.value[2]?.i32：表示内容模糊效果使用的取色模式，取{@link ArkUI_AdaptiveColor}枚举值。</li><br><li>.value[3]?.f32：表示模糊效果程度，取[0.0,1.0]范围内的值。</li><br><li>.value[4]?.f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。不传入时默认值为0。</li><br><li>.value[5]?.f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。不传入时默认值为0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：表示内容模糊样式，取{@link ArkUI_BlurStyle}枚举值。</li><br><li>.value[1].i32：表示内容模糊效果使用的深浅色模式，取{@link ArkUI_ColorMode}枚举值。</li><br><li>.value[2].i32：表示内容模糊效果使用的取色模式，取{@link ArkUI_AdaptiveColor}枚举值。</li> <li>.value[3].f32：表示模糊效果程度，取[0.0,1.0]范围内的值。</li><br><li>.value[4].f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。</li><br><li>.value[5].f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。</li> </ul>

**起始版本：** 12

### NODE_BACKDROP_BLUR

```c
NODE_BACKDROP_BLUR = 99
```

**描述：**

设置背景模糊效果，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：表示背景模糊半径，取值范围[0,+∞)，超出范围时返回错误码{@link ARKUI_ERROR_CODE_PARAM_INVALID}。单位px，默认值0.0。</li> <li>.value[1]?.f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。不传入时默认值为0。</li><br><li>.value[2]?.f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。不传入时默认值为0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：表示背景模糊半径，取值范围[0,+∞)，单位为px。</li><br><li>.value[1].f32：表示灰阶模糊参数，对黑色的提亮程度，取值范围为[0,127]。</li><br><li>.value[2].f32：表示灰阶模糊参数，对白色的压暗程度，取值范围为[0,127]。</li> </ul>

**起始版本：** 15

### NODE_TRANSLATE_WITH_PERCENT

```c
NODE_TRANSLATE_WITH_PERCENT = 103
```

**描述：**

设置组件平移，支持百分比形式的平移入参，与NODE_TRANSLATE互斥，同一组件只能使用一种平移属性设置方式，同时设置时后者将覆盖前者。支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：x轴移动距离，默认单位为百分比，除非value[3]存在且value[3]为0时单位为vp，默认值0。</li><br><li>.value[1].f32：y轴移动距离，默认单位为百分比，除非value[4]存在且value[4]为0时单位为vp，默认值0。</li><br><li>.value[2].f32：z轴移动距离，单位vp，默认值0。</li><br><li>.value[3]?.i32：x轴移动距离是否为百分比形式指定，取值范围：0或1。为1时表示以百分比形式指定，例如value[0].f32=0.1且value[3].i32=1时表示x方向平移10%。默认值1。</li><br><li>.value[4]?.i32：y轴移动距离是否为百分比形式指定，取值范围：0或1。为1时表示以百分比形式指定，例如value[1].f32=0.1且value[4].i32=1时表示y方向平移10%，默认值1。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：x轴移动距离，单位取决于value[3]。</li><br><li>.value[1].f32：y轴移动距离，单位取决于value[4]。</li><br><li>.value[2].f32：z轴移动距离，单位vp。</li><br><li>.value[3].i32：x轴移动距离的单位是否为百分比。</li><br><li>.value[4].i32：y轴移动距离的单位是否为百分比。</li> </ul>

**起始版本：** 20

### NODE_ROTATE_ANGLE

```c
NODE_ROTATE_ANGLE = 104
```

**描述：**

设置组件旋转，支持各轴旋转角属性设置，属性重置和属性获取接口。与NODE_ROTATE互斥，同一组件只能使用一种旋转属性设置方式，同时设置时后者将覆盖前者。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32：x轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[1].f32：y轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[2].f32：z轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[3].f32：视距，即视点到z=0平面的距离，单位px，默认值0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：x轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[1].f32：y轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[2].f32：z轴方向旋转角度，单位为度（°），默认值0。</li><br><li>.value[3].f32：视距，即视点到z=0平面的距离，单位px，默认值0。</li> </ul>

**起始版本：** 20

### NODE_SYSTEM_MATERIAL

```c
NODE_SYSTEM_MATERIAL = 127
```

**描述：**

定义系统材质属性，支持属性设置，属性重置和属性获取接口。 仅支持系统材质的设备可使用此属性。否则，当设置此属性时，将返回错误码{@link ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED}。<br>设备是否支持系统材质可通过调用{@link OH_ArkUI_NativeModule_GetSystemMaterialSupported}获取。<br>材质效果在不同算力的设备上表现不同。算力等级由{@link ArkUI_MaterialLevel}定义，可通过{@link OH_ArkUI_NativeModule_GetGlobalMaterialLevel}获取。<br>在算力等级为ARKUI_MATERIAL_LEVEL_SMOOTH的设备上，设置NODE_SYSTEM_MATERIAL会覆盖NODE_SHADOW/NODE_CUSTOM_SHADOW的阴影效果、NODE_OUTLINE_COLOR的外描边颜色、NODE_OUTLINE_WIDTH的外描边宽度，并改变组件背景颜色。<br>在算力等级为ARKUI_MATERIAL_LEVEL_EXQUISITE或ARKUI_MATERIAL_LEVEL_GENTLE的设备上，设置NODE_SYSTEM_MATERIAL会覆盖阴影属性并在系统材质层添加滤镜效果，可产生类似玻璃的效果。<br><br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.object：系统材质对象。参数类型为{@link ArkUI_ImmersiveMaterialHandle}。</li><br></ul><br>**返回：**<br><ul><br><li>.object：系统材质对象。参数类型为{@link ArkUI_ImmersiveMaterialHandle}。返回值中的ArkUI_ImmersiveMaterialHandle对象是指向静态成员的指针，因此无需也禁止通过{@link OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy}释放返回对象。</li> </ul>

**起始版本：** 26.0.0


