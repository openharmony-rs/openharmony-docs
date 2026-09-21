# Layout

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_WIDTH

```c
NODE_WIDTH = 0
```

**Description**

Defines the width attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width, in vp.</li> </ul>

**Since**: 12

### NODE_HEIGHT

```c
NODE_HEIGHT
```

**Description**

Defines the height attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height, in vp.</li> </ul>

**Since**: 12

### NODE_PADDING

```c
NODE_PADDING
```

**Description**

Defines the padding attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions. <ul> <li>.value[0].f32: padding, in vp.</li> </ul> 2: Specify different paddings for different directions. <ul> <li>.value[0].f32: top padding, in vp.</li> <li>.value[1].f32: right padding, in vp.</li> <li>.value[2].f32: bottom padding, in vp.</li> <li>.value[3].f32: left padding, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top padding, in vp.</li> <li>.value[1].f32: right padding, in vp.</li> <li>.value[2].f32: bottom padding, in vp.</li> <li>.value[3].f32: left padding, in vp.</li> </ul>

**Since**: 12

### NODE_MARGIN

```c
NODE_MARGIN
```

**Description**

Defines the margin attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1. Specify the same margin for the four directions. <ul> <li>.value[0].f32: margin, in vp.</li> </ul> 2. Specify different margins for different directions. <ul> <li>.value[0].f32: top margin, in vp.</li> <li>.value[1].f32: right margin, in vp.</li> <li>.value[2].f32: bottom margin, in vp.</li> <li>.value[3].f32: left margin, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top margin, in vp.</li> <li>.value[1].f32: right margin, in vp.</li> <li>.value[2].f32: bottom margin, in vp.</li> <li>.value[3].f32: left margin, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGNMENT

```c
NODE_ALIGNMENT
```

**Description**

Sets the alignment attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is <b>ARKUI_ALIGNMENT_CENTER</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH
```

**Description**

Defines the border width attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same border for the four directions. <ul> <li>.value[0].f32: width of the four borders.</li> </ul> 2. Specify different borders for different directions. <ul> <li>.value[0].f32: width of the top border.</li> <li>.value[1].f32: width of the right border.</li> <li>.value[2].f32: width of the bottom border.</li> <li>.value[3].f32: width of the left border.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the top border.</li> <li>.value[1].f32: width of the right border.</li> <li>.value[2].f32: width of the bottom border.</li> <li>.value[3].f32: width of the left border.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS
```

**Description**

Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same radius for the four directions. <ul> <li>.value[0].f32: radius of the four corners.</li> </ul> 2. Specify different radius for different directions. <ul> <li>.value[0].f32: radius of the upper left corner.</li> <li>.value[1].f32: radius of the upper right corner.</li> <li>.value[2].f32: radius of the lower left corner.</li> <li>.value[3].f32: radius of the lower right corner.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: radius of the upper left corner.</li> <li>.value[1].f32: radius of the upper right corner.</li> <li>.value[2].f32: radius of the lower left corner.</li> <li>.value[3].f32: radius of the lower right corner.</li> </ul>

**Since**: 12

### NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR
```

**Description**

Defines the border color attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same color of the four borders. <ul> <li>.value[0].u32: color of the four borders, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul> 2. Specify different colors of the four borders. <ul> <li>.value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the top border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[1].u32: color of the right border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[2].u32: color of the lower border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> <li>.value[3].u32: color of the left border, in 0xARGB format, for example, <b>0xFFFF11FF</b>.</li> </ul>

**Since**: 12

### NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE
```

**Description**

Defines the border line style attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1. Specify the same line style of the four borders. <ul> <li>.value[0].i32: line style of the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> </ul> 2. Specify different line styles of the four borders. <ul> <li>.value[0].i32: line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[1].i32: line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[2].i32: line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> <li>.value[3].i32: line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is <b>ARKUI_BORDER_STYLE_SOLID</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: line style of the top border.</li> <li>.value[1].i32: line style of the right border.</li> <li>.value[2].i32: line style of the bottom border.</li> <li>.value[3].i32: line style of the left border.</li> </ul>

**Since**: 12

### NODE_POSITION

```c
NODE_POSITION
```

**Description**

Defines the offset attribute, which specifies the offset of the component's upper left corner relative to the parent container's. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X coordinate.</li> <li>.value[1].f32: Y coordinate.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X coordinate.</li> <li>.value[1].f32: Y coordinate.</li> </ul>

**Since**: 12

### NODE_DIRECTION

```c
NODE_DIRECTION
```

**Description**

Sets the direction of the main axis. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is <b>ARKUI_DIRECTION_AUTO</b>.</li> </ul>

**Since**: 12

### NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE
```

**Description**

Defines the size constraints. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul>

**Since**: 12

### NODE_OFFSET

```c
NODE_OFFSET
```

**Description**

Defines the offset of the component's child relative to the component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32 : offset along the x-axis, in vp.</li> <li>.value[1].f32 : offset along the y-axis, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32 : offset along the x-axis, in vp.</li> <li>.value[1].f32 : offset along the y-axis, in vp.</li> </ul>

**Since**: 12

### NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR
```

**Description**

Sets the anchor for locating the component's child. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: X coordinate of the anchor, in vp.</li> <li>.value[1].f32: Y coordinate of the anchor, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X coordinate of the anchor, in vp.</li> <li>.value[1].f32: Y coordinate of the anchor, in vp.</li> </ul>

**Since**: 12

### NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES
```

**Description**

Sets the alignment rules in the relative container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul><br><li>.object: Use the {@link ArkUI_AlignmentRuleOption} object as the component’s alignment rule.</li><br></ul><br>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Use the {@link ArkUI_AlignmentRuleOption} object as the component’s alignment rule.</li> </ul>

**Since**: 12

### NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF
```

**Description**

Sets the alignment mode of the child components along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_AUTO</b>.</li> </ul>

**Since**: 12

### NODE_FLEX_GROW

```c
NODE_FLEX_GROW
```

**Description**

Sets the percentage of the parent container's remaining space that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK
```

**Description**

Sets the percentage of the parent container's shrink size that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's shrink size that is allocated to the component.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's shrink size that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS
```

**Description**

Sets the base size of the component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: percentage of the parent container's remaining space that is allocated to the component.</li> </ul>

**Since**: 12

### NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO
```

**Description**

Defines the aspect ratio attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: aspect ratio of the component, in width/height format.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: aspect ratio of the component, in width/height format.</li> </ul>

**Since**: 12

### NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT
```

**Description**

Defines the weight of the component within its row, column, or flex container for proportional distribution of available space within the container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: weight of the component along the main axis.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: weight of the component along the main axis.</li> </ul>

**Since**: 12

### NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY
```

**Description**

Sets the display priority for the component in the row, column, or flex (single-line) container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: display priority of the component in the container.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: display priority of the component in the container.</li> </ul>

**Since**: 12

### NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT
```

**Description**

Defines the width attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width, in percentage.</li> </ul>

**Since**: 12

### NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT
```

**Description**

Defines the height attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height, in percentage.</li> </ul>

**Since**: 12

### NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT
```

**Description**

Defines the padding attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same padding for the four directions. <ul> <li>.value[0].f32: padding, in percentage.</li> </ul> 2: Specify different paddings for different directions. <ul> <li>.value[0].f32: top padding, in percentage.</li> <li>.value[1].f32: right padding, in percentage.</li> <li>.value[2].f32: bottom padding, in percentage.</li> <li>.value[3].f32: left padding, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top padding, in percentage.</li> <li>.value[1].f32: right padding, in percentage.</li> <li>.value[2].f32: bottom padding, in percentage.</li> <li>.value[3].f32: left padding, in percentage.</li> </ul>

**Since**: 12

### NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT
```

**Description**

Defines the margin attribute, which can be set, reset, and obtained as required through APIs.<br> **There are two formats of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for setting the attribute value:**<br>1: Specify the same margin for the four directions. <ul> <li>.value[0].f32: margin, in percentage.</li> </ul> 2: Specify different margins for different directions. <ul> <li>.value[0].f32: top margin, in percentage.</li> <li>.value[1].f32: right margin, in percentage.</li> <li>.value[2].f32: bottom margin, in percentage.</li> <li>.value[3].f32: left margin, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: top margin, in percentage.</li> <li>.value[1].f32: right margin, in percentage.</li> <li>.value[2].f32: bottom margin, in percentage.</li> <li>.value[3].f32: left margin, in percentage.</li> </ul>

**Since**: 12

### NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE
```

**Description**

