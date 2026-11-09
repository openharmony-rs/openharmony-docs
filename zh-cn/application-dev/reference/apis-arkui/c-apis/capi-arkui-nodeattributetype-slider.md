# 滑动条

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_SLIDER_BLOCK_COLOR

```c
NODE_SLIDER_BLOCK_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER
```

**描述：**

Slider滑块的颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 滑块的颜色，类型为0xARGB，如0xFF1122FF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 滑块的颜色，类型为0xARGB，如0xFF1122FF。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_TRACK_COLOR

```c
NODE_SLIDER_TRACK_COLOR
```

**描述：**

Slider滑轨的背景颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景颜色，类型为0xARGB，如0xFF1122FF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景颜色，类型为0xARGB，如0xFF1122FF。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_SELECTED_COLOR

```c
NODE_SLIDER_SELECTED_COLOR
```

**描述：**

Slider滑轨的已滑动部分颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 已滑动部分颜色，类型为0xARGB，如0xFF1122FF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 已滑动部分颜色，类型为0xARGB，如0xFF1122FF。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_SHOW_STEPS

```c
NODE_SLIDER_SHOW_STEPS
```

**描述：**

设置是否显示步长刻度值，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 是否显示步长刻度值，1表示显示，0表示不显示，默认值为0。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_BLOCK_STYLE

```c
NODE_SLIDER_BLOCK_STYLE
```

**描述：**

Slider滑块形状参数，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: depending on the shape. Optional.</li> </ul> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. There are five types:<br>
1. Rectangle: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape. .value[2].f32: width of the rectangle. .value[3].f32: height of the rectangle. .value[4].f32: width of the rounded corner of the rectangle. .value[5].f32: height of the rounded corner of the rectangle.<br>
2. Circle: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape. .value[2].f32: width of the circle. .value[3].f32: height of the circle. 3.Ellipse: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape. .value[2].f32: width of the ellipse. .value[3].f32: height of the ellipse;<br>
4. Path: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape. .value[2].f32: width of the path. .value[3].f32: height of the path. .string: command for drawing the path. **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:** <ul> <li>.value[0].i32: shape. The parameter type is [ArkUI_SliderBlockStyle](capi-slider-h.md#arkui_sliderblockstyle).</li> <li>.string?: depending on the shape. Optional.</li> </ul> ARKUI_SLIDER_BLOCK_STYLE_IMAGE: image resource of the slider. Example: /pages/common/icon.png. ARKUI_SLIDER_BLOCK_STYLE_SHAPE: custom shape of the slider. There are five types:<br>
1. Rectangle: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_RECTANGLE</b> for the rectangle shape. .value[2].f32: width of the rectangle. .value[3].f32: height of the rectangle. .value[4].f32: width of the rounded corner of the rectangle. .value[5].f32: height of the rounded corner of the rectangle.<br>
2. Circle: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_CIRCLE</b> for the circle shape. .value[2].f32: width of the circle. .value[3].f32: height of the circle. 3.Ellipse: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_ELLIPSE</b> for the ellipse shape. .value[2].f32: width of the ellipse. .value[3].f32: height of the ellipse;<br>
4. Path: .value[1].i32: type of shape. The parameter type is [ArkUI_ShapeType](capi-native-type-visual-h.md#arkui_shapetype). The value is <b>ARKUI_SHAPE_TYPE_PATH</b> for the path shape. .value[2].f32: width of the path. .value[3].f32: height of the path. .string: command for drawing the path.

**起始版本：** 12

### NODE_SLIDER_VALUE

```c
NODE_SLIDER_VALUE
```

**描述：**

Slider进度值，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_MIN_VALUE

```c
NODE_SLIDER_MIN_VALUE
```

**描述：**

Slider最小值，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值的最小值。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值的最小值。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_MAX_VALUE

```c
NODE_SLIDER_MAX_VALUE
```

**描述：**

Slider最大值，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值的最大值。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 进度值的最大值。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_STEP

```c
NODE_SLIDER_STEP
```

**描述：**

Slider滑动步长，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 滑动步长，取值范围：[0.01, 100]。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 滑动步长，取值范围：[0.01, 100]。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_DIRECTION

```c
NODE_SLIDER_DIRECTION
```

**描述：**

Slider滑动条滑动方向，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 滑动方向，参数类型[ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 滑动方向，参数类型[ArkUI_SliderDirection](capi-slider-h.md#arkui_sliderdirection)。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_REVERSE

```c
NODE_SLIDER_REVERSE
```

**描述：**

Slider滑动条取值范围是否反向，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 是否反向，1表示反向，0表示不反向。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 是否反向，1表示反向，0表示不反向。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_STYLE

```c
NODE_SLIDER_STYLE
```

**描述：**

Slider的滑块与滑轨显示样式，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 显示样式，参数类型[ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 显示样式，参数类型[ArkUI_SliderStyle](capi-slider-h.md#arkui_sliderstyle)。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_TRACK_THICKNESS

```c
NODE_SLIDER_TRACK_THICKNESS
```

**描述：**

Slider滑块的滑轨粗细属性，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 滑轨的粗细，单位为vp；当参数NODE_SLIDER_STYLE的值设置为ARKUI_SLIDER_STYLE_OUT_SET时为4.0vp，设置为ARKUI_SLIDER_STYLE_IN_SET时为20.0vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 滑轨的粗细，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_SLIDER_ENABLE_HAPTIC_FEEDBACK = 17013
```

**描述：**

设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 是否开启触控反馈。默认值：true，true表示开启触控反馈，false则表示不开启触控反馈。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>value[0].i32: 是否开启触控反馈。</li> </ul>

**起始版本：** 18

### NODE_SLIDER_PREFIX

```c
NODE_SLIDER_PREFIX
```

**描述：**

在Slider组件的前端设置自定义组件。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型 [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。前缀组件将放置在Slider组件的起始位置，通常在LTR布局的左侧。</li> </ul> The prefix component will be placed at the start position of the Slider， typically on the left side in LTR layouts. *

**起始版本：** 20

### NODE_SLIDER_SUFFIX

```c
NODE_SLIDER_SUFFIX
```

**描述：**

在Slider组件的后端设置自定义组件。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型 [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。后缀组件将放置在Slider组件的尾侧位置，通常在LTR布局的右侧。</li> </ul> The suffix component will be placed at the end position of the Slider, typically on the right side in LTR layouts. *

**起始版本：** 20

### NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_BLOCK_LINEAR_GRADIENT_COLOR
```

**描述：**

Slider滑块的线性渐变颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色，设置非法颜色直接跳过：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul>

**起始版本：** 21

### NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_TRACK_LINEAR_GRADIENT_COLOR
```

**描述：**

Slider滑轨的背景线性渐变颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色，设置非法颜色直接跳过：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul>

**起始版本：** 21

### NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR

```c
NODE_SLIDER_SELECTED_LINEAR_GRADIENT_COLOR
```

**描述：**

Slider滑轨的已滑动部分线性渐变颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色，设置非法颜色直接跳过：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.object: 参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。指定相对比例位置处的渐变色颜色：<br>- colors：渐变色颜色。<br>- stops：渐变位置。<br>- size：颜色个数。</li> <li>colors: 渐变色颜色。</li> <li>stops: 渐变位置。</li> <li>size: 颜色个数。</li> </ul>

**起始版本：** 21


