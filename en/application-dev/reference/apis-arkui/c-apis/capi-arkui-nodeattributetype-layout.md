# Layout

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_WIDTH

```c
NODE_WIDTH = 0
```

**Description**

Width attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Width, in vp. Value range: [0, +∞). When an invalid value is set, the default value is used for display or the component size is abnormal.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width, in vp.</li> </ul>

**Since**: 12

### NODE_HEIGHT

```c
NODE_HEIGHT
```

**Description**

Height attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Height, in vp. Value range: [0, +∞). When an invalid value is set, the default value is displayed or the component size is abnormal. </li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Height, in vp.</li> </ul>

**Since**: 12

### NODE_PADDING

```c
NODE_PADDING
```

**Description**

Padding attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Padding for the four directions (top, bottom, left, and right), in vp. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> </ul> 2: Specify different padding values for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Top padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used.</li> <li>.value[1].f32: Right padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used.</li> <li>.value[2].f32: Bottom padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used.</li> <li>.value[3].f32: Left padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Top padding, in vp.</li> <li>.value[1].f32: Right padding, in vp.</li> <li>.value[2].f32: Bottom padding, in vp.</li> <li>.value[3].f32: Left padding, in vp.</li> </ul>

**Since**: 12

### NODE_MARGIN

```c
NODE_MARGIN
```

**Description**

Margin attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same margin for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Margin for the four directions (top, bottom, left, and right), in vp. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> </ul> 2: Specify different margins for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Top margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> <li>.value[1].f32: Right margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> <li>.value[2].f32: Bottom margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> <li>.value[3].f32: Left margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Top margin, in vp.</li> <li>.value[1].f32: Right margin, in vp.</li> <li>.value[2].f32: Bottom margin, in vp.</li> <li>.value[3].f32: Left margin, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGNMENT

```c
NODE_ALIGNMENT
```

**Description**

Alignment attribute for component content in the element drawing area, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH
```

**Description**

Border width attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: Specify the same width for the four borders. <ul> <li>.value[0].f32: Width for the four borders, in vp. Value range: [0, +∞). The default value is **0vp**.</li> </ul> 2: Specify different width values for the four borders. <ul> <li>.value[0].f32: Width of the top border, in vp. The default value is **0vp**. Value range: [0, +∞).</li> <li>.value[1].f32: Width of the right border, in vp. The default value is **0vp**. Value range: [0, +∞).</li> <li>.value[2].f32: Width of the bottom border, in vp. The default value is **0vp**. Value range: [0, +∞).</li> <li>.value[3].f32: Width of the left border, in vp. The default value is **0vp**. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width of the top border, in vp.</li> <li>.value[1].f32: Width of the right border, in vp.</li> <li>.value[2].f32: Width of the bottom border, in vp.</li> <li>.value[3].f32: Width of the left border, in vp.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS
```

**Description**

Border corner radius attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same corner radius for the four borders. <ul> <li>.value[0].f32: Corner radius for the four borders, in vp. Value range: [0, +∞). The default value is **0vp**<br>.</li> </ul> 2. Four parameters are passed, indicating respectively setting the border radius for each of the four corners. <ul> <li>.value[0].f32: Radius of the upper left corner, in vp. The default value is **0vp**. Value range: [0, + ∞).</li> <li>.value[1].f32: Radius of the upper right corner, in vp. The default value is **0vp**. Value range: [0, + ∞).</li> <li>.value[2].f32: Radius of the lower left corner, in vp. The default value is **0vp**. Value range: [0, + ∞).</li> <li>.value[3].f32: Radius of the lower right corner, in vp. The default value is **0vp**. Value range: [0, + ∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Radius of the upper left corner, in vp.</li> <li>.value[1].f32: Radius of the upper right corner, in vp.</li> <li>.value[2].f32: Radius of the lower left corner, in vp.</li> <li>.value[3].f32: Radius of the lower right corner, in vp.</li> </ul>

**Since**: 12

### NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR
```

**Description**

Border color attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: Specify the same color for the four borders. <ul> <li>.value[0].u32: Color for the four borders, in 0xARGB format, for example, `0xFFFF11FF`.</li> </ul> 2: Specify different colors for the four borders. <ul> <li>.value[0].u32: Color of the top border, in 0xARGB format. The default value is `0xFF000000`.</li> <li>.value[1].u32: Color of the right border, in 0xARGB format. The default value is `0xFF000000`.</li> <li>.value[2].u32: Color of the bottom border, in 0xARGB format. The default value is `0xFF000000`.</li> <li>.value[3].u32: Color of the left border, in 0xARGB format. The default value is `0xFF000000`.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Color of the top border, in 0xARGB format, for example, `0xFFFF11FF`.</li> <li>.value[1].u32: Color of the right border, in 0xARGB format, for example, `0xFFFF11FF`.</li> <li>.value[2].u32: Color of the bottom border, in 0xARGB format, for example, `0xFFFF11FF`.</li> <li>.value[3].u32: Color of the left border, in 0xARGB format, for example, `0xFFFF11FF`.</li> </ul>

**Since**: 12

### NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE
```

**Description**

Border line style attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: Specify the same line style for the four borders. <ul> <li>.value[0].i32: Line style for the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.</li> </ul> 2: Specify different line styles for the four borders. <ul> <li>.value[0].i32: Line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.</li> <li>.value[1].i32: Line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.</li> <li>.value[2].i32: Line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.</li> <li>.value[3].i32: Line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).</li> <li>.value[1].i32: Line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).</li> <li>.value[2].i32: Line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).</li> <li>.value[3].i32: Line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle).</li> </ul>