specifies the parameters of the chain formed by this component as the chain head, and supports attribute setting, attribute reset and attribute acquisition interfaces.<br> Only takes effect when the parent container is RelativeContainer<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul><br><li>.value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li><br><li>.value[1].i32: Chain style. Enum {@link ArkUI_RelativeLayoutChainStyle}.</li><br><li>.value[0].i32: The direction of the chain. Enum [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li><br><li>.value[1].i32: Chain style. Enum {@link ArkUI_RelativeLayoutChainStyle}.</li> </ul>

**Since**: 12

### NODE_SIZE

```c
NODE_SIZE
```

**Description**

Set the height and width dimensions, support property setting, property reset and property acquisition interface.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Width value, unit is vp.</li> <li>.value[1].f32: Height value, unit is vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Width value, unit is vp.</li> <li>.value[1].f32: Height value, unit is vp.</li> </ul>

**Since**: 12

### NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT
```

**Description**

Defines the component size and position for layout. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: X coordinate of the component, in px.</li> <li>.value[1].i32: Y coordinate of the component, in px.</li> <li>.value[2].i32: width of the component, in px.</li> <li>.value[3].i32: height of the component, in px.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: X coordinate of the component, in px.</li> <li>.value[1].i32: Y coordinate of the component, in px.</li> <li>.value[2].i32: width of the component, in px.</li> <li>.value[3].i32: height of the component, in px.</li> </ul>

**Since**: 12

### NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

**Description**

Defines the border width attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: <ul> <li>.value[0].f32: width of the four borders, in percentage.</li> </ul> 2: <ul> <li>.value[0].f32: width of the top border, in percentage.</li> <li>.value[1].f32: width of the right border, in percentage.</li> <li>.value[2].f32: width of the bottom border, in percentage.</li> <li>.value[3].f32: width of the left border, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the top border, in percentage.</li> <li>.value[1].f32: width of the right border, in percentage.</li> <li>.value[2].f32: width of the bottom border, in percentage.</li> <li>.value[3].f32: width of the left border, in percentage.</li> </ul>

**Since**: 12

### NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

**Description**

Defines the border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br>1: <ul> <li>.value[0].f32: radius of the four corners, in percentage.</li> </ul> 2: <ul> <li>.value[0].f32: radius of the upper left corner, in percentage.</li> <li>.value[1].f32: radius of the upper right corner, in percentage.</li> <li>.value[2].f32: radius of the lower left corner, in percentage.</li> <li>.value[3].f32: radius of the lower right corner, in percentage.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: radius of the upper left corner, in percentage.</li> <li>.value[1].f32: radius of the upper right corner, in percentage.</li> <li>.value[2].f32: radius of the lower left corner, in percentage.</li> <li>.value[3].f32: radius of the lower right corner, in percentage.</li> </ul>

**Since**: 12

### NODE_EXPAND_SAFE_AREA

```c
NODE_EXPAND_SAFE_AREA = 92
```

**Description**

defines control components to extend their security zones, supporting property setting, property reset, and property fetching.<br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:**<br><ul> <li>.value[0]? .u32: Set of extended security zone enumerated values [ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype), For example, ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT.</li> <li>.value[1]? .u32: set of directional enum values for extended security zones [ArkUI_SafeAreaEdge](capi-layout-h.md#arkui_safeareaedge); For example: ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM.</li> </ul> **Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.value[0].u32: extends the security zone. .</li> <li>.value[1].u32: indicates the direction to extend the security zone. .</li> </ul>

**Since**: 12

### NODE_WIDTH_LAYOUTPOLICY

```c
NODE_WIDTH_LAYOUTPOLICY = 105
```

**Description**

Defines the width attribute with param type LayoutPolicy, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the LayoutPolicy that the width of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the LayoutPolicy that the width of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul>

**Since**: 21

### NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

**Description**

Defines the height attribute with param type LayoutPolicy, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the LayoutPolicy that the height of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the LayoutPolicy that the height of the component follows. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy).</li> </ul>

**Since**: 21

### NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

**Description**

Defines the position attribute in param type Edges, which specifies the position of the component by the distance relative to the parent container's four edges. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object indicates struct of edges for position. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).</li> </ul>

**Since**: 21

### NODE_PIXEL_ROUND

```c
NODE_PIXEL_ROUND = 109
```

**Description**

Defines the pixelRound attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object indicates struct of policy for pixelRound. The parameter type is [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md).</li> </ul>

**Since**: 21

### NODE_CHAIN_WEIGHT

```c
NODE_CHAIN_WEIGHT = 118
```

**Description**

Sets the weight of the component in a chain, which is used to re-lay out components that form the chain. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Horizontal ChainWeight.</li> <li>.value[1].f32: Vertical ChainWeight.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Horizontal ChainWeight.</li> <li>.value[1].f32: Vertical ChainWeight.</li> </ul>

**Since**: 23

### NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

**Description**

Expands the layout safe area of a component., supporting property setting, property reset, and property fetching.<br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:**<br><ul> <li>.value[0].u32: The region type to expand the component's layout safe area into. The default value is LayoutSafeAreaType.SYSTEM. [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype), For example, ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM.</li> <li>.value[1].u32: The set of edges for which to ignore layout safe area. The default value is LayoutSafeAreaEdge.ALL. [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge); For example: ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_START.</li> </ul> **Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.value[0].u32: The region type to expand the component's layout safe area into.</li> <li>.value[1].u32: The set of edges for which to ignore layout safe area.</li> </ul>

**Since**: 23

### NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

**Description**

Defines the length of dash when BorderStyle is dashed, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The length of dash on the top border.</li> <li>.value[1].f32: The length of dash on the right border.</li> <li>.value[2].f32: The length of dash on the bottom border.</li> <li>.value[3].f32: The length of dash on the left border.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The length of dash on the top border.</li> <li>.value[1].f32: The length of dash on the right border.</li> <li>.value[2].f32: The length of dash on the bottom border.</li> <li>.value[3].f32: The length of dash on the left border.</li> </ul>

**Since**: 23

### NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

**Description**

Defines the gap of dash when BorderStyle is dashed, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The gap of dash on the top border.</li> <li>.value[1].f32: The gap of dash on the right border.</li> <li>.value[2].f32: The gap of dash on the bottom border.</li> <li>.value[3].f32: The gap of dash on the left border.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The gap of dash on the top border.</li> <li>.value[1].f32: The gap of dash on the right border.</li> <li>.value[2].f32: The gap of dash on the bottom border.</li> <li>.value[3].f32: The gap of dash on the left border.</li> </ul>

**Since**: 23

### NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

**Description**

Defines the align rules of child component in Stack container, which can be set, reset, and obtained as required through APIs. The default value is <b>ARKUI_LOCALIZED_ALIGNMENT_CENTER</b>.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: LocalizedAlignment mode. The data type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment).</li> </ul>

**Since**: 23

### NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

**Description**

Defines the render types for drawing rounded corners when the radius of the border rounded corners is set, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is <b>ARKUI_RENDERSTRATEGY_FAST</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Render types for drawing rounded corners. The data type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).</li> </ul>

**Since**: 23

### NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK
```

**Description**

Defines the alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is <b>ARKUI_ALIGNMENT_CENTER</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The data type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).</li> </ul>

