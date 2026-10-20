# 布局

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_WIDTH

```c
NODE_WIDTH = 0
```

**描述：**

宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为vp。取值范围：[0, +∞)。设置异常值时，按默认值显示或组件尺寸异常。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_HEIGHT

```c
NODE_HEIGHT
```

**描述：**

高度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置高度数值，单位为vp。取值范围：[0, +∞)。设置异常值时，按默认值显示或组件尺寸异常。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：高度数值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_PADDING

```c
NODE_PADDING
```

**描述：**

内间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的内间距值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的内间距值，单位为vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的内间距值。 <ul> <li>.value[0].f32：设置上内间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[1].f32：设置右内间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[2].f32：设置下内间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[3].f32：设置左内间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上内间距数值，单位为vp。</li> <li>.value[1].f32：右内间距数值，单位为vp。</li> <li>.value[2].f32：下内间距数值，单位为vp。</li> <li>.value[3].f32：左内间距数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_MARGIN

```c
NODE_MARGIN
```

**描述：**

外间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的外间距值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的外间距值，单位为vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的外间距值。 <ul> <li>.value[0].f32：设置上外间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[1].f32：设置右外间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[2].f32：设置下外间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> <li>.value[3].f32：设置左外间距数值，单位为vp，默认值为0vp。取值范围：[0, +∞)。设置异常值时，按默认值0vp显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上外间距数值，单位为vp。</li> <li>.value[1].f32：右外间距数值，单位为vp。</li> <li>.value[2].f32：下外间距数值，单位为vp。</li> <li>.value[3].f32：左外间距数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_ALIGNMENT

```c
NODE_ALIGNMENT
```

**描述：**

设置组件内容在元素绘制区域内的对齐方式，支持属性设置，属性重置和属性获取接口。<br> 在Stack中该属性与NODE_STACK_ALIGN_CONTENT效果一致，只能设置子组件在容器内的对齐方式。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置对齐方式，参数类型[ArkUI_Alignment](capi-layout-h.md#arkui_alignment)，默认值为ARKUI_ALIGNMENT_CENTER。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：对齐方式，类型为[ArkUI_Alignment](capi-layout-h.md#arkui_alignment)。</li> </ul>

**起始版本：** 12

### NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH
```

**描述：**

边框宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置四条边的边框宽度。 <ul> <li>.value[0].f32：统一设置四条边的边框宽度，单位为vp。取值范围：[0, +∞)。默认值为0vp。</li> </ul> 2. 传入四个参数，表示分别设置四条边的边框宽度。 <ul> <li>.value[0].f32：设置上边框的边框宽度，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[1].f32：设置右边框的边框宽度，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[2].f32：设置下边框的边框宽度，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[3].f32：设置左边框的边框宽度，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框的边框宽度，单位为vp。</li> <li>.value[1].f32：右边框的边框宽度，单位为vp。</li> <li>.value[2].f32：下边框的边框宽度，单位为vp。</li> <li>.value[3].f32：左边框的边框宽度，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS
```

**描述：**

边框圆角属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1：只传入一个参数，表示统一设置四个角的边框圆角半径。 <ul> <li>.value[0].f32：统一设置四个角的边框圆角半径，单位为vp。取值范围：[0, +∞)。默认值为0vp。</li> </ul> 2：传入四个参数，表示分别设置四个角的边框圆角半径。 <ul> <li>.value[0].f32：设置左上角圆角半径，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[1].f32：设置右上角圆角半径，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[2].f32：设置左下角圆角半径，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> <li>.value[3].f32：设置右下角圆角半径，单位为vp，默认值为0vp。取值范围：[0, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：左上角圆角半径，单位为vp。</li> <li>.value[1].f32：右上角圆角半径，单位为vp。</li> <li>.value[2].f32：左下角圆角半径，单位为vp。</li> <li>.value[3].f32：右下角圆角半径，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR
```

**描述：**

边框颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1：统一设置四条边的边框颜色。 <ul> <li>.value[0].u32：统一设置四条边的边框颜色，使用0xARGB表示，如`0xFFFF11FF`。</li> </ul> 2：分别设置四条边的边框颜色。 <ul> <li>.value[0].u32：设置上侧边框颜色，使用0xARGB表示，默认值为`0xFF000000`。</li> <li>.value[1].u32：设置右侧边框颜色，使用0xARGB表示，默认值为`0xFF000000`。</li> <li>.value[2].u32：设置下侧边框颜色，使用0xARGB表示，默认值为`0xFF000000`。</li> <li>.value[3].u32：设置左侧边框颜色，使用0xARGB表示，默认值为`0xFF000000`。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：上侧边框颜色，使用0xARGB表示，如`0xFFFF11FF`。</li> <li>.value[1].u32：右侧边框颜色，使用0xARGB表示，如`0xFFFF11FF`。</li> <li>.value[2].u32：下侧边框颜色，使用0xARGB表示，如`0xFFFF11FF`。</li> <li>.value[3].u32：左侧边框颜色，使用0xARGB表示，如`0xFFFF11FF`。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE
```

**描述：**

边框线条样式属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置四条边的边框线条样式。 <ul> <li>.value[0].i32：统一设置四条边的边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> </ul> 2. 传入四个参数，表示分别设置四条边的边框线条样式。 <ul> <li>.value[0].i32：设置上侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[1].i32：设置右侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[2].i32：设置下侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[3].i32：设置左侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：上侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)。</li> <li>.value[1].i32：右侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)。</li> <li>.value[2].i32：下侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)。</li> <li>.value[3].i32：左侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_POSITION

