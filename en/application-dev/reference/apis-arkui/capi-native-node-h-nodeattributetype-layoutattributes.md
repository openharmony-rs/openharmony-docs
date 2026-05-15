# ArkUI_NodeAttributeType (Layout Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW; @zju_ljz; @camlostshi-->
<!--Designer: @CCFFWW; @lanshouren-->
<!--Tester: @liuli0427; @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the layout attribute types that can be set by ArkUI on the native side, including size, size in percentage, paddings, margins, borders, positions, alignment, directions, constraints, Flex parameters, layout rules, and attributes related to layout components.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_WIDTH

```c
NODE_WIDTH = 0
```

Width attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

## NODE_HEIGHT

```c
NODE_HEIGHT = 1
```

Height attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

## NODE_PADDING

```c
NODE_PADDING = 4
```

Padding attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1: Specify the same padding for the four directions.<br>

| Name| Description|
| -- | -- |
| value[0].f32 | Padding, in vp.|

2: Specify different paddings for the four directions.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top padding, in vp. The default value is **0**.|
| .value[1].f32 | Right padding, in vp. The default value is **0**.|
| .value[2].f32 | Bottom padding, in vp. The default value is **0**.|
| .value[3].f32 | Left padding, in vp. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Top padding, in vp.|
| .value[1].f32 | Right padding, in vp.|
| .value[2].f32 | Bottom padding, in vp.|
| .value[3].f32 | Left padding, in vp.|

## NODE_MARGIN

```c
NODE_MARGIN = 7
```

Margin attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1: Specify the same margin for the four directions.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Margin, in vp.|

2: Specify different margins for the four directions.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top margin, in vp. The default value is **0**.|
| .value[1].f32 | Right margin, in vp. The default value is **0**.|
| .value[2].f32 | Bottom margin, in vp. The default value is **0**.|
| .value[3].f32 | Left margin, in vp. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Top margin, in vp.|
| .value[1].f32 | Right margin, in vp.|
| .value[2].f32 | Bottom margin, in vp.|
| .value[3].f32 | Left margin, in vp.|

## NODE_ALIGNMENT

```c
NODE_ALIGNMENT = 15
```

Alignment attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment method. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment).|

## NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH = 17
```

Border width attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1. Specify the same width for the four borders.<br>
| Name| Description|
| -- | -- |
| 1. .value[0].f32 | Width.|

2. Specify different width values for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the top border.|
| .value[1].f32 | Width of the right border.|
| .value[2].f32 | Width of the bottom border.|
| .value[3].f32 | Width of the left border.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the top border.|
| .value[1].f32 | Width of the right border.|
| .value[2].f32 | Width of the bottom border.|
| .value[3].f32 | Width of the left border.|

## NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS = 18
```

Border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1. Specify the same corner radius for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Corner radius.|

2. Specify different corner radii for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner.|
| .value[1].f32 | Radius of the upper right corner.|
| .value[2].f32 | Radius of the lower left corner.|
| .value[3].f32 | Radius of the lower right corner.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner.|
| .value[1].f32 | Radius of the upper right corner.|
| .value[2].f32 | Radius of the lower left corner.|
| .value[3].f32 | Radius of the lower right corner.|

## NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR = 19
```

Border color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1. Specify the same color for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].u32 | Border color, in 0xARGB format, for example, **0xFFFF11FF**.|

2. Specify different colors for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the top border, in 0xARGB format. The default value is **0xFF000000**.|
| .value[1].u32 | Color of the right border, in 0xARGB format. The default value is **0xFF000000**.|
| .value[2].u32 | Color of the bottom border, in 0xARGB format. The default value is **0xFF000000**.|
| .value[3].u32 | Color of the left border, in 0xARGB format. The default value is **0xFF000000**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the top border, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[1].u32 | Color of the right border, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[2].u32 | Color of the bottom border, in 0xARGB format, for example, **0xFFFF11FF**.|
| .value[3].u32 | Color of the left border, in 0xARGB format, for example, **0xFFFF11FF**.|

## NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE = 20
```

