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

Width attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width, in vp, used to set the component width.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width, in vp.</li> </ul>

**Since**: 12

### NODE_HEIGHT

```c
NODE_HEIGHT
```

**Description**

Height attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height, in vp, used to set the height of the component. Negative values are not supported.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height, in vp.</li> </ul>

**Since**: 12

### NODE_PADDING

```c
NODE_PADDING
```

**Description**

Padding attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions. <ul> <li>.value[0].f32: padding, in vp.</li> </ul> 2: Specify different paddings for different directions. <ul> <li>.value[0].f32: top padding, in vp.</li> <li>.value[1].f32: right padding, in vp.</li> <li>.value[2].f32: bottom padding, in vp.</li> <li>.value[3].f32: left padding, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top padding, in vp.</li> <li>.value[1].f32: right padding, in vp.</li> <li>.value[2].f32: bottom padding, in vp.</li> <li>.value[3].f32: left padding, in vp.</li> </ul>

**Since**: 12

### NODE_MARGIN

```c
NODE_MARGIN
```

**Description**

Margin attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1. Specify the same margin for the four directions. <ul> <li>.value[0].f32: margin, in vp.</li> </ul> 2. Specify different margins for different directions. <ul> <li>.value[0].f32: top margin, in vp.</li> <li>.value[1].f32: right margin, in vp.</li> <li>.value[2].f32: bottom margin, in vp.</li> <li>.value[3].f32: left margin, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top margin, in vp.</li> <li>.value[1].f32: right margin, in vp.</li> <li>.value[2].f32: bottom margin, in vp.</li> <li>.value[3].f32: left margin, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGNMENT

```c
NODE_ALIGNMENT
```

**Description**

Alignment attribute for component content in the element drawing area, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is <b>ARKUI_ALIGNMENT_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH
```

**Description**

Border width attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same border for the four directions. <ul> <li>.value[0].f32: width of the four borders.</li> </ul> 2. Specify different borders for different directions. <ul> <li>.value[0].f32: width of the top border.</li> <li>.value[1].f32: width of the right border.</li> <li>.value[2].f32: width of the bottom border.</li> <li>.value[3].f32: width of the left border.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the top border.</li> <li>.value[1].f32: width of the right border.</li> <li>.value[2].f32: width of the bottom border.</li> <li>.value[3].f32: width of the left border.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS
```

**Description**

Border corner radius attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same radius for the four directions. <ul> <li>.value[0].f32: radius of the four corners.</li> </ul> 2. Specify different radius for different directions. <ul> <li>.value[0].f32: radius of the upper left corner.</li> <li>.value[1].f32: radius of the upper right corner.</li> <li>.value[2].f32: radius of the lower left corner.</li> <li>.value[3].f32: radius of the lower right corner.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: radius of the upper left corner.</li> <li>.value[1].f32: radius of the upper right corner.</li> <li>.value[2].f32: radius of the lower left corner.</li> <li>.value[3].f32: radius of the lower right corner.</li> </ul>

**Since**: 12

### NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR
```

**Description**

Border color attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same color of the four borders. <ul> <li>.value[0].u32: color of the four borders, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul> 2. Specify different colors of the four borders. <ul> <li>.value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul>

**Since**: 12

### NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE
```

**Description**

Border line style attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same line style of the four borders. <ul> <li>.value[0].i32: line style of the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> </ul> 2. Specify different line styles of the four borders. <ul> <li>.value[0].i32: line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[1].i32: line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[2].i32: line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[3].i32: line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: line style of the top border.</li> <li>.value[1].i32: line style of the right border.</li> <li>.value[2].i32: line style of the bottom border.</li> <li>.value[3].i32: line style of the left border.</li> </ul>

**Since**: 12

### NODE_POSITION

```c
NODE_POSITION
```

**Description**

Offset of the component's upper left corner relative to the parent container's. This attribute can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X coordinate.</li> <li>.value[1].f32: Y coordinate.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X coordinate.</li> <li>.value[1].f32: Y coordinate.</li> </ul>

**Since**: 12

### NODE_DIRECTION

```c
NODE_DIRECTION
```

**Description**

Direction of the main axis within the container element. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>.</li> </ul>

**Since**: 12

### NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE
```

**Description**

Size constraint attribute, used to restricts the size range during component layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul>

**Since**: 12

### NODE_OFFSET

```c
NODE_OFFSET
```

**Description**

Additional offset of a component's child element relative to the component itself. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32 : offset along the x-axis, in vp.</li> <li>.value[1].f32 : offset along the y-axis, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32 : offset along the x-axis, in vp.</li> <li>.value[1].f32 : offset along the y-axis, in vp.</li> </ul>

**Since**: 12

### NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR
```

