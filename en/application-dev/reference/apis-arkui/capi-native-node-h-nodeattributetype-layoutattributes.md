# ArkUI_NodeAttributeType (Layout Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3; @zju_ljz; @camlostshi-->
<!--Designer: @hehongyang3; @fenglinbailu-->
<!--Tester: @liuli0427; @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=6cf262681c9e0cd9c697d71c12de487ae14f710a translatedAt=2026-08-25T02:19:51.256Z pushedAt=2026-08-26T07:59:06.463Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the layout attribute types that can be set by ArkUI on the native side, including size, size in percentage, paddings, margins, borders, positions, alignment, directions, constraints, Flex parameters, layout rules, and attributes related to layout components. It is applicable to scenarios requiring fine-grained component layout control, responsive layout adaptation, and complex layout on the native side. With these attributes, you can flexibly control the position, size, and alignment of components, solving layout issues such as component positioning, size adaptation, and alignment adjustment, thereby improving layout efficiency and flexibility.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_WIDTH

```c
NODE_WIDTH = 0
```

Width attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp. Value range: [0, +∞). When an invalid value is set, the default value is used for display or the component size is abnormal. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

## NODE_HEIGHT

```c
NODE_HEIGHT = 1
```

Height attribute, which can be (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Height, in vp. Value range: [0, +∞). When an invalid value is set, the default value is displayed or the component size is abnormal. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

## NODE_PADDING

```c
NODE_PADDING = 4
```

Padding attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same padding for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Padding for the four directions (top, bottom, left, and right), in vp. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |

2: Specify different padding values for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used. |
| .value[1].f32 | Right padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used. |
| .value[2].f32 | Bottom padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used. |
| .value[3].f32 | Left padding, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used. |

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

Margin attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same margin for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Margin for the four directions (top, bottom, left, and right), in vp. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |

2: Specify different margins for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |
| .value[1].f32 | Right margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |
| .value[2].f32 | Bottom margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |
| .value[3].f32 | Left margin, in vp. The default value is **0vp**. Value range: [0, +∞). When an invalid value is set, the default value **0vp** is used for display. |

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

Alignment attribute for component content in the element drawing area, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). |

## NODE_BORDER_WIDTH

```c
NODE_BORDER_WIDTH = 17
```

Border width attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same width for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Width for the four borders, in vp. Value range: [0, +∞). The default value is **0vp**. |

2: Specify different width values for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the top border, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[1].f32 | Width of the right border, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[2].f32 | Width of the bottom border, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[3].f32 | Width of the left border, in vp. The default value is **0vp**. Value range: [0, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the top border, in vp. |
| .value[1].f32 | Width of the right border, in vp. |
| .value[2].f32 | Width of the bottom border, in vp. |
| .value[3].f32 | Width of the left border, in vp. |

## NODE_BORDER_RADIUS

```c
NODE_BORDER_RADIUS = 18
```

Border corner radius attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1. Specify the same corner radius for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Corner radius for the four borders, in vp. Value range: [0, +∞). The default value is **0vp**. |

2. Four parameters are passed, indicating respectively setting the border radius for each of the four corners.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[1].f32 | Radius of the upper right corner, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[2].f32 | Radius of the lower left corner, in vp. The default value is **0vp**. Value range: [0, +∞). |
| .value[3].f32 | Radius of the lower right corner, in vp. The default value is **0vp**. Value range: [0, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner, in vp. |
| .value[1].f32 | Radius of the upper right corner, in vp. |
| .value[2].f32 | Radius of the lower left corner, in vp. |
| .value[3].f32 | Radius of the lower right corner, in vp. |

## NODE_BORDER_COLOR

```c
NODE_BORDER_COLOR = 19
```

Border color attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same color for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].u32 | Color for the four borders, in 0xARGB format, for example, `0xFFFF11FF`. |

2: Specify different colors for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the top border, in 0xARGB format. The default value is `0xFF000000`. |
| .value[1].u32 | Color of the right border, in 0xARGB format. The default value is `0xFF000000`. |
| .value[2].u32 | Color of the bottom border, in 0xARGB format. The default value is `0xFF000000`. |
| .value[3].u32 | Color of the left border, in 0xARGB format. The default value is `0xFF000000`. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the top border, in 0xARGB format, for example, `0xFFFF11FF`. |
| .value[1].u32 | Color of the right border, in 0xARGB format, for example, `0xFFFF11FF`. |
| .value[2].u32 | Color of the bottom border, in 0xARGB format, for example, `0xFFFF11FF`. |
| .value[3].u32 | Color of the left border, in 0xARGB format, for example, `0xFFFF11FF`. |

## NODE_BORDER_STYLE

```c
NODE_BORDER_STYLE = 20
```

Border line style attribute, which can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same line style for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Line style for the four borders. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|

2: Specify different line styles for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].i32 | Line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[1].i32 | Line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[2].i32 | Line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|
| .value[3].i32 | Line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). The default value is **ARKUI_BORDER_STYLE_SOLID**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line style of the top border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). |
| .value[1].i32 | Line style of the right border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). |
| .value[2].i32 | Line style of the bottom border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). |
| .value[3].i32 | Line style of the left border. The parameter type is [ArkUI_BorderStyle](capi-native-type-h.md#arkui_borderstyle). |

## NODE_POSITION

```c
NODE_POSITION = 27
```

Offset of the component's upper left corner relative to the parent container's. This attribute can be set (through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)), reset (through [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)), and obtained (through [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)) as required.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate, in vp. Value range: (-∞, +∞). |
| .value[1].f32 | Y-coordinate, in vp. Value range: (-∞, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate, in vp. |
| .value[1].f32 | Y-coordinate, in vp. |

## NODE_DIRECTION

```c
NODE_DIRECTION = 47
```

Direction of the main axis within the container element. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Direction of the main axis, which is used to set the arrangement direction of child components in the container. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction of the main axis. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). |