Border line style attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

1. Specify the same line style for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Border line style. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|

2. Specify different line styles for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[1].i32 | Line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[2].i32 | Line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[3].i32 | Line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line style of the top border.|
| .value[1].i32 | Line style of the right border.|
| .value[2].i32 | Line style of the bottom border.|
| .value[3].i32 | Line style of the left border.|

## NODE_POSITION

```c
NODE_POSITION = 27
```

Offset of the component's upper left corner relative to the parent container's. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate.|
| .value[1].f32 | Y-coordinate.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate.|
| .value[1].f32 | Y-coordinate.|

## NODE_DIRECTION

```c
NODE_DIRECTION = 47
```

Direction of the main axis. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Direction of the main axis. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction of the main axis. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction).|

## NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE = 48
```

Size constraints. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum width, in vp.|
| .value[1].f32 | Maximum width, in vp.|
| .value[2].f32 | Minimum height, in vp.|
| .value[3].f32 | Maximum height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum width, in vp.|
| .value[1].f32 | Maximum width, in vp.|
| .value[2].f32 | Minimum height, in vp.|
| .value[3].f32 | Maximum height, in vp.|

## NODE_OFFSET

```c
NODE_OFFSET = 54
```

Offset of the component's child relative to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Offset along the x-axis, in vp.|
| .value[1].f32 | Offset along the y-axis, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Offset along the x-axis, in vp.|
| .value[1].f32 | Offset along the y-axis, in vp.|

## NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR = 55
```

Anchor for locating the component's child. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the anchor, in vp.|
| .value[1].f32 | Y-coordinate of the anchor, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the anchor, in vp.|
| .value[1].f32 | Y-coordinate of the anchor, in vp.|

## NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES = 57
```

Alignment rules of the child components in the relative container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Alignment rules of the child components in the relative container. The parameter type is [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Alignment rules of the child components in the relative container. The parameter type is [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md).|

## NODE_ALIGN_SELF

```c
NODE_ALIGN_SELF = 58
```

Alignment mode of the child components along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the child components along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-native-type-h.md#arkui_itemalignment).|

## NODE_FLEX_GROW

```c
NODE_FLEX_GROW = 59
```

Percentage of the parent container's remaining space that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Percentage of the parent container's remaining space that is allocated to the component.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Percentage of the parent container's remaining space that is allocated to the component.|

## NODE_FLEX_SHRINK

```c
NODE_FLEX_SHRINK = 60
```

Percentage of the parent container's shrink size that is allocated to the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Percentage of the parent container's shrink size that is allocated to the current component.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Percentage of the parent container's shrink size that is allocated to the current component.|

## NODE_FLEX_BASIS

```c
NODE_FLEX_BASIS = 61
```

Base size of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Base size of the component on the main axis of the parent container.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Base size of the component on the main axis of the parent container.|

## NODE_ASPECT_RATIO

```c
NODE_ASPECT_RATIO = 67
```

Aspect ratio attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Aspect ratio of the component, in width/height format.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Aspect ratio of the component, in width/height format.|

## NODE_LAYOUT_WEIGHT

```c
NODE_LAYOUT_WEIGHT = 68
```

Weight of the component within the **Row**, **Column**, or **Flex** layout. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Weight of the component along the main axis.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Weight of the component along the main axis.|

## NODE_DISPLAY_PRIORITY

```c
NODE_DISPLAY_PRIORITY = 69
```

Display priority of the component within the **Row**, **Column**, or **Flex** (single-line) layout in the layout container. This attribute can be set, reset, and obtained as required through APIs.<br>
When the value of **displayPriority** is greater than 1, a larger value indicates a higher priority.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Display priority of the component in the layout container.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Display priority of the component in the layout container.|

## NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH = 70
```