```c
NODE_POSITION
```

**描述：**

元素左上角相对于父容器左上角偏移位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置x轴坐标，单位为vp。取值范围：(-∞, +∞)。</li> <li>.value[1].f32：设置y轴坐标，单位为vp。取值范围：(-∞, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：x轴坐标，单位为vp。</li> <li>.value[1].f32：y轴坐标，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为2。

**起始版本：** 12

### NODE_DIRECTION

```c
NODE_DIRECTION
```

**描述：**

设置容器元素内主轴方向上的布局，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：主轴方向，设置容器内子组件的排列方向。参数类型[ArkUI_Direction](capi-layout-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：主轴方向，类型为[ArkUI_Direction](capi-layout-h.md#arkui_direction)。</li> </ul>

**起始版本：** 12

### NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE
```

**描述：**

约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置最小宽度，单位为vp。取值范围：[0, +∞)。默认值：0。</li> <li>.value[1].f32：设置最大宽度，单位为vp。取值范围：[0, +∞)。默认值：无限制。</li> <li>.value[2].f32：设置最小高度，单位为vp。取值范围：[0, +∞)。默认值：0。</li> <li>.value[3].f32：设置最大高度，单位为vp。取值范围：[0, +∞)。默认值：无限制。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：最小宽度，单位为vp。</li> <li>.value[1].f32：最大宽度，单位为vp。</li> <li>.value[2].f32：最小高度，单位为vp。</li> <li>.value[3].f32：最大高度，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_OFFSET

```c
NODE_OFFSET
```

**描述：**

组件子元素相对组件自身的额外偏移属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置x轴偏移量，单位为vp。取值范围：(-∞, +∞)。默认值：0。</li> <li>.value[1].f32：设置y轴偏移量，单位为vp。取值范围：(-∞, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：相对于组件自身的x轴偏移量，单位为vp。</li> <li>.value[1].f32：相对于组件自身的y轴偏移量，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR
```

**描述：**

组件子元素在位置定位时的锚点属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置锚点x轴坐标，单位为vp。取值范围：(-∞, +∞)。默认值：0。</li> <li>.value[1].f32：设置锚点y轴坐标，单位为vp。取值范围：(-∞, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：锚点在组件坐标系中的x轴坐标，单位为vp。</li> <li>.value[1].f32：锚点在组件坐标系中的y轴坐标，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES
```

**描述：**

相对容器中子组件的对齐规则属性，支持属性设置，属性重置，获取属性接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：设置相对容器中子组件的对齐规则，参数类型为ArkUI_AlignmentRuleOption。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：相对容器中子组件的对齐规则，参数类型为ArkUI_AlignmentRuleOption。</li> </ul>

**起始版本：** 12

### NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF
```

**描述：**

设置子组件在父容器交叉轴的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在父容器交叉轴上的对齐方式，改变子组件在交叉轴方向的位置。参数类型[ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment)，默认值为 ARKUI_ITEM_ALIGNMENT_AUTO。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在父容器交叉轴上的对齐方式，类型为[ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment)。</li> </ul>

**起始版本：** 12

### NODE_FLEX_GROW

```c
NODE_FLEX_GROW
```

**描述：**

设置组件在父容器的剩余空间所占比例，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件在父容器剩余空间中所占比例。取值范围：[0, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件在父容器剩余空间中所占比例。</li> </ul>

**起始版本：** 12

### NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK
```

**描述：**

设置父容器压缩尺寸分配给此属性所在组件的比例，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置父容器压缩尺寸分配给当前组件的比例。取值范围：[0, +∞)。默认值：1。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：父容器压缩尺寸分配给当前组件的比例。</li> </ul>

**起始版本：** 12

### NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS
```

**描述：**

设置组件的基准尺寸，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件在父容器主轴上的基准尺寸，单位为vp。取值范围：[0, +∞)。默认值：auto。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件在父容器主轴上的基准尺寸，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO
```

**描述：**

设置组件的宽高比，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件宽高比，格式为宽度/高度。取值范围：(0, +∞)。默认值：不设置宽高比约束。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件宽高比，格式为宽度/高度。设置后组件将按此比例调整尺寸。</li> </ul>

**起始版本：** 12

### NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT
```

**描述：**

Row/Column/Flex 布局下的子组件布局权重参数，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置组件在主轴上的布局权重，决定组件在剩余空间中的分配比例。取值范围：[0, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：组件在主轴上的布局权重，决定组件在剩余空间中的分配比例。</li> </ul>

**起始版本：** 12

### NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY
```

**描述：**

Row/Column/Flex(单行) 布局下的子组件在布局容器中显示的优先级。 当子组件的displayPriority大于1时，displayPriority数值越大，优先级越高。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置组件在布局容器中的显示优先级。取值范围：[0, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：组件在布局容器中的显示优先级。值越大优先级越高，空间不足时优先显示高优先级组件。</li> </ul>

**起始版本：** 12

### NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT
```

**描述：**

宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为百分比。取值范围：(0, +∞)。无默认值，不设置时由组件布局决定尺寸，使用子组件自身内容需要的宽度。传入异常值时返回错误码。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为百分比。</li> </ul>

**起始版本：** 12

### NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT
```

**描述：**

高度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置高度数值，单位为百分比。取值范围：(0, +∞)。无默认值，不设置时由组件布局决定尺寸，使用子组件自身内容需要的高度。传入异常值时返回错误码。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：高度数值，单位为百分比。</li> </ul>

**起始版本：** 12

### NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT
```

**描述：**

内间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的内间距百分比数值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的内间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的内间距百分比数值。 <ul> <li>.value[0].f32：设置上内间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[1].f32：设置右内间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[2].f32：设置下内间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[3].f32：设置左内间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上内间距数值，单位为百分比。</li> <li>.value[1].f32：右内间距数值，单位为百分比。</li> <li>.value[2].f32：下内间距数值，单位为百分比。</li> <li>.value[3].f32：左内间距数值，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT
```

**描述：**

外间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的外间距百分比数值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的外间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的外间距百分比数值。 <ul> <li>.value[0].f32：设置上外间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[1].f32：设置右外间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[2].f32：设置下外间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[3].f32：设置左外间距数值，单位为百分比。默认值为0。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上外间距数值，单位为百分比。</li> <li>.value[1].f32：右外间距数值，单位为百分比。</li> <li>.value[2].f32：下外间距数值，单位为百分比。</li> <li>.value[3].f32：左外间距数值，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE
```

**描述：**

指定以该组件为链头所构成的链的参数，支持属性设置、属性重置和属性获取接口。<br> 仅当父容器为RelativeContainer时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：链的方向，设置链在水平或垂直方向上排列。枚举[ArkUI_Axis](capi-layout-h.md#arkui_axis)。</li> <li>.value[1].i32：链的样式，设置链内组件的分布方式。枚举[ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：链的方向，类型为[ArkUI_Axis](capi-layout-h.md#arkui_axis)。</li> <li>.value[1].i32：链的样式，类型为[ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle)。</li> </ul>

**起始版本：** 12

### NODE_SIZE

```c
NODE_SIZE
```

**描述：**

设置高宽尺寸，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为vp。取值范围：[0, +∞)。</li> <li>.value[1].f32：设置高度数值，单位为vp。取值范围：[0, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为vp。</li> <li>.value[1].f32：高度数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为2。

**起始版本：** 12

### NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT
```

**描述：**

组件布局大小位置属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件x轴坐标，单位为px。取值范围：(-∞, +∞)。</li> <li>.value[1].i32：设置组件y轴坐标，单位为px。取值范围：(-∞, +∞)。</li> <li>.value[2].i32：设置组件宽度，单位为px。取值范围：[0, +∞)。</li> <li>.value[3].i32：设置组件高度，单位为px。取值范围：[0, +∞)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件x轴坐标，单位为px。</li> <li>.value[1].i32：组件y轴坐标，单位为px。</li> <li>.value[2].i32：组件宽度，单位为px。</li> <li>.value[3].i32：组件高度，单位为px。</li> </ul>

**起始版本：** 12

### NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

**描述：**

边框宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1: 只传入一个参数，表示统一设置四条边的边框宽度百分比数值。 <ul> <li>.value[0].f32：统一设置四条边的边框宽度数值，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> </ul> 2: 传入四个参数，表示分别设置四条边的边框宽度百分比数值。 <ul> <li>.value[0].f32：设置上边框的边框宽度，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[1].f32：设置右边框的边框宽度，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[2].f32：设置下边框的边框宽度，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[3].f32：设置左边框的边框宽度，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框的边框宽度，单位为百分比。</li> <li>.value[1].f32：右边框的边框宽度，单位为百分比。</li> <li>.value[2].f32：下边框的边框宽度，单位为百分比。</li> <li>.value[3].f32：左边框的边框宽度，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

**描述：**

边框圆角属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1: 只传入一个参数，表示统一设置四个角的边框圆角半径百分比数值。 <ul> <li>.value[0].f32：统一设置四个角的边框圆角半径数值，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> </ul> 2: 传入四个参数，表示分别设置四个角的边框圆角半径百分比数值。 <ul> <li>.value[0].f32：设置左上角圆角半径，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[1].f32：设置右上角圆角半径，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[2].f32：设置左下角圆角半径，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> <li>.value[3].f32：设置右下角圆角半径，单位为百分比。取值范围：[0, +∞)。默认值：0。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：左上角圆角半径，单位为百分比。</li> <li>.value[1].f32：右上角圆角半径，单位为百分比。</li> <li>.value[2].f32：左下角圆角半径，单位为百分比。</li> <li>.value[3].f32：右下角圆角半径，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 12

### NODE_EXPAND_SAFE_AREA

```c
NODE_EXPAND_SAFE_AREA = 92
```

**描述：**

定义控制组件扩展其安全区域，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.u32：设置扩展安全区域的枚举值集合[ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype)，例如：ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT。</li> <li>.value[1]?.u32：设置扩展安全区域的方向枚举值集合[ArkUI_SafeAreaEdge](capi-layout-h.md#arkui_safeareaedge)。例如：ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：扩展安全区域。</li> <li>.value[1].u32：扩展安全区域的方向。</li> </ul>

**起始版本：** 12

### NODE_WIDTH_LAYOUTPOLICY

```c
NODE_WIDTH_LAYOUTPOLICY = 105
```

**描述：**

设置组件宽度布局策略，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件宽度布局策略，参数类型[ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy)，默认值：ARKUI_LAYOUT_POLICY_WRAP_CONTENT。设置异常值时，按默认值显示。 </li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件宽度布局策略，参数类型[ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy)，默认值：ARKUI_LAYOUT_POLICY_WRAP_CONTENT。设置异常值时，按默认值显示。 </li> </ul>

**起始版本：** 21

### NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

**描述：**

设置组件高度布局策略，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件高度布局策略，参数类型[ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy)，默认值：ARKUI_LAYOUT_POLICY_WRAP_CONTENT。设置异常值时，按默认值显示。 </li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件高度布局策略，参数类型[ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy)，默认值：ARKUI_LAYOUT_POLICY_WRAP_CONTENT。设置异常值时，按默认值显示。 </li> </ul>

**起始版本：** 21

### NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

**描述：**

设置组件相对容器内容区边界的位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：设置组件相对容器内容区边界的位置，参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：组件相对容器内容区边界的位置，参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li> </ul>

**起始版本：** 21

### NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

**描述：**

设置组件的像素取整策略，用于避免组件在缩放或非整数像素位置渲染时出现视觉锯齿等问题，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 **参数：**<br><ul> <li>.object：设置组件的像素取整策略；参数类型为[ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)。</li> </ul> **返回：**<br><ul> <li>.object：组件的像素取整策略；参数类型为[ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)。</li> </ul>

**起始版本：** 21

### NODE_CHAIN_WEIGHT

```c
NODE_CHAIN_WEIGHT = 118
```

**描述：**

父组件为RelativeContainer时，设置已形成链的组件的布局位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件在水平方向的布局权重，默认值：0。权重值越大，组件在链中占据的空间比例越大。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> <li>.value[1].f32：设置组件在竖直方向的布局权重，默认值：0。权重值越大，组件在链中占据的空间比例越大。取值范围：[0, +∞)。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件在水平方向的布局权重，权重值越大，组件在链中占据的空间比例越大。</li> <li>.value[1].f32：组件在竖直方向的布局权重，权重值越大，组件在链中占据的空间比例越大。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为2。

**起始版本：** 23

### NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

**描述：**

设置扩展组件布局时的安全区域，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置扩展安全区域的类型。参数类型为[ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype)，默认值：ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM。设置异常值时，按默认值显示。</li> <li>.value[1].u32：设置扩展安全区域的方向。参数类型为[ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge)，默认值：ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL，例如： ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：扩展安全区域的类型，类型为[ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype)。</li> <li>.value[1].u32：扩展安全区域的方向，类型为[ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge)。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为2。

**起始版本：** 23

### NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

**描述：**

设置边框样式为虚线时虚线的长度，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置上边框虚线的长度，单位vp，控制虚线段的长度。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[1].f32：设置右边框虚线的长度，单位vp，控制虚线段的长度。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[2].f32：设置下边框虚线的长度，单位vp，控制虚线段的长度。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[3].f32：设置左边框虚线的长度，单位vp，控制虚线段的长度。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框虚线的长度，单位vp。</li> <li>.value[1].f32：右边框虚线的长度，单位vp。</li> <li>.value[2].f32：下边框虚线的长度，单位vp。</li> <li>.value[3].f32：左边框虚线的长度，单位vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 23

### NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

**描述：**

设置边框样式为虚线时虚线的间隙，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置上边框虚线的间隙，单位vp，控制虚线段之间的间隔。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[1].f32：设置右边框虚线的间隙，单位vp，控制虚线段之间的间隔。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[2].f32：设置下边框虚线的间隙，单位vp，控制虚线段之间的间隔。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> <li>.value[3].f32：设置左边框虚线的间隙，单位vp，控制虚线段之间的间隔。取值范围：[0, +∞)。默认值：NODE_BORDER_WIDTH属性的边框宽度值。设置异常值时，按默认的虚线效果显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框虚线的间隙，单位vp。</li> <li>.value[1].f32：右边框虚线的间隙，单位vp。</li> <li>.value[2].f32：下边框虚线的间隙，单位vp。</li> <li>.value[3].f32：左边框虚线的间隙，单位vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为4。

**起始版本：** 23

### NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

**描述：**

设置Stack容器中子组件的对齐规则，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置Stack容器中子组件的对齐规则，决定子组件在Stack容器中的位置。参数类型为[ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment)，默认值： ARKUI_LOCALIZED_ALIGNMENT_CENTER。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：Stack容器中子组件的对齐规则，类型为[ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment)。</li> </ul>

**起始版本：** 23

### NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

**描述：**

设置组件绘制圆角的模式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件绘制圆角的模式，影响圆角的渲染效果和性能。参数类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)，默认值：ARKUI_RENDERSTRATEGY_FAST。FAST模式 直接裁剪圆角，渲染性能优先；OFFSCREEN模式使用离屏渲染优化圆角效果，可能影响性能。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件绘制圆角的模式，类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)。</li> </ul>

**起始版本：** 23

### NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK
```

**描述：**

设置子组件在Stack容器中的对齐方式，支持属性设置，属性重置和属性获取接口。<br> 该属性与通用属性NODE_ALIGNMENT同时设置时，后设置的属性生效。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：对齐方式，数据类型[ArkUI_Alignment](capi-layout-h.md#arkui_alignment)。可选取值包括TOP（顶部对齐）、BOTTOM（底部对齐）、LEFT（左侧对齐）、RIGHT（右侧对齐）、TOP_START （左上角对齐）、TOP_END（右上角对齐）、BOTTOM_START（左下角对齐）、BOTTOM_END（右下角对齐）、CENTER（居中对齐）、START（起始端对齐）、END（结束端对齐）。具体枚举值与数字对应关系请参考 [ArkUI_Alignment](capi-layout-h.md#arkui_alignment)定义。当需要子组件在容器内的特定位置对齐时选择相应的对齐方式。默认值：ARKUI_ALIGNMENT_CENTER（居中对齐）。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：对齐方式的枚举值，数据类型[ArkUI_Alignment](capi-layout-h.md#arkui_alignment)。具体取值及含义参见参数说明。</li> </ul>

**起始版本：** 12

### NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN
```

**描述：**

设置子组件在Column容器中水平方向上的对齐方式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对 齐）。具体枚举值与数字对应关系请参考[ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment)定义。当需要子组件在Column容器内水平方向特定位置对齐时选择相应的对齐格式。默认值： ARKUI_HORIZONTAL_ALIGNMENT_CENTER（居中对齐）。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在水平方向上的对齐格式的枚举值，数据类型[ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment)。具体取值及含义参见参数说明。</li> </ul>

**起始版本：** 12

### NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT
```

**描述：**

设置子组件在Column容器中垂直方向上的对齐方式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对齐）、 SPACE_BETWEEN（两端对齐）、SPACE_AROUND（环绕对齐）、SPACE_EVENLY（均匀对齐）。具体枚举值与数字对应关系请参考[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)定义。当需要子元素在 Column容器内垂直方向特定分布方式时选择相应的对齐格式。默认值：ARKUI_FLEX_ALIGNMENT_START（起始端对齐）。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在垂直方向上的对齐格式的枚举值，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。具体取值及含义参见参数说明。</li> </ul>

**起始版本：** 12

### NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE
```

**描述：**

设置Column或Row容器中子组件的间距，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：子组件之间的间距，单位：vp，默认值：0。取值范围：`[0, +∞)`。当需要为Column或Row容器的子组件之间添加间隔时设置此参数，设置为0表示无间距。设置异常值时，按默认值显示。 </li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：子组件之间的间距，单位：vp。</li> </ul>

**起始版本：** 23

### NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE
```

**描述：**

设置Column或Row容器中沿主轴方向的子组件排列是否反向，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：主轴方向的子组件排列是否反向，默认值：0（false）。值为非零整数时，子组件沿主轴方向反转排列（适用于从右到左或从下到上的布局需求）；值为0时，子组件沿主轴方向正序排列（适用于常规布局）。 当需要实现反向排列效果（如列表倒序显示）时设置为非零值，否则设置为0。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：主轴方向的子组件排列是否反向。返回非零值表示反向排列，返回0表示正序排列。</li> </ul>

**起始版本：** 23

### NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW
```

**描述：**

设置子组件在Row容器中垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在垂直方向上的对齐格式，数据类型[ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment)。可选取值包括TOP（顶部对齐）、CENTER（居中对齐）、BOTTOM（底部对齐）。具体 枚举值与数字对应关系请参考[ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment)定义。当需要子组件在Row容器内垂直方向特定位置对齐时选择相应的对齐格式。默认值： ARKUI_VERTICAL_ALIGNMENT_CENTER（居中对齐）。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在垂直方向上的对齐格式的枚举值，数据类型[ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment)。具体取值及含义参见参数说明。</li> </ul>

**起始版本：** 12

### NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT
```

**描述：**

设置Row子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在水平方向上的对齐格式，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对齐）、 SPACE_BETWEEN（两端对齐）、SPACE_AROUND（环绕对齐）、SPACE_EVENLY（均匀对齐）。具体枚举值与数字对应关系请参考[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)定义。当需要子元素在Row 容器内水平方向特定分布方式时选择相应的对齐格式。默认值：ARKUI_FLEX_ALIGNMENT_START（起始端对齐）。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在水平方向上的对齐格式的枚举值，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。具体取值及含义参见参数说明。</li> </ul>

**起始版本：** 12

### NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX
```

**描述：**

设置Flex属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.i32：子组件在Flex容器上排列的方向[ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection)。可选取值包括ROW（水平方向从左到右排列）、ROW_REVERSE（水平方向从右到左排列）、 COLUMN（垂直方向从上到下排列）、COLUMN_REVERSE（垂直方向从下到上排列）。具体枚举值与数字对应关系请参考[ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection)定义。当需要实现水平布局时选择ROW或 ROW_REVERSE，需要实现垂直布局时选择COLUMN或COLUMN_REVERSE。默认值为ARKUI_FLEX_DIRECTION_ROW（水平方向从左到右排列）。设置异常值时，按默认值显示。</li> <li>.value[1]?.i32：排列规则[ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap)。可选取值包括NO_WRAP（不换行，子元素超出容器时压缩显示）、WRAP（正向换行，子元素超出容器时自动换行）、 WRAP_REVERSE（反向换行，换行方向与正向相反）。具体枚举值与数字对应关系请参考[ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap)定义。当需要子元素在单行/单列显示时选择NO_WRAP，需要自动换行显示时选择WRAP或 WRAP_REVERSE。默认值为ARKUI_FLEX_WRAP_NO_WRAP（不换行）。设置异常值时，按默认值显示。</li> <li>.value[2]?.i32：主轴上的对齐格式[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对齐）、SPACE_BETWEEN（两 端对齐，元素间间距相等）、SPACE_AROUND（环绕对齐，元素两侧间距相等）、SPACE_EVENLY（均匀对齐，元素间及两端间距相等）。具体枚举值与数字对应关系请参考[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment) 定义。当需要子元素在主轴上特定分布方式时选择相应的对齐格式。默认值为ARKUI_FLEX_ALIGNMENT_START（起始端对齐）。设置异常值时，按默认值显示。</li> <li>.value[3]?.i32：交叉轴上的对齐格式[ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对齐）、STRETCH（拉伸填充）、 BASELINE（基线对齐）。具体枚举值与数字对应关系请参考[ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment)定义。当需要子元素在交叉轴上特定对齐方式时选择相应的对齐格式。默认值为 ARKUI_ITEM_ALIGNMENT_START（起始端对齐）。设置异常值时，按默认值显示。</li> <li>.value[4]?.i32：交叉轴中有额外的空间时，多行内容的对齐方式[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。可选取值包括START（起始端对齐）、CENTER（居中对齐）、END（结束端对齐）、 SPACE_BETWEEN（两端对齐，行间距相等）、SPACE_AROUND（环绕对齐，行两侧间距相等）、SPACE_EVENLY（均匀对齐，行间及两端间距相等）。具体枚举值与数字对应关系请参考 [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)定义。当Flex容器换行时，需要控制多行在交叉轴上的分布方式时选择相应的对齐格式。默认值为ARKUI_FLEX_ALIGNMENT_START（起始端对齐）。设置异常值时， 按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在Flex容器上排列的方向的枚举值，数据类型[ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection)。具体取值及含义参见参数说明。</li> <li>.value[1].i32：排列规则的枚举值，数据类型[ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap)。具体取值及含义参见参数说明。</li> <li>.value[2].i32：主轴上的对齐格式的枚举值，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。具体取值及含义参见参数说明。</li> <li>.value[3].i32：交叉轴上的对齐格式的枚举值，数据类型[ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment)。具体取值及含义参见参数说明。</li> <li>.value[4].i32：交叉轴中有额外的空间时，多行内容的对齐方式的枚举值，数据类型[ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment)。具体取值及含义参见参数说明。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为5。

**起始版本：** 12

### NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE
```

**描述：**

设置Flex容器内子组件的间距，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：Flex容器主轴方向的间距，单位：vp，默认值：0。取值范围：`[0, +∞)`。当需要为Flex容器内的子元素在主轴方向添加间距时设置此参数，设置为0表示无间距。设置异常值时，按默认值显 示。</li> <li>.value[1].f32：Flex容器交叉轴方向的间距，单位：vp，默认值：0。取值范围：`[0, +∞)`。当Flex容器换行时，需要为不同行之间在交叉轴方向添加间距时设置此参数，设置为0表示无间距。设置异常值时， 按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：Flex容器主轴方向的间距，单位：vp。</li> <li>.value[1].f32：Flex容器交叉轴方向的间距，单位：vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值，实际返回的value数组长度恒为2。

**起始版本：** 23

### NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER
```

**描述：**

设置RelativeContainer容器内的辅助线，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContainer容器内的辅助线，用于辅助子组件定位，参数类型为ArkUI_GuidelineOption。当需要在RelativeContainer中定义辅助定位线， 用于子组件相对辅助线定位时设置此参数。不传入时不设置辅助线。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContainer容器内的辅助线，参数类型为ArkUI_GuidelineOption。未设置辅助线时，获取接口返回NULL。</li> </ul>

**起始版本：** 12

### NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER
```

**描述：**

设置RelativeContainer容器内的屏障，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContainer容器内的屏障，用于约束子组件的布局边界，参数类型为ArkUI_BarrierOption。当需要在RelativeContainer中定义屏障，用于约 束子组件的布局边界时设置此参数。不传入时不设置屏障。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContainer容器内的屏障，参数类型为ArkUI_BarrierOption。未设置屏障时，获取接口返回NULL。</li> </ul>

**起始版本：** 12