## NODE_CONSTRAINT_SIZE

```c
NODE_CONSTRAINT_SIZE = 48
```

Size constraint attribute, used to restricts the size range during component layout. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum width, in vp. Value range: [0, +∞). Default value: **0**. |
| .value[1].f32 | Maximum width, in vp. Value range: [0, +∞). Default value: no limit. |
| .value[2].f32 | Minimum height, in vp. Value range: [0, +∞). Default value: **0**. |
| .value[3].f32 | Maximum height, in vp. Value range: [0, +∞). Default value: no limit. |

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

Additional offset of a component's child element relative to the component itself. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Offset along the x-axis, in vp. Value range: (-∞, +∞). Default value: **0**. |
| .value[1].f32 | Offset along the y-axis, in vp. Value range: (-∞, +∞). Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-axis offset relative to the component itself, in vp. |
| .value[1].f32 | Y-axis offset relative to the component itself, in vp. |

## NODE_MARK_ANCHOR

```c
NODE_MARK_ANCHOR = 55
```

Anchor of a component's child element during locating. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the anchor, in vp. Value range: (-∞, +∞). Default value: **0**. |
| .value[1].f32 | Y-coordinate of the anchor, in vp. Value range: (-∞, +∞). Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate of the anchor in the component's coordinate system, in vp. |
| .value[1].f32 | Y-coordinate of the anchor in the component's coordinate system, in vp. |

## NODE_ALIGN_RULES

```c
NODE_ALIGN_RULES = 57
```

Alignment rules of the child components in the relative container. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br>
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