Outline width of an element, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the left outline, in vp.|
| .value[1].f32 | Width of the top outline, in vp.|
| .value[2].f32 | Width of the right outline, in vp.|
| .value[3].f32 | Width of the bottom outline, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the left outline, in vp.|
| .value[1].f32 | Width of the top outline, in vp.|
| .value[2].f32 | Width of the right outline, in vp.|
| .value[3].f32 | Width of the bottom outline, in vp.|

## NODE_WIDTH_PERCENT

```c
NODE_WIDTH_PERCENT = 71
```

Width attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in percentage.|

## NODE_HEIGHT_PERCENT

```c
NODE_HEIGHT_PERCENT = 72
```

Height attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Height, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Height, in percentage.|

## NODE_PADDING_PERCENT

```c
NODE_PADDING_PERCENT = 73
```

Padding attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| 1. .value[0].f32 | Padding, which is the same for the four directions, in percentage.|
| 2. .value[0].f32 | Top padding, in percentage.|
| .value[1].f32 | Right padding, in percentage.|
| .value[2].f32 | Bottom padding, in percentage.|
| .value[3].f32 | Left padding, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Top padding, in percentage.|
| .value[1].f32 | Right padding, in percentage.|
| .value[2].f32 | Bottom padding, in percentage.|
| .value[3].f32 | Left padding, in percentage.|

## NODE_MARGIN_PERCENT

```c
NODE_MARGIN_PERCENT = 74
```

Margin attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| 1. .value[0].f32 | Margin, which is the same for the four directions, in percentage.|
| 2. .value[0].f32 | Top margin, in percentage.|
| .value[1].f32 | Right margin, in percentage.|
| .value[2].f32 | Bottom margin, in percentage.|
| .value[3].f32 | Left margin, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Top margin, in percentage.|
| .value[1].f32 | Right margin, in percentage.|
| .value[2].f32 | Bottom margin, in percentage.|
| .value[3].f32 | Left margin, in percentage.|

## NODE_RELATIVE_LAYOUT_CHAIN_MODE

```c
NODE_RELATIVE_LAYOUT_CHAIN_MODE = 76
```

