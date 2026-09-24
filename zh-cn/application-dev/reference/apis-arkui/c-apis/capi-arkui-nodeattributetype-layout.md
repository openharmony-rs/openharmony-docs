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

宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_HEIGHT

```c
NODE_HEIGHT
```

**描述：**

高度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置高度数值，单位为vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：高度数值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_PADDING

```c
NODE_PADDING
```

**描述：**

内间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的内间距值。 <ul> <li>.value[0].f32：统一设置内间距数值，单位为vp。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的内间距值。 <ul> <li>.value[0].f32：设置上内间距数值，单位为vp，默认值为0vp。</li> <li>.value[1].f32：设置右内间距数值，单位为vp，默认值为0vp。</li> <li>.value[2].f32：设置下内间距数值，单位为vp，默认值为0vp。</li> <li>.value[3].f32：设置左内间距数值，单位为vp，默认值为0vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上内间距数值，单位为vp。</li> <li>.value[1].f32：右内间距数值，单位为vp。</li> <li>.value[2].f32：下内间距数值，单位为vp。</li> <li>.value[3].f32：左内间距数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_MARGIN

```c
NODE_MARGIN
```

**描述：**

外间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的外间距值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的外间距值，单位为vp。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的外间距值。 <ul> <li>.value[0].f32：设置上外间距数值，单位为vp，默认值为0vp。</li> <li>.value[1].f32：设置右外间距数值，单位为vp，默认值为0vp。</li> <li>.value[2].f32：设置下外间距数值，单位为vp，默认值为0vp。</li> <li>.value[3].f32：设置左外间距数值，单位为vp，默认值为0vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上外间距数值，单位为vp。</li> <li>.value[1].f32：右外间距数值，单位为vp。</li> <li>.value[2].f32：下外间距数值，单位为vp。</li> <li>.value[3].f32：左外间距数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_ALIGNMENT

```c
NODE_ALIGNMENT
```

**描述：**

设置组件内容在元素绘制区域内的对齐方式，支持属性设置，属性重置和属性获取接口。<br> 在Stack中该属性与NODE_STACK_ALIGN_CONTENT效果一致，只能设置子组件在容器内的对齐方式。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32： 设置对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32： 对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。</li> </ul>

**起始版本：** 12

### NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH
```

**描述：**

边框宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置四条边的边框宽度。 <ul> <li>.value[0].f32：统一设置四条边的边框宽度，单位为vp。</li> </ul> 2. 传入四个参数，表示分别设置四条边的边框宽度。 <ul> <li>.value[0].f32：设置上边框的边框宽度，单位为vp，默认值为0vp。</li> <li>.value[1].f32：设置右边框的边框宽度，单位为vp，默认值为0vp。</li> <li>.value[2].f32：设置下边框的边框宽度，单位为vp，默认值为0vp。</li> <li>.value[3].f32：设置左边框的边框宽度，单位为vp，默认值为0vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框的边框宽度。</li> <li>.value[1].f32：右边框的边框宽度。</li> <li>.value[2].f32：下边框的边框宽度。</li> <li>.value[3].f32：左边框的边框宽度。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS
```

**描述：**

边框圆角属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置四条边的边框圆角。 <ul> <li>.value[0].f32：统一设置四条边的边框圆角。</li> </ul> 2. 传入四个参数，表示分别设置四条边的边框圆角。 <ul> <li>.value[0].f32：设置左上角圆角半径，单位为vp，默认值为0vp。</li> <li>.value[1].f32：设置右上角圆角半径，单位为vp，默认值为0vp。</li> <li>.value[2].f32：设置左下角圆角半径，单位为vp，默认值为0vp。</li> <li>.value[3].f32：设置右下角圆角半径，单位为vp，默认值为0vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：左上角圆角半径。</li> <li>.value[1].f32：右上角圆角半径。</li> <li>.value[2].f32：左下角圆角半径。</li> <li>.value[3].f32：右下角圆角半径。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR
```

**描述：**

边框颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1：统一设置四条边的边框颜色。 <ul> <li>.value[0].u32：统一设置四条边的边框颜色，使用0xargb表示，如`0xFFFF11FF`。</li> </ul> 2：分别设置四条边的边框颜色。 <ul> <li>.value[0].u32：设置上侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li> <li>.value[1].u32：设置右侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li> <li>.value[2].u32：设置下侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li> <li>.value[3].u32：设置左侧边框颜色，使用0xargb表示，默认值为0xFF000000。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：上侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li> <li>.value[1].u32：右侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li> <li>.value[2].u32：下侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li> <li>.value[3].u32：左侧边框颜色，使用0xargb表示，如0xFFFF11FF。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE
```