**Since**: 12

### NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN
```

**Description**

Defines the horizontal alignment mode of child components in the column. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). Default value: <b>ARKUI_HORIZONTAL_ALIGNMENT_CENTER</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment).</li> </ul>

**Since**: 12

### NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT
```

**Description**

Defines the vertical alignment mode of child components in the column. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).</li> </ul>

**Since**: 12

### NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE
```

**Description**

Defines Row constructor options or Column constructor options used for settting the spacing of child components, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: The space of child components, in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: The space of child components, in vp.</li> </ul>

**Since**: 23

### NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE
```

**Description**

Defines whether the arrangement of child components along the main axis in a Column or Row is reversed, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The value that determines whether the arrangement of child components along the main axis is reversed.</li> </ul>

**Since**: 23

### NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW
```

**Description**

Defines the vertical alignment mode of child components in the row. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). Default value: <b>ARKUI_VERTICAL_ALIGNMENT_CENTER</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment).</li> </ul>

**Since**: 12

### NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT
```

**Description**

Defines the horizontal alignment mode of child components in the row. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Default value: <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).</li> </ul>

**Since**: 12

### NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX
```

**Description**

Defines the flex attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.i32: direction in which flex items are arranged. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). The default value is <b>ARKUI_FLEX_DIRECTION_ROW</b>.</li> <li>.value[1]?.i32: how the flex items are wrapped. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). The default value is <b>ARKUI_FLEX_WRAP_NO_WRAP</b>.</li> <li>.value[2]?.i32: alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> <li>.value[3]?.i32: alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is <b>ARKUI_ITEM_ALIGNMENT_START</b>.</li> <li>.value[4]?.i32: alignment mode along the cross axis for multi-line content. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is <b>ARKUI_FLEX_ALIGNMENT_START</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: direction in which flex items are arranged.</li> <li>.value[1].i32: how the flex items are wrapped.</li> <li>.value[2].i32: alignment mode along the main axis.</li> <li>.value[3].i32: alignment mode along the cross axis.</li> <li>.value[4].i32: alignment mode along the cross axis for multi-line content.</li> </ul>

**Since**: 12

### NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE
```

**Description**

Defines Row constructor options used for settting the spacing of child components, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Space on the main axis of the flex container., in vp.</li> <li>.value[1].f32: Space on the cross axis of a flex container., in vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Space on the main axis of the flex container., in vp.</li> <li>.value[1].f32: Space on the cross axis of a flex container., in vp.</li> </ul>

**Since**: 23

### NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER
```

**Description**

Set the auxiliary line in the RelativeContainer container, supporting property setting, property reset and property acquisition interfaces.<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Auxiliary lines within the RelativeContainer container:.</li> </ul> **Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Auxiliary lines within the RelativeContainer container:.</li> </ul>

**Since**: 12

### NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER
```

**Description**

Sets the barrier within the RelativeContainer container and supports property setting, property reset and property acquisition interfaces.<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Barrier within the RelativeContainer container:.</li> </ul> **Attribute acquisition method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Barrier within the RelativeContainer container:.</li> </ul>

**Since**: 12