**Since**: 12

### NODE_POSITION

```c
NODE_POSITION
```

**Description**

Offset of the component's upper left corner relative to the parent container's. This attribute can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X-coordinate, in vp. Value range: (-∞, +∞).</li> <li>.value[1].f32: Y-coordinate, in vp. Value range: (-∞, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate, in vp.</li> <li>.value[1].f32: Y-coordinate, in vp.</li> </ul>

**Since**: 12

### NODE_DIRECTION

```c
NODE_DIRECTION
```

**Description**

Direction of the main axis within the container element. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Direction of the main axis, which is used to set the arrangement direction of child components in the container. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**<br>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction).</li> </ul>

**Since**: 12

### NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE
```

**Description**

Size constraint attribute, used to restricts the size range during component layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Minimum width, in vp. Value range: [0, +∞). Default value: **0**.</li> <li>.value[1].f32: Maximum width, in vp. Value range: [0, +∞). Default value: no limit.</li> <li>.value[2].f32: Minimum height, in vp. Value range: [0, +∞). Default value: **0**.</li> <li>.value[3].f32: Maximum height, in vp. Value range: [0, +∞). Default value: no limit.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Minimum width, in vp.</li> <li>.value[1].f32: Maximum width, in vp.</li> <li>.value[2].f32: Minimum height, in vp.</li> <li>.value[3].f32: Maximum height, in vp.</li> </ul>

**Since**: 12

### NODE_OFFSET

```c
NODE_OFFSET
```

**Description**

Additional offset of a component's child element relative to the component itself. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Offset along the x-axis, in vp. Value range: (-∞, +∞). Default value: **0**.</li> <li>.value[1].f32: Offset along the y-axis, in vp. Value range: (-∞, +∞). Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-axis offset relative to the component itself, in vp.</li> <li>.value[1].f32: Y-axis offset relative to the component itself, in vp.</li> </ul>

**Since**: 12

### NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR
```

**Description**

Anchor of a component's child element during locating. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X-coordinate of the anchor, in vp. Value range: (-∞, +∞). Default value: **0**.</li> <li>.value[1].f32: Y-coordinate of the anchor, in vp. Value range: (-∞, +∞). Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate of the anchor in the component's coordinate system, in vp.</li> <li>.value[1].f32: Y-coordinate of the anchor in the component's coordinate system, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES
```

**Description**

Alignment rules of the child components in the relative container. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Alignment rules of the child components in the relative container. The parameter type is ArkUI_AlignmentRuleOption.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Alignment rules of the child components in the relative container. The parameter type is ArkUI_AlignmentRuleOption.</li> </ul>

**Since**: 12

### NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF
```

**Description**

Alignment mode of the child component along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Alignment mode of the child component along the cross axis of the parent container, used to change the position of the child component along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_AUTO**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Alignment mode of the child component along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment).</li> </ul>

**Since**: 12

### NODE_FLEX_GROW

```c
NODE_FLEX_GROW
```

**Description**