Parameters of the chain in which the component is the head. This attribute can be set, reset, and obtained as required through APIs. This attribute has effect only when the parent container is **RelativeContainer**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Direction of the chain. The value is an enumerated value of [ArkUI_Axis](capi-native-type-h.md#arkui_axis).|
| .value[1].i32 | Style of the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction of the chain. The value is an enumerated value of [ArkUI_Axis](capi-native-type-h.md#arkui_axis).|
| .value[1].i32 | Style of the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-native-type-h.md#arkui_relativelayoutchainstyle).|

## NODE_SIZE

```c
NODE_SIZE = 79
```

Size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|
| .value[1].f32 | Height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|
| .value[1].f32 | Height, in vp.|

## NODE_LAYOUT_RECT

```c
NODE_LAYOUT_RECT = 83
```

Component size and position for layout. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the component, in px.|
| .value[1].i32 | Y-coordinate of the component, in px.|
| .value[2].i32 | Width of the component, in px.|
| .value[3].i32 | Height of the component, in px.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the component, in px.|
| .value[1].i32 | Y-coordinate of the component, in px.|
| .value[2].i32 | Width of the component, in px.|
| .value[3].i32 | Height of the component, in px.|

## NODE_BORDER_WIDTH_PERCENT

```c
NODE_BORDER_WIDTH_PERCENT = 85
```

Border width attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| 1. .value[0].f32 | Width, which is the same for the four borders, in percentage.|
| 2. .value[0].f32 | Width of the top border, in percentage.|
| .value[1].f32 | Width of the right border, in percentage.|
| .value[2].f32 | Width of the bottom border, in percentage.|
| .value[3].f32 | Width of the left border, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the top border, in percentage.|
| .value[1].f32 | Width of the right border, in percentage.|
| .value[2].f32 | Width of the bottom border, in percentage.|
| .value[3].f32 | Width of the left border, in percentage.|

## NODE_BORDER_RADIUS_PERCENT

```c
NODE_BORDER_RADIUS_PERCENT = 86
```

Border corner radius attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| 1. .value[0].f32 | Radius, which is the same for the four corners, in percentage.|
| 2. .value[0].f32 | Radius of the upper left corner, in percentage.|
| .value[1].f32 | Radius of the upper right corner, in percentage.|
| .value[2].f32 | Radius of the lower left corner, in percentage.|
| .value[3].f32 | Radius of the lower right corner, in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner, in percentage.|
| .value[1].f32 | Radius of the upper right corner, in percentage.|
| .value[2].f32 | Radius of the lower left corner, in percentage.|
| .value[3].f32 | Radius of the lower right corner, in percentage.|

## NODE_WIDTH_LAYOUTPOLICY

```c
NODE_WIDTH_LAYOUTPOLICY = 105
```

Width layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).|

## NODE_HEIGHT_LAYOUTPOLICY

```c
NODE_HEIGHT_LAYOUTPOLICY = 106
```

Height layout policy of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Layout policy. The parameter type is [ArkUI_LayoutPolicy](capi-native-type-h.md#arkui_layoutpolicy).|

## NODE_POSITION_EDGES

```c
NODE_POSITION_EDGES = 107
```

Position of the component relative to the edges of the container's content area. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| .object | Position of the component relative to the edges of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Position of the component relative to the edges of the container's content area. The parameter type is [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md).|

## NODE_CHAIN_WEIGHT

```c
NODE_CHAIN_WEIGHT = 118
```

Layout location of components that have formed a chain when the parent component is **RelativeContainer**. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Layout weight of the component in the horizontal direction. The default value is **0**. If an invalid value is set, the default value is used.|
| .value[1].f32 | Layout weight of the component in the vertical direction. The default value is **0**. If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Layout weight of the component in the horizontal direction.|
| .value[1].f32 | Layout weight of the component in the vertical direction.|

## NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

Safe area to be ignored when extending the layout of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Type for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-native-type-h.md#arkui_layoutsafeareatype). The default value is **ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM**. If an invalid value is set, the default value is used.|
| .value[1].u32 | Edge for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-native-type-h.md#arkui_layoutsafeareaedge). The default value is **ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL**. Example: **ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM**. If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Type for expanding the safe area.|
| .value[1].u32 | Edge for expanding the safe area.|

## NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

Length of the dashed line when the border style is set to dashed. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Length of the top border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[1].f32 | Length of the right border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[2].f32 | Length of the bottom border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[3].f32 | Length of the left border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Length of the top border, in vp.|
| .value[1].f32 | Length of the right border, in vp.|
| .value[2].f32 | Length of the bottom border, in vp.|
| .value[3].f32 | Length of the left border, in vp.|

## NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

Gap between dashes on the dashed line when the border style is set to dashed. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Gap between dashes on the top border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[1].f32 | Gap between dashes on the right border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[2].f32 | Gap between dashes on the bottom border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|
| .value[3].f32 | Gap between dashes on the left border, in vp. Value range: [0, +∞). If an abnormal value is set, the default dashed line effect is displayed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Gap between dashes on the top border, in vp.|
| .value[1].f32 | Gap between dashes on the right border, in vp.|
| .value[2].f32 | Gap between dashes on the bottom border, in vp.|
| .value[3].f32 | Gap between dashes on the left border, in vp.|

## NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

Alignment rule of the child components in the **Stack** container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment rule of the child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment). The default value is **ARKUI_ALIGNMENT_CENTER**. If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment rule of the child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-native-type-h.md#arkui_localizedalignment).|

## NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

Mode for drawing rounded corners of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Mode for drawing rounded corners of the component. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is **ARKUI_RENDERSTRATEGY_FAST**. If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Mode for drawing rounded corners of the component. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy).|