**Description**

Anchor of a component's child element during locating. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X coordinate of the anchor, in vp.</li> <li>.value[1].f32: Y coordinate of the anchor, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X coordinate of the anchor, in vp.</li> <li>.value[1].f32: Y coordinate of the anchor, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES
```

**Description**

Alignment rules of the child components in the relative container. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Use the ArkUI_AlignmentRuleOption object as the component’s alignment rule.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Use the ArkUI_AlignmentRuleOption object as the component’s alignment rule.</li> </ul>

**Since**: 12

### NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF
```

**Description**

Alignment mode of the child component along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>.</li> </ul>

**Since**: 12

### NODE_FLEX_GROW

```c
NODE_FLEX_GROW
```

**Description**

Percentage of the parent container's remaining space that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK
```

**Description**

Percentage of the parent container's shrink size that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's shrink size that is allocated to the component.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's shrink size that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS
```

**Description**

Base size of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO
```

**Description**

Aspect ratio attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: aspect ratio of the component, in width/height format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: aspect ratio of the component, in width/height format.</li> </ul>

**Since**: 12

### NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT
```

**Description**

Weight of the component within the **Row**, **Column**, or **Flex** layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: weight of the component along the main axis.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: weight of the component along the main axis.</li> </ul>

**Since**: 12

### NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY
```

**Description**

Display priority of the component within the **Row**, **Column**, or **Flex** (single-line) layout in the layout container. This attribute can be set, reset, and obtained as required through APIs.<br> When the value of **displayPriority** is greater than 1, a larger value indicates a higher priority.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: display priority of the component in the container.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: display priority of the component in the container.</li> </ul>

**Since**: 12

### NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT
```

**Description**

Width attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width, in percentage.</li> </ul>

**Since**: 12

### NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT
```

**Description**

Height attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height, in percentage.</li> </ul>

**Since**: 12

### NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT
```

**Description**

Padding attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions. <ul> <li>.value[0].f32: padding, in percentage.</li> </ul> 2: Specify different paddings for different directions. <ul> <li>.value[0].f32: top padding, in percentage.</li> <li>.value[1].f32: right padding, in percentage.</li> <li>.value[2].f32: bottom padding, in percentage.</li> <li>.value[3].f32: left padding, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top padding, in percentage.</li> <li>.value[1].f32: right padding, in percentage.</li> <li>.value[2].f32: bottom padding, in percentage.</li> <li>.value[3].f32: left padding, in percentage.</li> </ul>

**Since**: 12

### NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT
```

**Description**

Margin attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same margin for the four directions. <ul> <li>.value[0].f32: margin, in percentage.</li> </ul> 2: Specify different margins for different directions. <ul> <li>.value[0].f32: top margin, in percentage.</li> <li>.value[1].f32: right margin, in percentage.</li> <li>.value[2].f32: bottom margin, in percentage.</li> <li>.value[3].f32: left margin, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top margin, in percentage.</li> <li>.value[1].f32: right margin, in percentage.</li> <li>.value[2].f32: bottom margin, in percentage.</li> <li>.value[3].f32: left margin, in percentage.</li> </ul>

**Since**: 12

### NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE
```

**Description**

Parameters of the chain in which the component is the head, used to control the distribution of multiple child components along the main axis or cross axis within a RelativeContainer. It is commonly used to implement scenarios where multiple components are evenly distributed along the same direction and maintain fixed spacing or alignment mode. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li> <li>.value[1].i32: Chain style. Enum [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle).</li> <li>.value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li> <li>.value[1].i32: Chain style. Enum [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle).</li> </ul>

**Since**: 12

### NODE_SIZE

```c
NODE_SIZE
```

**Description**

Size attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Width value, unit is vp.</li> <li>.value[1].f32: Height value, unit is vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width value, unit is vp.</li> <li>.value[1].f32: Height value, unit is vp.</li> </ul>

**Since**: 12

### NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT
```

**Description**

Component size and position for layout. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: X coordinate of the component, in px.</li> <li>.value[1].i32: Y coordinate of the component, in px.</li> <li>.value[2].i32: width of the component, in px.</li> <li>.value[3].i32: height of the component, in px.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: X coordinate of the component, in px.</li> <li>.value[1].i32: Y coordinate of the component, in px.</li> <li>.value[2].i32: width of the component, in px.</li> <li>.value[3].i32: height of the component, in px.</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

**Description**

Border width attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: <ul> <li>.value[0].f32: width of the four borders, in percentage.</li> </ul> 2: <ul> <li>.value[0].f32: width of the top border, in percentage.</li> <li>.value[1].f32: width of the right border, in percentage.</li> <li>.value[2].f32: width of the bottom border, in percentage.</li> <li>.value[3].f32: width of the left border, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the top border, in percentage.</li> <li>.value[1].f32: width of the right border, in percentage.</li> <li>.value[2].f32: width of the bottom border, in percentage.</li> <li>.value[3].f32: width of the left border, in percentage.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

**Description**

Border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: <ul> <li>.value[0].f32: radius of the four corners, in percentage.</li> </ul> 2: <ul> <li>.value[0].f32: radius of the upper left corner, in percentage.</li> <li>.value[1].f32: radius of the upper right corner, in percentage.</li> <li>.value[2].f32: radius of the lower left corner, in percentage.</li> <li>.value[3].f32: radius of the lower right corner, in percentage.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: radius of the upper left corner, in percentage.</li> <li>.value[1].f32: radius of the upper right corner, in percentage.</li> <li>.value[2].f32: radius of the lower left corner, in percentage.</li> <li>.value[3].f32: radius of the lower right corner, in percentage.</li> </ul>

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

Width layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the LayoutPolicy that the width of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the LayoutPolicy that the width of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul>

**Since**: 21

### NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

**Description**

Height layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the LayoutPolicy that the height of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the LayoutPolicy that the height of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul>

**Since**: 21

### NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

**Description**

Position of the component relative to the edges of the container's content area. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul>

**Since**: 21

### NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

**Description**

Pixel rounding policy of the component, used to avoid issues such as visual aliasing when the component is rendered at a scaled size or non-integer-pixel position. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul>

**Since**: 21

### NODE_CHAIN_WEIGHT

```c
NODE_CHAIN_WEIGHT = 118
```

**Description**

Layout location of components that have formed a chain when the parent component is a RelativeContainer. This attribute is used to control the proportion of space occupied by each component in the chain along the chain direction, commonly applied to scenarios where components in the same chain are allocated remaining space by weight ratio. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Horizontal ChainWeight.</li> <li>.value[1].f32: Vertical ChainWeight.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Horizontal ChainWeight.</li> <li>.value[1].f32: Vertical ChainWeight.</li> </ul>

**Since**: 23

### NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

**Description**

Safe area to be ignored when expanding the layout of the component, allowing components to extend into system UI areas such as the system status bar and navigation bar. This attribute is commonly used in scenarios requiring full-screen display, such as immersive video playback, full-screen games, and image viewers. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br><br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:**<br><ul> <li>.value[0].u32: The region type to expand the component's layout safe area into. The default value is LayoutSafeAreaType.SYSTEM. [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype), For example, ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM.</li> <li>.value[1].u32: The set of edges for which to ignore layout safe area. The default value is LayoutSafeAreaEdge.ALL. [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge); For example: ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_START.</li> </ul><br> **Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.value[0].u32: The region type to expand the component's layout safe area into.</li> <li>.value[1].u32: The set of edges for which to ignore layout safe area.</li> </ul>

**Since**: 23

### NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

**Description**

Length of the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH**<br>attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The length of dash on the top border.</li> <li>.value[1].f32: The length of dash on the right border.</li> <li>.value[2].f32: The length of dash on the bottom border.</li> <li>.value[3].f32: The length of dash on the left border.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The length of dash on the top border.</li> <li>.value[1].f32: The length of dash on the right border.</li> <li>.value[2].f32: The length of dash on the bottom border.</li> <li>.value[3].f32: The length of dash on the left border.</li> </ul>

**Since**: 23

### NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

**Description**

Gap between dashes on the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH**<br>attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The gap of dash on the top border.</li> <li>.value[1].f32: The gap of dash on the right border.</li> <li>.value[2].f32: The gap of dash on the bottom border.</li> <li>.value[3].f32: The gap of dash on the left border.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The gap of dash on the top border.</li> <li>.value[1].f32: The gap of dash on the right border.</li> <li>.value[2].f32: The gap of dash on the bottom border.</li> <li>.value[3].f32: The gap of dash on the left border.</li> </ul>

**Since**: 23

### NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

**Description**

Alignment rule of the child components in the **Stack** container. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment).</li> </ul>

**Since**: 23

### NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

**Description**

Mode for drawing rounded corners of the component. This attribute can be set, reset, and obtained as required through APIs.<br> The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is <b>ARKUI_RENDERSTRATEGY_FAST</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).</li> </ul>

**Since**: 23

### NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK
```

**Description**

Defines the alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is <b>ARKUI_ALIGNMENT_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).</li> </ul>

**Since**: 12

### NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN
```

**Description**

Defines the horizontal alignment mode of child components in the column. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). Default value: <b>ARKUI_HORIZONTAL_ALIGNMENT_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment).</li> </ul>

**Since**: 12

### NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT
```

**Description**

Vertical alignment mode of child components in the Column component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the vertical alignment mode of child components in a **Column** container needs to be controlled, such as top alignment, bottom alignment, center alignment, or justified alignment. This addresses the issue where the default vertical alignment mode of child components in a **Column** container does not meet requirements, providing flexible vertical alignment control for child components to achieve diverse vertical layout effects.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).</li> </ul>

**Since**: 12

### NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE
```

**Description**

Spacing between the child components of **Column** or **Row**. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components in a **Column** or **Row** container needs to be controlled, such as the spacing between card list items or between buttons. This addresses the issue where the spacing between child components in a **Column** or **Row** container needs to be uniformly controlled, providing a convenient way to set spacing between child components and avoiding the need to set margins for each child component individually, thereby simplifying development.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The space of child components, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The space of child components, in vp.</li> </ul>

**Since**: 23

### NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE
```

**Description**

Whether the child components along the main axis in **Column** or **Row** are arranged reversely. This attribute can be set, reset, and obtained through APIs. This attribute is used when the arrangement order of child components in a **Column** or **Row** container needs to be reversed, such as a chat message list (with the latest message at the bottom) or displaying list items in reverse order. This addresses the issue where child components in a **Column** or **Row** container need to be arranged in reverse, enabling a reversed arrangement effect without changing the data source order, thereby simplifying development logic.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.</li> </ul>

**Since**: 23

### NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW
```

**Description**

Defines the vertical alignment mode of child components in the row. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). Default value: <b>ARKUI_VERTICAL_ALIGNMENT_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment).</li> </ul>

**Since**: 12

### NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT
```

**Description**

Horizontal alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the horizontal alignment mode of child components in a **Row** container needs to be controlled, such as left alignment, right alignment, center distribution, or justified alignment. This addresses the issue where the default horizontal alignment mode of child components in a **Row** container does not meet requirements, providing flexible horizontal alignment control for child components to achieve diverse horizontal layout effects.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).</li> </ul>

**Since**: 12

### NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX
```

**Description**

Defines the flex attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.i32: direction in which flex items are arranged. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). The default value is <b>ARKUI_FLEX_DIRECTION_ROW</b>.</li> <li>.value[1]?.i32: how the flex items are wrapped. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). The default value is <b>ARKUI_FLEX_WRAP_NO_WRAP</b>.</li> <li>.value[2]?.i32: alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> <li>.value[3]?.i32: alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_START</b>.</li> <li>.value[4]?.i32: alignment mode along the cross axis for multi-line content. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: direction in which flex items are arranged.</li> <li>.value[1].i32: how the flex items are wrapped.</li> <li>.value[2].i32: alignment mode along the main axis.</li> <li>.value[3].i32: alignment mode along the cross axis.</li> <li>.value[4].i32: alignment mode along the cross axis for multi-line content.</li> </ul>

**Since**: 12

### NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE
```

**Description**

Spacing between the child components within the **Flex** container. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components along the main axis and cross axis directions needs to be controlled separately in a **Flex** container, such as when row spacing and column spacing in a grid layout need to be set independently. This addresses the issue where child components in a **Flex** container require different spacing in the main axis and cross axis, providing flexible bidirectional spacing control to achieve more refined layout effects and avoiding the need to set margins for each child component individually.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Space on the main axis of the flex container., in vp.</li> <li>.value[1].f32: Space on the cross axis of a flex container., in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Space on the main axis of the flex container., in vp.</li> <li>.value[1].f32: Space on the cross axis of a flex container., in vp.</li> </ul>

**Since**: 23

### NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER
```

**Description**

Set the auxiliary line in the RelativeContainer container, supporting property setting, property reset and property acquisition interfaces.<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Auxiliary lines within the RelativeContainer container:.</li> </ul><br> **Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Auxiliary lines within the RelativeContainer container:.</li> </ul>

**Since**: 12

### NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER
```

**Description**

Barrier in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when barriers need to be created in a **RelativeContainer**<br>container to constrain the positions of child components, such as ensuring that a component is always positioned to the left or right of other components. This addresses the issue where dynamic constraint boundaries need to be created based on the positions of other components in a **RelativeContainer** container, providing barrier capabilities to implement more flexible relative layout constraints and meet complex UI layout requirements.<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Barrier within the RelativeContainer container:.</li> </ul><br> **Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Barrier within the RelativeContainer container:.</li> </ul>

**Since**: 12