Percentage of the parent container's remaining space that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Percentage of the parent container's remaining space that is allocated to the component. Value range: [0, +∞). Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Percentage of the parent container's remaining space that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK
```

**Description**

Percentage of the parent container's shrink size that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Percentage of the parent container's shrink size that is allocated to the current component. Value range: [0, +∞). Default value: **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Percentage of the parent container's shrink size that is allocated to the current component.</li> </ul>

**Since**: 12

### NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS
```

**Description**

Base size of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Base size of the component on the main axis of the parent container, in vp. Value range: [0, + ∞). Default value: **auto**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Base size of the component on the main axis of the parent container, in vp.</li> </ul>

**Since**: 12

### NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO
```

**Description**

Aspect ratio attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Aspect ratio of the component, in width/height format. Value range: (0, +∞). Default value: no aspect ratio constraint is set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Aspect ratio of the component, in width/height format. After being set, the component adjusts its size based on this ratio.</li> </ul>

**Since**: 12

### NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT
```

**Description**

Weight of the component within the **Row**, **Column**, or **Flex** layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Layout weight of the component along the main axis, which determines the allocation ratio of the component in the remaining space. Value range: [0, +∞). Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Layout weight of the component along the main axis, which determines the allocation ratio of the component in the remaining space.</li> </ul>

**Since**: 12

### NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY
```

**Description**

Display priority of the component within the **Row**, **Column**, or **Flex** (single-line) layout in the layout container. This attribute can be set, reset, and obtained as required through APIs.<br> When the value of **displayPriority** is greater than 1, a larger value indicates a higher priority.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Display priority of the component in the layout container. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Display priority of the component in the layout container. A larger value indicates a higher priority. When space is insufficient, components with higher priority are displayed first.</li> </ul>

**Since**: 12

### NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT
```

**Description**

Width attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Width, in percentage. Value range: (0, +∞). There is no default value. When not set, the size is determined by the component layout, using the width required by the child component's own content. When an invalid value is set, an error code is returned.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width, in percentage.</li> </ul>

**Since**: 12

### NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT
```

**Description**

Height attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Height, in percentage. Value range: (0, +∞). There is no default value. When not set, the size is determined by the component layout, using the height required by the child component's own content. When an invalid value is set, an error code is returned.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Height, in percentage.</li> </ul>

**Since**: 12

### NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT
```

**Description**

Padding attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Padding for the four directions, in percentage. The default value is **0**. Value range: [0, + ∞). When an invalid value is set, the default value is used for display.</li> </ul> 2: Specify different padding values for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Top padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[1].f32: Right padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[2].f32: Bottom padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[3].f32: Left padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Top padding, in percentage.</li> <li>.value[1].f32: Right padding, in percentage.</li> <li>.value[2].f32: Bottom padding, in percentage.</li> <li>.value[3].f32: Left padding, in percentage.</li> </ul>

**Since**: 12

### NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT
```

**Description**

Margin attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same margin for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Margin for the four directions, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> </ul> 2: Specify different margins for the four directions (top, bottom, left, and right). <ul> <li>.value[0].f32: Top margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[1].f32: Right margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[2].f32: Bottom margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[3].f32: Left margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Top margin, in percentage.</li> <li>.value[1].f32: Right margin, in percentage.</li> <li>.value[2].f32: Bottom margin, in percentage.</li> <li>.value[3].f32: Left margin, in percentage.</li> </ul>

**Since**: 12

### NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE
```

**Description**