Alignment mode of the child component along the cross axis of the parent container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the child component along the cross axis of the parent container, used to change the position of the child component along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_AUTO**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the child component along the cross axis of the parent container. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). |

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
| .value[0].f32 | Percentage of the parent container's remaining space that is allocated to the component. Value range: [0, +∞). Default value: **0**. |

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
| .value[0].f32 | Percentage of the parent container's shrink size that is allocated to the current component. Value range: [0, +∞). Default value: **1**. |

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
| .value[0].f32 | Base size of the component on the main axis of the parent container, in vp. Value range: [0, +∞). Default value: **auto**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Base size of the component on the main axis of the parent container, in vp. |

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
| .value[0].f32 | Aspect ratio of the component, in width/height format. Value range: (0, +∞). Default value: no aspect ratio constraint is set. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Aspect ratio of the component, in width/height format. After being set, the component adjusts its size based on this ratio. |

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
| .value[0].u32 | Layout weight of the component along the main axis, which determines the allocation ratio of the component in the remaining space. Value range: [0, +∞). Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Layout weight of the component along the main axis, which determines the allocation ratio of the component in the remaining space. |

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
| .value[0].u32 | Display priority of the component in the layout container. Value range: [0, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Display priority of the component in the layout container. A larger value indicates a higher priority. When space is insufficient, components with higher priority are displayed first. |

## NODE_OUTLINE_WIDTH

```c
NODE_OUTLINE_WIDTH = 70
```

Width of the outline of an element. The outline is not involved in component layout calculation and does not affect the component size. It is different from the border width. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the left outline, in vp. Value range: [0, +∞). Default value: **0**. |
| .value[1].f32 | Width of the top outline, in vp. Value range: [0, +∞). Default value: **0**. |
| .value[2].f32 | Width of the right outline, in vp. Value range: [0, +∞). Default value: **0**. |
| .value[3].f32 | Width of the bottom outline, in vp. Value range: [0, +∞). Default value: **0**. |

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
| .value[0].f32 | Width, in percentage. Value range: (0, +∞). There is no default value. When not set, the size is determined by the component layout, using the width required by the child component's own content. When an invalid value is set, an error code is returned. |

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
| .value[0].f32 | Height, in percentage. Value range: (0, +∞). There is no default value. When not set, the size is determined by the component layout, using the height required by the child component's own content. When an invalid value is set, an error code is returned. |

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
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same padding for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Padding for the four directions, in percentage. The default value is **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |

2: Specify different padding values for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[1].f32 | Right padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[2].f32 | Bottom padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[3].f32 | Left padding, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |

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
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same margin for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Margin for the four directions, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |

2: Specify different margins for the four directions (top, bottom, left, and right).<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Top margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[1].f32 | Right margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[2].f32 | Bottom margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[3].f32 | Left margin, in percentage. Default value: **0**. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |

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

Parameters of the chain in which the component is the head, used to control the distribution of multiple child components along the main axis or cross axis within a RelativeContainer. It is commonly used to implement scenarios where multiple components are evenly distributed along the same direction and maintain fixed spacing or alignment mode. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when the parent container is a RelativeContainer.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Direction of the chain, used to set whether the chain is arranged horizontally or vertically. The value is an enumerated value of [ArkUI_Axis](capi-layout-h.md#arkui_axis). |
| .value[1].i32 | Style of the chain, used to set the distribution mode of components within the chain. The value is an enumerated value of [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction of the chain. The parameter type is [ArkUI_Axis](capi-layout-h.md#arkui_axis). |
| .value[1].i32 | Style of the chain. The parameter type is [ArkUI_RelativeLayoutChainStyle](capi-layout-h.md#arkui_relativelayoutchainstyle). |

## NODE_SIZE

```c
NODE_SIZE = 79
```

Size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp. Value range: [0, +∞). |
| .value[1].f32 | Height, in vp. Value range: [0, +∞). |

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
| .value[0].i32 | X-coordinate of the component, in px. Value range: (-∞, +∞). |
| .value[1].i32 | Y-coordinate of the component, in px. Value range: (-∞, +∞). |
| .value[2].i32 | Width of the component, in px. Value range: [0, +∞). |
| .value[3].i32 | Height of the component, in px. Value range: [0, +∞). |

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
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1: Specify the same width for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Width for the four borders, in percentage. Value range: [0, +∞). Default value: **0**. |

2: Specify different width values for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the top border, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[1].f32 | Width of the right border, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[2].f32 | Width of the bottom border, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[3].f32 | Width of the left border, in percentage. Value range: [0, +∞). Default value: **0**. |

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
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 12

**Parameters**

One or four parameters can be passed:

1. Specify the same corner radius for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Corner radius for the four borders, in percentage. Value range: [0, +∞). Default value: **0**. |

2. Specify different corner radii for the four borders.<br>

| Name| Description|
| -- | -- |
| .value[0].f32 | Radius of the upper left corner, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[1].f32 | Radius of the upper right corner, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[2].f32 | Radius of the lower left corner, in percentage. Value range: [0, +∞). Default value: **0**. |
| .value[3].f32 | Radius of the lower right corner, in percentage. Value range: [0, +∞). Default value: **0**. |

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
| .value[0].i32 | Width layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Width layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used. |

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
| .value[0].i32 | Height layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Height layout policy of the component. The parameter type is [ArkUI_LayoutPolicy](capi-layout-h.md#arkui_layoutpolicy). Default value: **ARKUI_LAYOUT_POLICY_WRAP_CONTENT**. When an invalid value is set, the default value is used for display. |

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

Layout location of components that have formed a chain when the parent component is a RelativeContainer. This attribute is used to control the proportion of space occupied by each component in the chain along the chain direction, commonly applied to scenarios where components in the same chain are allocated remaining space by weight ratio. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Layout weight of the component in the horizontal direction. Default value: **0**. A larger weight value indicates a larger proportion of space the component occupies in the chain. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |
| .value[1].f32 | Layout weight of the component in the vertical direction. Default value: **0**. A larger weight value indicates a larger proportion of space the component occupies in the chain. Value range: [0, +∞). When an invalid value is set, the default value is used for display. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Layout weight of the component in the horizontal direction. A larger weight value indicates a larger proportion of space the component occupies in the chain. |
| .value[1].f32 | Layout weight of the component in the vertical direction. A larger weight value indicates a larger proportion of space the component occupies in the chain. |

## NODE_IGNORE_LAYOUT_SAFE_AREA

```c
NODE_IGNORE_LAYOUT_SAFE_AREA = 119
```

Safe area to be ignored when expanding the layout of the component, allowing components to extend into system UI areas such as the system status bar and navigation bar. This attribute is commonly used in scenarios requiring full-screen display, such as immersive video playback, full-screen games, and image viewers. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Type of the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype). The default value is **ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM**. If an invalid value is set, the default value is used.|
| .value[1].u32 | Edges for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge). The default value is **ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL**. Example: **ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM**. If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Type of the safe area. The parameter type is [ArkUI_LayoutSafeAreaType](capi-layout-h.md#arkui_layoutsafeareatype). |
| .value[1].u32 | Edges for expanding the safe area. The parameter type is [ArkUI_LayoutSafeAreaEdge](capi-layout-h.md#arkui_layoutsafeareaedge). |

## NODE_DASH_WIDTH

```c
NODE_DASH_WIDTH = 120
```

Length of the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH** attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Length of the dashed line on the top border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[1].f32 | Length of the dashed line on the right border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[2].f32 | Length of the dashed line on the bottom border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[3].f32 | Length of the dashed line on the left border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Length of the dashed line on the top border, in vp.|
| .value[1].f32 | Length of the dashed line on the right border, in vp.|
| .value[2].f32 | Length of the dashed line on the bottom border, in vp.|
| .value[3].f32 | Length of the dashed line on the left border, in vp.|

## NODE_DASH_GAP

```c
NODE_DASH_GAP = 121
```

Gap between dashes on the dashed line when the border style is set to dashed (**ArkUI_BorderStyle** is set to **ARKUI_BORDER_STYLE_DASHED**). The default value is the border width value of the **NODE_BORDER_WIDTH** attribute. This attribute takes effect only when the border style is dashed. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 4.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Gap between dashes on the dash line of the top border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[1].f32 | Gap between dashes on the dash line of the right border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[2].f32 | Gap between dashes on the dash line of the bottom border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |
| .value[3].f32 | Gap between dashes on the dash line of the left border, in vp. Value range: [0, +∞). Default value: the border width value of the **NODE_BORDER_WIDTH** attribute. When an invalid value is set, the default dashed line effect is displayed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Gap between dashes on the dash line of the top border, in vp.|
| .value[1].f32 | Gap between dashes on the dash line of the right border, in vp.|
| .value[2].f32 | Gap between dashes on the dash line of the bottom border, in vp.|
| .value[3].f32 | Gap between dashes on the dash line of the left border, in vp.|

## NODE_LAYOUT_GRAVITY

```c
NODE_LAYOUT_GRAVITY = 122
```

Alignment rule of the child components in the **Stack** container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment rule of the child components in the **Stack** container, determining the position of child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment). The default value is **ARKUI_ALIGNMENT_CENTER**. When an invalid value is set, the default value is used for display. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment rule of the child components in the **Stack** container. The parameter type is [ArkUI_LocalizedAlignment](capi-layout-h.md#arkui_localizedalignment). |

## NODE_BORDER_RADIUS_TYPE

```c
NODE_BORDER_RADIUS_TYPE = 123
```

Mode for drawing rounded corners of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Mode for rendering rounded corners of the component, which affects the rendering effect and performance of rounded corners. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). The default value is **ARKUI_RENDERSTRATEGY_FAST**. In FAST mode, rounded corners are directly clipped, prioritizing rendering performance. In OFFSCREEN mode, offscreen rendering is used to optimize the rounded corner effect, which may affect performance. When an invalid value is set, the default value is used for display. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Mode for rendering rounded corners of the component. The parameter type is [ArkUI_RenderStrategy](capi-native-type-h.md#arkui_renderstrategy). |

## NODE_ACCESSIBILITY_NEXT_FOCUS_ID

```c
NODE_ACCESSIBILITY_NEXT_FOCUS_ID = 124
```

[NODE_ID](capi-native-node-h-nodeattributetype-base.md#node_id) of the next focus component for accessibility of this component. After the node ID of the component is set, the accessibility service searches for the component whose node ID is the same as that of the next focus component on the current page. If no such component exists, the setting is invalid. This attribute can be set, reset, and obtained as required through APIs.

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .string | Node ID of the next focus component for accessibility.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Node ID of the next focus component for accessibility.|

## NODE_ACCESSIBILITY_DEFAULT_FOCUS

```c
NODE_ACCESSIBILITY_DEFAULT_FOCUS = 125
```

Default focus flag for accessibility to find the default focus component. This attribute can be set, reset, and obtained as required through APIs.

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Default accessibility focus. The value can be **0** or **1**. The value **1** indicates that the component is defined as the default focus in the accessibility service, and **0** indicates that the component is not defined as the default focus in the accessibility service. When other values are passed, the default value **0** is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Default accessibility focus. The value can be **0** or **1**. The value **1** indicates that the component is defined as the default focus in the accessibility service, and **0** indicates that the component is not defined as the default focus in the accessibility service. When other values are passed, the default value **0** is used. |