**描述：**

边框线条样式属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置四条边的边框线条样式。 <ul> <li>.value[0].i32：统一设置四条边的边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> </ul> 2. 传入四个参数，表示分别设置四条边的边框线条样式。 <ul> <li>.value[0].i32：设置上侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[1].i32：设置右侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[2].i32：设置下侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> <li>.value[3].i32：设置左侧边框线条样式，参数类型[ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle)，默认值为ARKUI_BORDER_STYLE_SOLID。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：上侧边框线条样式对应的数值。</li> <li>.value[1].i32：右侧边框线条样式对应的数值。</li> <li>.value[2].i32：下侧边框线条样式对应的数值。</li> <li>.value[3].i32：左侧边框线条样式对应的数值。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_POSITION

```c
NODE_POSITION
```

**描述：**

元素左上角相对于父容器左上角偏移位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置x轴坐标。</li> <li>.value[1].f32: 设置y轴坐标。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：x轴坐标。</li> <li>.value[1].f32: y轴坐标。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_DIRECTION

```c
NODE_DIRECTION
```

**描述：**

设置容器元素内主轴方向上的布局，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置容器元素内主轴方向上的布局类型，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：容器元素内主轴方向上的布局类型，参数类型[ArkUI_Direction](capi-native-type-h.md#arkui_direction)，默认值为ARKUI_DIRECTION_AUTO。</li> </ul>

**起始版本：** 12

### NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE
```

**描述：**

约束尺寸属性，组件布局时，进行尺寸范围限制，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置最小宽度，单位vp。</li> <li>.value[1].f32：设置最大宽度，单位vp。</li> <li>.value[2].f32：设置最小高度，单位vp。</li> <li>.value[3].f32：设置最大高度，单位vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：最小宽度，单位vp。</li> <li>.value[1].f32：最大宽度，单位vp。</li> <li>.value[2].f32：最小高度，单位vp。</li> <li>.value[3].f32：最大高度，单位vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_OFFSET

```c
NODE_OFFSET
```

**描述：**

组件子元素相对组件自身的额外偏移属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32 设置x轴方向的偏移值, 单位为vp。</li> <li>.value[1].f32 设置y轴方向的偏移值, 单位为vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32 x轴方向的偏移值, 单位为vp。</li> <li>.value[1].f32 y轴方向的偏移值, 单位为vp。</li> </ul>

**起始版本：** 12

### NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR
```

**描述：**

组件子元素在位置定位时的锚点属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32 设置锚点x坐标值, 单位为vp。</li> <li>.value[1].f32 设置锚点y坐标值, 单位为vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32 锚点x坐标值, 单位为vp。</li> <li>.value[1].f32 锚点y坐标值, 单位为vp。</li> </ul>

**起始版本：** 12

### NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES
```

**描述：**

相对容器中子组件的对齐规则属性，支持属性设置，属性重置，获取属性接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul><br><li>.object：设置相对容器中子组件的对齐规则，参数类型为{@link ArkUI_AlignmentRuleOption}。</li><br></ul><br>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：相对容器中子组件的对齐规则，参数类型为{@link ArkUI_AlignmentRuleOption}。</li> </ul>

**起始版本：** 12

### NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF
```

**描述：**

设置子组件在父容器交叉轴的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在父容器交叉轴的对齐格式类型，参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在父容器交叉轴的对齐格式类型，参数类型[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_AUTO。</li> </ul>

**起始版本：** 12

### NODE_FLEX_GROW

```c
NODE_FLEX_GROW
```

**描述：**

设置组件在父容器的剩余空间所占比例，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置父容器的剩余空间所占比例。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：父容器的剩余空间所占比例。</li> </ul>

**起始版本：** 12

### NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK
```

**描述：**

设置父容器压缩尺寸分配给此属性所在组件的比例，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置父容器压缩尺寸分配给此属性所在组件的比例数值。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：父容器压缩尺寸分配给此属性所在组件的比例数值。</li> </ul>

**起始版本：** 12

### NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS
```

**描述：**

设置组件的基准尺寸，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件在父容器主轴方向上的基准尺寸。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件在父容器主轴方向上的基准尺寸。</li> </ul>

**起始版本：** 12

### NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO
```

**描述：**

设置组件的宽高比，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件的宽高比，输入值为 width/height。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件的宽高比，width/height的比值。</li> </ul>

**起始版本：** 12

### NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT
```

**描述：**

Row/Column/Flex 布局下的子组件布局权重参数，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置子组件占主轴尺寸的权重。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：子组件占主轴尺寸的权重。</li> </ul>

**起始版本：** 12

### NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY
```

**描述：**

Row/Column/Flex(单行) 布局下的子组件在布局容器中显示的优先级。 当子组件的displayPriority大于1时，displayPriority数值越大，优先级越高。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置子组件在父容器中的显示优先级。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：子组件在父容器中的显示优先级。</li> </ul>

**起始版本：** 12

### NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT
```

**描述：**

宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为百分比。</li> </ul>

**起始版本：** 12

### NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT
```

**描述：**

高度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置高度数值，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：高度数值，单位为百分比。</li> </ul>

**起始版本：** 12

### NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT
```

**描述：**

内间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的内间距百分比数值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的内间距数值，单位为百分比。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的内间距百分比数值。 <ul> <li>.value[0].f32：设置上内间距数值，单位为百分比。</li> <li>.value[1].f32：设置右内间距数值，单位为百分比。</li> <li>.value[2].f32：设置下内间距数值，单位为百分比。</li> <li>.value[3].f32：设置左内间距数值，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上内间距数值，单位为百分比。</li> <li>.value[1].f32：右内间距数值，单位为百分比。</li> <li>.value[2].f32：下内间距数值，单位为百分比。</li> <li>.value[3].f32：左内间距数值，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT
```

**描述：**

外间距属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1. 只传入一个参数，表示统一设置上下左右四个位置的外间距百分比数值。 <ul> <li>.value[0].f32：统一设置上下左右四个位置的外间距数值，单位为百分比。</li> </ul> 2. 传入四个参数，表示分别设置上下左右四个位置的外间距百分比数值。 <ul> <li>.value[0].f32：设置上外间距数值，单位为百分比。</li> <li>.value[1].f32：设置右外间距数值，单位为百分比。</li> <li>.value[2].f32：设置下外间距数值，单位为百分比。</li> <li>.value[3].f32：设置左外间距数值，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上外间距数值，单位为百分比。</li> <li>.value[1].f32：右外间距数值，单位为百分比。</li> <li>.value[2].f32：下外间距数值，单位为百分比。</li> <li>.value[3].f32：左外间距数值，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE
```

**描述：**

指定以该组件为链头所构成的链的参数，支持属性设置、属性重置和属性获取接口。<br> 仅当父容器为RelativeContainer时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul><br><li>.value[0].i32：设置链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。</li><br><li>.value[1].i32：设置链的样式。枚举{@link ArkUI_RelativeLayoutChainStyle}。</li><br></ul><br>**属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul><br><li>.value[0].i32：链的方向。枚举[ArkUI_Axis](capi-native-type-h.md#arkui_axis)。</li><br><li>.value[1].i32：链的样式。枚举{@link ArkUI_RelativeLayoutChainStyle}。</li> </ul>

**起始版本：** 12

### NODE_SIZE

```c
NODE_SIZE
```

**描述：**

设置高宽尺寸，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置宽度数值，单位为vp。</li> <li>.value[1].f32：设置高度数值，单位为vp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：宽度数值，单位为vp。</li> <li>.value[1].f32：高度数值，单位为vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT
```

**描述：**

组件布局大小位置属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件X轴坐标，单位为px。</li> <li>.value[1].i32：设置组件Y轴坐标，单位为px。</li> <li>.value[2].i32：设置组件宽度，单位为px。</li> <li>.value[3].i32：设置组件高度，单位为px。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件X轴坐标，单位为px。</li> <li>.value[1].i32：组件Y轴坐标，单位为px。</li> <li>.value[2].i32：组件宽度，单位为px。</li> <li>.value[3].i32：组件高度，单位为px。</li> </ul>

**起始版本：** 12

### NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

**描述：**

边框宽度属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1: 只传入一个参数，表示统一设置四条边的边框宽度百分比数值。 <ul> <li>.value[0].f32：统一设置四条边的边框宽度，单位为百分比。</li> </ul> 2: 传入四个参数，表示分别设置四条边的边框宽度百分比数值。 <ul> <li>.value[0].f32：设置上边框的边框宽度，单位为百分比。</li> <li>.value[1].f32：设置右边框的边框宽度，单位为百分比。</li> <li>.value[2].f32：设置下边框的边框宽度，单位为百分比。</li> <li>.value[3].f32：设置左边框的边框宽度，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框的边框宽度，单位为百分比。</li> <li>.value[1].f32：右边框的边框宽度，单位为百分比。</li> <li>.value[2].f32：下边框的边框宽度，单位为百分比。</li> <li>.value[3].f32：左边框的边框宽度，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

**描述：**

边框圆角属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式有两种：**<br>1: 只传入一个参数，表示统一设置四条边的边框圆角半径百分比数值。 <ul> <li>.value[0].f32：统一设置四条边的边框圆角半径百分比数值，单位为百分比。</li> </ul> 2: 传入四个参数，表示分别设置四条边的边框圆角半径百分比数值。 <ul> <li>.value[0].f32：设置左上角圆角半径，单位为百分比。</li> <li>.value[1].f32：设置右上角圆角半径，单位为百分比。</li> <li>.value[2].f32：设置左下角圆角半径，单位为百分比。</li> <li>.value[3].f32：设置右下角圆角半径，单位为百分比。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：左上角圆角半径，单位为百分比。</li> <li>.value[1].f32：右上角圆角半径，单位为百分比。</li> <li>.value[2].f32：左下角圆角半径，单位为百分比。</li> <li>.value[3].f32：右下角圆角半径，单位为百分比。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_EXPAND_SAFE_AREA

```c
NODE_EXPAND_SAFE_AREA = 92
```

**描述：**

定义控制组件扩展其安全区域，支持属性设置，属性重置和属性获取。<br> **属性设置方法[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)参数格式：**<br><ul> <li>.value[0]?.u32：设置扩展安全区域的枚举值集合[ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype)，例如：ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT。</li> <li>.value[1]?.u32：设置扩展安全区域的方向枚举值集合[ArkUI_SafeAreaEdge](capi-native-type-h.md#arkui_safeareaedge)。例如：ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：扩展安全区域。</li> <li>.value[1].u32：扩展安全区域的方向。</li> </ul>

**起始版本：** 12

### NODE_WIDTH_LAYOUTPOLICY

```c
NODE_WIDTH_LAYOUTPOLICY = 105
```

**描述：**

设置组件宽度布局策略，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件宽度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件宽度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li> </ul>

**起始版本：** 21

### NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

**描述：**

设置组件高度布局策略，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件高度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件高度布局策略；参数类型为[ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy)。</li> </ul>

**起始版本：** 21

### NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

**描述：**

设置组件相对容器内容区边界的位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：设置组件相对容器内容区边界的位置；参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：组件相对容器内容区边界的位置；参数类型为[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)。</li> </ul>

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

父组件为RelativeContainer时，设置已形成链的组件的布局位置，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置组件在水平方向的布局权重，默认值：0。设置异常值时，按默认值显示。</li> <li>.value[1].f32：设置组件在竖直方向的布局权重，默认值：0。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：组件在水平方向的布局权重。</li> <li>.value[1].f32：组件在竖直方向的布局权重。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 23

### NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

**描述：**

设置扩展组件布局时的安全区域，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：设置扩展安全区域的类型。参数类型为[ArkUI_LayoutSafeAreaType](capi-native-type-h.md#arkui_layoutsafeareatype)，默认值：ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM。设置异常值时，按默认值显示。</li> <li>.value[1].u32：设置扩展安全区域的方向。参数类型为[ArkUI_LayoutSafeAreaEdge](capi-native-type-h.md#arkui_layoutsafeareaedge)，默认值：ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL。例如：ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_START。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：扩展安全区域的类型。</li> <li>.value[1].u32：扩展安全区域的方向。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 23

### NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

**描述：**

设置边框样式为虚线时虚线的长度，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置上边框虚线的长度，单位vp。</li> <li>.value[1].f32：设置右边框虚线的长度，单位vp。</li> <li>.value[2].f32：设置下边框虚线的长度，单位vp。</li> <li>.value[3].f32：设置左边框虚线的长度，单位vp。取值范围：[0, +∞)设置异常值时，按默认的虚线效果显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框虚线的长度，单位vp。</li> <li>.value[1].f32：右边框虚线的长度，单位vp。</li> <li>.value[2].f32：下边框虚线的长度，单位vp。</li> <li>.value[3].f32：左边框虚线的长度，单位vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 23

### NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

**描述：**

设置边框样式为虚线时虚线的间隙，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置上边框虚线的间隙，单位vp。</li> <li>.value[1].f32：设置右边框虚线的间隙，单位vp。</li> <li>.value[2].f32：设置下边框虚线的间隙，单位vp。</li> <li>.value[3].f32：设置左边框虚线的间隙，单位vp。取值范围：[0, +∞)设置异常值时，按默认的虚线效果显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：上边框虚线的间隙，单位vp。</li> <li>.value[1].f32：右边框虚线的间隙，单位vp。</li> <li>.value[2].f32：下边框虚线的间隙，单位vp。</li> <li>.value[3].f32：左边框虚线的间隙，单位vp。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 23

### NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

**描述：**

设置Stack容器中子组件的对齐规则，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置Stack容器中子组件的对齐规则。参数类型为[ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment)，默认值：ARKUI_ALIGNMENT_CENTER。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：Stack容器中子组件的对齐规则。参数类型为[ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment)。</li> </ul>

**起始版本：** 23

### NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

**描述：**

设置组件绘制圆角的模式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置组件绘制圆角的模式。参数类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)，默认值：ARKUI_RENDERSTRATEGY_FAST。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：组件绘制圆角的模式。参数类型为[ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy)。</li> </ul>

**起始版本：** 23

### NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK
```

**描述：**

设置子组件在Stack容器中的对齐方式，支持属性设置，属性重置和属性获取接口。<br> 该属性与通用属性NODE_ALIGNMENT同时设置时，后设置的属性生效。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32： 设置子组件在Stack容器中的对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)，默认值ARKUI_ALIGNMENT_CENTER。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32： 子组件在Stack容器中的对齐方式，数据类型[ArkUI_Alignment](capi-native-type-h.md#arkui_alignment)。</li> </ul>

**起始版本：** 12

### NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN
```

**描述：**

设置子组件在Column容器中水平方向上的对齐方式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在Column容器中水平方向上的对齐方式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)，默认值ARKUI_HORIZONTAL_ALIGNMENT_CENTER。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：Column子组件在Column容器中水平方向上的对齐方式，数据类型[ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment)。</li> </ul>

**起始版本：** 12

### NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT
```

**描述：**

设置子组件在Column容器中垂直方向上的对齐方式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在Column容器中垂直方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值ARKUI_FLEX_ALIGNMENT_START。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在Column容器中垂直方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。</li> </ul>

**起始版本：** 12

### NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE
```

**描述：**

设置Column或Row容器中子组件的间距，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置Column或Row容器中子组件之间的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:**<br><ul> <li>.value[0].f32：Column或Row容器中子组件之间的间距，单位vp。</li> </ul>

**起始版本：** 23

### NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE
```

**描述：**

设置Column或Row容器中沿主轴方向的子组件排列是否反向，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置Column或Row容器中沿主轴方向的子组件排列是否反向，默认值：false。值为true时，子组件在主轴方向上反转排列。值为false时，子组件在主轴方向上正序排列。设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:**<br><ul> <li>.value[0].i32：Column或Row容器中主轴方向的子组件排列是否反向。</li> </ul>

**起始版本：** 23

### NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW
```

**描述：**

设置子组件在Row容器中垂直方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在Row容器中垂直方向上的对齐方式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)，默认值ARKUI_VERTICAL_ALIGNMENT_CENTER。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在Row容器中垂直方向上的对齐方式，数据类型[ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment)。</li> </ul>

**起始版本：** 12

### NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT
```

**描述：**

设置Row子组件在水平方向上的对齐格式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置子组件在Row容器中水平方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值ARKUI_FLEX_ALIGNMENT_START。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在Row容器中水平方向上的对齐方式，数据类型[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)。</li> </ul>

**起始版本：** 12

### NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX
```

**描述：**

设置Flex属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.i32：设置子组件在Flex容器上排列的方向[ArkUI_FlexDirection](capi-native-type-h.md#arkui_flexdirection)，默认值为ARKUI_FLEX_DIRECTION_ROW。</li> <li>.value[1]?.i32：设置排列规则[ArkUI_FlexWrap](capi-native-type-h.md#arkui_flexwrap)，默认值为ARKUI_FLEX_WRAP_NO_WRAP。</li> <li>.value[2]?.i32：设置主轴上的对齐格式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START。</li> <li>.value[3]?.i32：设置交叉轴上的对齐格式[ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment)，默认值为ARKUI_ITEM_ALIGNMENT_START。</li> <li>.value[4]?.i32：设置交叉轴中有额外的空间时，多行内容的对齐方式[ArkUI_FlexAlignment](capi-native-type-h.md#arkui_flexalignment)，默认值为ARKUI_FLEX_ALIGNMENT_START。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：子组件在Flex容器上排列的方向的枚举值。</li> <li>.value[1].i32：排列规则的枚举值。</li> <li>.value[2].i32：主轴上的对齐格式的枚举值。</li> <li>.value[3].i32：交叉轴上的对齐格式的枚举值。</li> <li>.value[4].i32：交叉轴中有额外的空间时，多行内容的对齐方式的枚举值。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 12

### NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE
```

**描述：**

设置Flex容器内子组件的间距，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置Flex容器主轴方向的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li> <li>.value[1].f32：设置Flex容器交叉轴方向的间距，单位vp，默认值：0。取值范围：[0, +∞)设置异常值时，按默认值显示。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式:**<br><ul> <li>.value[0].f32：Flex容器主轴方向的间距，单位vp，默认值：0。</li> <li>.value[1].f32：Flex容器交叉轴方向的间距，单位vp，默认值：0。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)中size为无效值。

**起始版本：** 23

### NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER
```

**描述：**

设置RelativeContaine容器内的辅助线，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 设置RelativeContaine容器内的辅助线。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContaine容器内的辅助线。</li> </ul>

**起始版本：** 12

### NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER
```

**描述：**

设置RelativeContaine容器内的屏障，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 设置RelativeContaine容器内的屏障。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: RelativeContaine容器内的屏障。</li> </ul>

**起始版本：** 12