Parameters of the chain in which the component is the head, used to control the distribution of multiple child components along the main axis or cross axis within a RelativeContainer. It is commonly used to implement scenarios where multiple components are evenly distributed along the same direction and maintain fixed spacing or alignment mode. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Direction of the chain, used to set whether the chain is arranged horizontally or vertically. The value is an enumerated value of [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li> <li>.value[1].i32: Style of the chain, used to set the distribution mode of components within the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Direction of the chain. The parameter type is [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li> <li>.value[1].i32: Style of the chain. The parameter type is [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle).</li> </ul>

**Since**: 12

### NODE_SIZE

```c
NODE_SIZE
```

**Description**

Size attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Width, in vp. Value range: [0, +∞).</li> <li>.value[1].f32: Height, in vp. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width, in vp.</li> <li>.value[1].f32: Height, in vp.</li> </ul>

**Since**: 12

### NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT
```

**Description**

Component size and position for layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: X-coordinate of the component, in px. Value range: (-∞, +∞).</li> <li>.value[1].i32: Y-coordinate of the component, in px. Value range: (-∞, +∞).</li> <li>.value[2].i32: Width of the component, in px. Value range: [0, +∞).</li> <li>.value[3].i32: Height of the component, in px. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: X-coordinate of the component, in px.</li> <li>.value[1].i32: Y-coordinate of the component, in px.</li> <li>.value[2].i32: Width of the component, in px.</li> <li>.value[3].i32: Height of the component, in px.</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

**Description**

Border width attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: Specify the same width for the four borders. <ul> <li>.value[0].f32: Width for the four borders, in percentage. Value range: [0, +∞). Default value: **0**.</li> </ul> 2: Specify different width values for the four borders. <ul> <li>.value[0].f32: Width of the top border, in percentage. Value range: [0, +∞). Default value: **0**.</li> <li>.value[1].f32: Width of the right border, in percentage. Value range: [0, +∞). Default value: **0**.</li> <li>.value[2].f32: Width of the bottom border, in percentage. Value range: [0, +∞). Default value: **0**.</li> <li>.value[3].f32: Width of the left border, in percentage. Value range: [0, +∞). Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width of the top border, in percentage.</li> <li>.value[1].f32: Width of the right border, in percentage.</li> <li>.value[2].f32: Width of the bottom border, in percentage.</li> <li>.value[3].f32: Width of the left border, in percentage.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

**Description**

Border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same corner radius for the four borders. <ul> <li>.value[0].f32: Corner radius for the four borders, in percentage. Value range: [0, +∞). Default value: **0**<br>.</li> </ul> 2. Specify different corner radii for the four borders. <ul> <li>.value[0].f32: Radius of the upper left corner, in percentage. Value range: [0, +∞). Default value: **0**<br>.</li> <li>.value[1].f32: Radius of the upper right corner, in percentage. Value range: [0, +∞). Default value: **0**<br>.</li> <li>.value[2].f32: Radius of the lower left corner, in percentage. Value range: [0, +∞). Default value: **0**<br>.</li> <li>.value[3].f32: Radius of the lower right corner, in percentage. Value range: [0, +∞). Default value: **0**<br>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Radius of the upper left corner, in percentage.</li> <li>.value[1].f32: Radius of the upper right corner, in percentage.</li> <li>.value[2].f32: Radius of the lower left corner, in percentage.</li> <li>.value[3].f32: Radius of the lower right corner, in percentage.</li> </ul>

**Since**: 12

### NODE_EXPAND_SAFE_AREA

```c
NODE_EXPAND_SAFE_AREA = 92
```

**Description**

Safe area to be expanded to. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.u32: Types of the expanded safe area, which are enumerated values of [ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype). Example: **ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT**.</li> <li>.value[1]?.u32: Types of the expanded safe area edge, which are enumerated values of [ArkUI_SafeAreaEdge](capi-layout-h.md#arkui_safeareaedge). Example: **ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Types of the expanded safe area.</li> <li>.value[1].u32: Edges for expanding the safe area.</li> </ul>

**Since**: 12

### NODE_WIDTH_LAYOUTPOLICY

```c
NODE_WIDTH_LAYOUTPOLICY = 105
```

**Description**

Width layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Width layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Width layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used.</li> </ul>

**Since**: 21

### NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

**Description**

Height layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Height layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Height layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display.</li> </ul>

**Since**: 21

### NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

**Description**

Position of the component relative to the edges of the container's content area. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Position of the component relative to the edges of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Position of the component relative to the edges of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul>

**Since**: 21

### NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

**Description**

Pixel rounding policy of the component, used to avoid issues such as visual aliasing when the component is rendered at a scaled size or non-integer-pixel position. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Pixel rounding policy of the component. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul>

**Since**: 21

### NODE_CHAIN_WEIGHT

```c
NODE_CHAIN_WEIGHT = 118
```

**Description**

Layout location of components that have formed a chain when the parent component is a RelativeContainer. This attribute is used to control the proportion of space occupied by each component in the chain along the chain direction, commonly applied to scenarios where components in the same chain are allocated remaining space by weight ratio. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Layout weight of the component in the horizontal direction. Default value: **0**. A larger weight value indicates a larger proportion of space the component occupies in the chain. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> <li>.value[1].f32: Layout weight of the component in the vertical direction. Default value: **0**. A larger weight value indicates a larger proportion of space the component occupies in the chain. Value range: [0, +∞). When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Layout weight of the component in the horizontal direction. A larger weight value indicates a larger proportion of space the component occupies in the chain.</li> <li>.value[1].f32: Layout weight of the component in the vertical direction. A larger weight value indicates a larger proportion of space the component occupies in the chain.</li> </ul>

**Since**: 23

### NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

**Description**

Safe area to be ignored when expanding the layout of the component, allowing components to extend into system UI areas such as the system status bar and navigation bar. This attribute is commonly used in scenarios requiring full-screen display, such as immersive video playback, full-screen games, and image viewers. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Type of the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype). The default value is **ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM**. If an invalid value is set, the default value is used.</li> <li>.value[1].u32: Edges for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge). The default value is **ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL**. Example: **ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM**. If an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Type of the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype).</li> <li>.value[1].u32: Edges for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge) .</li> </ul>

**Since**: 23

### NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

**Description**

Length of the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH**<br>attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Length of the dashed line on the top border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[1].f32: Length of the dashed line on the right border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[2].f32: Length of the dashed line on the bottom border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[3].f32: Length of the dashed line on the left border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Length of the dashed line on the top border, in vp.</li> <li>.value[1].f32: Length of the dashed line on the right border, in vp.</li> <li>.value[2].f32: Length of the dashed line on the bottom border, in vp.</li> <li>.value[3].f32: Length of the dashed line on the left border, in vp.</li> </ul>

**Since**: 23

### NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

**Description**

Gap between dashes on the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH**<br>attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Gap between dashes on the dash line of the top border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[1].f32: Gap between dashes on the dash line of the right border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[2].f32: Gap between dashes on the dash line of the bottom border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> <li>.value[3].f32: Gap between dashes on the dash line of the left border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Gap between dashes on the dash line of the top border, in vp.</li> <li>.value[1].f32: Gap between dashes on the dash line of the right border, in vp.</li> <li>.value[2].f32: Gap between dashes on the dash line of the bottom border, in vp.</li> <li>.value[3].f32: Gap between dashes on the dash line of the left border, in vp.</li> </ul>

**Since**: 23

### NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

**Description**

Alignment rule of the child components in the **Stack** container. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Alignment rule of the child components in the **Stack** container, determining the position of child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment). The default value is **ARKUI_LOCALIZED_ALIGNMENT_CENTER**. When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Alignment rule of the child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment).</li> </ul>

**Since**: 23

### NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

**Description**

Mode for drawing rounded corners of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Mode for rendering rounded corners of the component, which affects the rendering effect and performance of rounded corners. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is **ARKUI_RENDERSTRATEGY_FAST**. In FAST mode, rounded corners are directly clipped, prioritizing rendering performance. In OFFSCREEN mode, offscreen rendering is used to optimize the rounded corner effect, which may affect performance. When an invalid value is set, the default value is used for display.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Mode for rendering rounded corners of the component. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).</li> </ul>

**Since**: 23

### NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK
```

**Description**

Defines the alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The value options are as follows: **TOP** (top alignment), **BOTTOM** (bottom alignment), **LEFT** (left alignment), **RIGHT** (right alignment), **TOP_START** (top-left alignment), **TOP_END** (top-right alignment), **BOTTOM_START** (bottom-left alignment), **BOTTOM_END** (bottom-right alignment), **CENTER** (center alignment), **START** (alignment with the start edge), and **END** (alignment with the end edge). For the mapping between enumerated values and numbers, see [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). Select the corresponding alignment mode when a child component needs to be aligned at a specific position within the container. The default value is **ARKUI_ALIGNMENT_CENTER** (center alignment). When an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). For details about the values and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN
```

**Description**

Defines the horizontal alignment mode of child components in the column. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). The value options are as follows: **START** (alignment with the start edge), CENTER (center alignment), and END (alignment with the end edge). For the mapping between enumerated values and numbers, see [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). Select the corresponding alignment mode when child components need to be aligned at a specific horizontal position within a **Column** container. The default value is **ARKUI_HORIZONTAL_ALIGNMENT_CENTER** (center alignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). For details about the options and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT
```

**Description**

Vertical alignment mode of child components in the Column component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the vertical alignment mode of child components in a **Column** container needs to be controlled, such as top alignment, bottom alignment, center alignment, or justified alignment. This addresses the issue where the default vertical alignment mode of child components in a **Column** container does not meet requirements, providing flexible vertical alignment control for child components to achieve diverse vertical layout effects. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment), **SPACE_AROUND** (circular alignment), and **SPACE_EVENLY** (even alignment). For the mapping between enumerated values and numbers, see the definition of [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when a specific distribution of child elements in the **Column** container in the vertical direction is needed. The default value is **ARKUI_FLEX_ALIGNMENT_START** (alignment with the start edge).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE
```

**Description**

Spacing between the child components of **Column** or **Row**. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components in a **Column** or **Row** container needs to be controlled, such as the spacing between card list items or between buttons. This addresses the issue where the spacing between child components in a **Column** or **Row** container needs to be uniformly controlled, providing a convenient way to set spacing between child components and avoiding the need to set margins for each child component individually, thereby simplifying development. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Spacing between child components, in vp. Default value: **0**. Value range: `[0, +∞)`. Set this parameter when spacing is needed between child components of a **Column** or **Row** container. Setting it to **0** means no spacing. When an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Spacing between child components, in vp.</li> </ul>

**Since**: 23

### NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE
```

**Description**

Whether the child components along the main axis in **Column** or **Row** are arranged reversely. This attribute can be set, reset, and obtained through APIs. This attribute is used when the arrangement order of child components in a **Column** or **Row** container needs to be reversed, such as a chat message list (with the latest message at the bottom) or displaying list items in reverse order. This addresses the issue where child components in a **Column** or **Row** container need to be arranged in reverse, enabling a reversed arrangement effect without changing the data source order, thereby simplifying development logic. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the child components along the main axis are arranged reversely. Default value: **0**<br>(false). When the value is a non-zero integer, the child components are arranged in reverse order along the main axis (applicable to right-to-left or bottom-to-top layout requirements). When the value is 0, the child components are arranged in normal order along the main axis (applicable to general layout). Set this parameter to a non-zero value when a reverse arrangement effect is needed (such as displaying a list in reverse order); otherwise, set it to **0**. When an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the child components along the main axis are arranged reversely. A non-zero value indicates reverse arrangement, and **0** indicates normal order.</li> </ul>

**Since**: 23

### NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW
```

**Description**

Defines the vertical alignment mode of child components in the row. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). The value options are as follows: **TOP** (top alignment), **CENTER** (center alignment), and **BOTTOM** (bottom alignment). For the mapping between enumerated values and numbers, see [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). Select the corresponding alignment mode when the child component needs to be aligned at a specific vertical position within the **Row** container. The default value is **ARKUI_VERTICAL_ALIGNMENT_CENTER** (center alignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). For details about the values and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT
```

**Description**

Horizontal alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the horizontal alignment mode of child components in a **Row** container needs to be controlled, such as left alignment, right alignment, center distribution, or justified alignment. This addresses the issue where the default horizontal alignment mode of child components in a **Row** container does not meet requirements, providing flexible horizontal alignment control for child components to achieve diverse horizontal layout effects. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment), **SPACE_AROUND** (circular alignment), and **SPACE_EVENLY** (even alignment). For the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when child elements need a specific distribution along the horizontal axis within a **Row** container. The default value is **ARKUI_FLEX_ALIGNMENT_START** (start alignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX
```

**Description**

Defines the flex attribute. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.i32: Direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). The value options are as follows: **ROW** (horizontal, from left to right), **ROW_REVERSE** (horizontal, from right to left), **COLUMN** (vertical, from top to bottom), and **COLUMN_REVERSE** (vertical, from bottom to top). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). Select **ROW** or **ROW_REVERSE** when a horizontal layout is implemented, and **COLUMN** or **COLUMN_REVERSE** when a vertical layout is implemented. The default value is **ARKUI_FLEX_DIRECTION_ROW** (horizontal, from left to right). When an invalid value is set, the default value is used.</li> <li>.value[1]?.i32: Wrapping rule. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). The value options are as follows: **NO_WRAP** (no wrapping; child elements are compressed when they exceed the container boundary), **WRAP** (forward wrapping; child elements automatically wrap when they exceed the container boundary), and **WRAP_REVERSE** (reverse wrapping; the wrapping direction is opposite to that of the forward wrapping). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). Select **NO_WRAP**<br>when child elements need to be displayed in a single row or column, and **WRAP** or **WRAP_REVERSE** when automatic wrapping is required. The default value is **ARKUI_FLEX_WRAP_NO_WRAP** (no wrapping). When an invalid value is set, the default value is used.</li> <li>.value[2]?.i32: Alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END**<br>(alignment with the end edge), **SPACE_BETWEEN** (justified alignment; equal spacing between elements), **SPACE_AROUND** (circular alignment; equal spacing on both sides of each element), and **SPACE_EVENLY** (even alignment; equal spacing between elements and on both ends). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when a specific distribution of child elements on the main axis is required. The default value is **ARKUI_FLEX_ALIGNMENT_START**<br>(alignment with the start edge). When an invalid value is set, the default value is used.</li> <li>.value[3]?.i32: Alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END**<br>(alignment with the end edge), **STRETCH** (stretch to fill), and **BASELINE** (baseline alignment). For details about the mapping between enumerated values and numbers, see [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). Select the corresponding alignment mode when a specific alignment of child elements on the cross axis is required. The default value is **ARKUI_ITEM_ALIGNMENT_START** (alignment with the start edge). When an invalid value is set, the default value is used.</li> <li>.value[4]?.i32: Alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment; equal spacing between lines), **SPACE_AROUND** (circular alignment; equal spacing on both sides of each line), and **SPACE_EVENLY** (even alignment; equal spacing between lines and on both ends). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when the **Flex** container requires wrapping and the distribution of multiple lines on the cross axis needs to be controlled. The default value is **ARKUI_FLEX_ALIGNMENT_START** (alignment with the start edge). When an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). For details about the values and their meanings, see the parameter description.</li> <li>.value[1].i32: Wrapping rule. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). For details about the values and their meanings, see the parameter description.</li> <li>.value[2].i32: Alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description.</li> <li>.value[3].i32: Alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). For details about the values and their meanings, see the parameter description.</li> <li>.value[4].i32: Alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description.</li> </ul>

**Since**: 12

### NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE
```

**Description**

Spacing between the child components within the **Flex** container. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components along the main axis and cross axis directions needs to be controlled separately in a **Flex** container, such as when row spacing and column spacing in a grid layout need to be set independently. This addresses the issue where child components in a **Flex** container require different spacing in the main axis and cross axis, providing flexible bidirectional spacing control to achieve more refined layout effects and avoiding the need to set margins for each child component individually. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Spacing between the child components along the main axis of the **Flex** container, in vp. Default value: **0**. Value range: `[0, +∞)`. Set this parameter to add spacing between child elements along the main axis within the **Flex** container. The value **0** indicates no spacing. When an invalid value is set, the default value is used.</li> <li>.value[1].f32: Spacing between the child components along the cross axis of the **Flex** container, in vp. Default value: **0**. Value range: `[0, +∞)`. Set this parameter to add spacing between different rows along the cross axis when the **Flex** container requires wrapping. The value **0** indicates no spacing. When an invalid value is set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Spacing between the child components along the main axis of the **Flex** container, in vp.</li> <li>.value[1].f32: Spacing between the child components along the cross axis of the **Flex** container, in vp.</li> </ul>

**Since**: 23

### NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER
```

**Description**

Set the auxiliary line in the RelativeContainer container, supporting property setting, property reset and property acquisition interfaces. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Guideline in the **RelativeContainer** component. The parameter type is ArkUI_GuidelineOption. Set this parameter when a guideline needs to be defined in **RelativeContainer**<br>for locating child components relative to the guideline. No guideline is set when this parameter is not passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Guideline in the **RelativeContainer** component. The parameter type is ArkUI_GuidelineOption. If no guideline is set, **NULL** is returned.</li> </ul>

**Since**: 12

### NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER
```

**Description**

Barrier in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when barriers need to be created in a **RelativeContainer**<br>container to constrain the positions of child components, such as ensuring that a component is always positioned to the left or right of other components. This addresses the issue where dynamic constraint boundaries need to be created based on the positions of other components in a **RelativeContainer** container, providing barrier capabilities to implement more flexible relative layout constraints and meet complex UI layout requirements. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Barrier in the **RelativeContainer** component. The parameter type is ArkUI_BarrierOption. Set this parameter when a barrier needs to be defined in **RelativeContainer** to constrain the layout boundaries of child components. No barrier is set when this parameter is not passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Barrier in the **RelativeContainer** component. The parameter type is ArkUI_BarrierOption. When no barrier is set, **NULL** is returned.</li> </ul>

**Since**: 12


