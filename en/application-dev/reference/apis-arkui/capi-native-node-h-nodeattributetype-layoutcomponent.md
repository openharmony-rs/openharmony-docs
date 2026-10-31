# ArkUI_NodeAttributeType (Layout Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-25T02:19:27.939Z pushedAt=2026-08-26T08:00:20.503Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for layout components, including **Stack**, **Column**, **Row**, **Flex**, and **RelativeContainer**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK = 1000000
```

Alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs. If this attribute and the universal attribute **NODE_ALIGNMENT** (which indicates the alignment mode of child components within the container) are both set, whichever is set later takes effect. This attribute is used when the alignment position of child components in a **Stack** container needs to be controlled, such as center, top-left, or bottom-right alignment. This addresses the issue where the default alignment mode of child components in the **Stack** container does not meet requirements, providing flexible child component alignment control to satisfy various layout needs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The value options are as follows: **TOP** (top alignment), **BOTTOM** (bottom alignment), **LEFT** (left alignment), **RIGHT** (right alignment), **TOP_START** (top-left alignment), **TOP_END** (top-right alignment), **BOTTOM_START** (bottom-left alignment), **BOTTOM_END** (bottom-right alignment), **CENTER** (center alignment), **START** (alignment with the start edge), and **END** (alignment with the end edge). For the mapping between enumerated values and numbers, see [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). Select the corresponding alignment mode when a child component needs to be aligned at a specific position within the container. The default value is **ARKUI_ALIGNMENT_CENTER** (center alignment). When an invalid value is set, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). For details about the values and their meanings, see the parameter description. |

## NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN = 1006000
```

Horizontal alignment mode of child components in the **Column** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the horizontal alignment mode of child components in a **Column** container needs to be controlled, such as left alignment, center alignment, or right alignment. This addresses the issue where the default horizontal alignment mode of child components in a **Column** container does not meet requirements, providing flexible horizontal alignment control for child components to satisfy various vertical layout scenarios.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). The value options are as follows: **START** (alignment with the start edge), CENTER (center alignment), and END (alignment with the end edge). For the mapping between enumerated values and numbers, see [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). Select the corresponding alignment mode when child components need to be aligned at a specific horizontal position within a **Column** container. The default value is **ARKUI_HORIZONTAL_ALIGNMENT_CENTER** (center alignment). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). For details about the options and their meanings, see the parameter description. |

## NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT = 1006001
```

Vertical alignment mode of child components in the Column component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the vertical alignment mode of child components in a **Column** container needs to be controlled, such as top alignment, bottom alignment, center alignment, or justified alignment. This addresses the issue where the default vertical alignment mode of child components in a **Column** container does not meet requirements, providing flexible vertical alignment control for child components to achieve diverse vertical layout effects.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment), **SPACE_AROUND** (circular alignment), and **SPACE_EVENLY** (even alignment). For the mapping between enumerated values and numbers, see the definition of [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when a specific distribution of child elements in the **Column** container in the vertical direction is needed. The default value is **ARKUI_FLEX_ALIGNMENT_START** (alignment with the start edge). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description. |

## NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE = 1006002
```

Spacing between the child components of **Column** or **Row**. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components in a **Column** or **Row** container needs to be controlled, such as the spacing between card list items or between buttons. This addresses the issue where the spacing between child components in a **Column** or **Row** container needs to be uniformly controlled, providing a convenient way to set spacing between child components and avoiding the need to set margins for each child component individually, thereby simplifying development.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp. Default value: **0**.<br>Value range: `[0, +∞)`. Set this parameter when spacing is needed between child components of a **Column** or **Row** container. Setting it to **0** means no spacing.<br>When an invalid value is set, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp. |

## NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE = 1006003
```

Whether the child components along the main axis in **Column** or **Row** are arranged reversely. This attribute can be set, reset, and obtained through APIs. This attribute is used when the arrangement order of child components in a **Column** or **Row** container needs to be reversed, such as a chat message list (with the latest message at the bottom) or displaying list items in reverse order. This addresses the issue where child components in a **Column** or **Row** container need to be arranged in reverse, enabling a reversed arrangement effect without changing the data source order, thereby simplifying development logic.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the child components along the main axis are arranged reversely. Default value: **0** (false). When the value is a non-zero integer, the child components are arranged in reverse order along the main axis (applicable to right-to-left or bottom-to-top layout requirements). When the value is 0, the child components are arranged in normal order along the main axis (applicable to general layout). Set this parameter to a non-zero value when a reverse arrangement effect is needed (such as displaying a list in reverse order); otherwise, set it to **0**.<br>When an invalid value is set, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the child components along the main axis are arranged reversely. A non-zero value indicates reverse arrangement, and **0** indicates normal order. |

## NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW = 1007000
```

Vertical alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the vertical alignment mode of child components in a **Row** container needs to be controlled, such as top alignment, center alignment, or bottom alignment. This addresses the issue where the default vertical alignment mode of child components in a **Row** container does not meet requirements, providing flexible vertical alignment control for child components to satisfy various horizontal layout scenarios.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). The value options are as follows: **TOP** (top alignment), **CENTER** (center alignment), and **BOTTOM** (bottom alignment). For the mapping between enumerated values and numbers, see [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). Select the corresponding alignment mode when the child component needs to be aligned at a specific vertical position within the **Row** container. The default value is **ARKUI_VERTICAL_ALIGNMENT_CENTER** (center alignment). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). For details about the values and their meanings, see the parameter description. |

## NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT = 1007001
```

Horizontal alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the horizontal alignment mode of child components in a **Row** container needs to be controlled, such as left alignment, right alignment, center distribution, or justified alignment. This addresses the issue where the default horizontal alignment mode of child components in a **Row** container does not meet requirements, providing flexible horizontal alignment control for child components to achieve diverse horizontal layout effects.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment), **SPACE_AROUND** (circular alignment), and **SPACE_EVENLY** (even alignment). For the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when child elements need a specific distribution along the horizontal axis within a **Row** container. The default value is **ARKUI_FLEX_ALIGNMENT_START** (start alignment). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description. |

## NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX = 1008000
```

**Flex** attribute, which can be set, reset, and obtained as required through APIs. This attribute is used when the arrangement direction, wrapping mode, and alignment mode of child components in a **Flex** container need to be flexibly configured, such as in complex layout scenarios like responsive layouts and adaptive layouts. This addresses the issue where a **Flex** container needs to have multiple layout parameters configured uniformly, enabling multiple layout parameters of a **Flex** container to be set in a single call, thereby simplifying the development process and improving code maintainability.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 5.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.i32 | Direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). The value options are as follows: **ROW** (horizontal, from left to right), **ROW_REVERSE** (horizontal, from right to left), **COLUMN** (vertical, from top to bottom), and **COLUMN_REVERSE** (vertical, from bottom to top). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). Select **ROW** or **ROW_REVERSE** when a horizontal layout is implemented, and **COLUMN** or **COLUMN_REVERSE** when a vertical layout is implemented. The default value is **ARKUI_FLEX_DIRECTION_ROW** (horizontal, from left to right). When an invalid value is set, the default value is used. |
| .value[1]?.i32 | Wrapping rule. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). The value options are as follows: **NO_WRAP** (no wrapping; child elements are compressed when they exceed the container boundary), **WRAP** (forward wrapping; child elements automatically wrap when they exceed the container boundary), and **WRAP_REVERSE** (reverse wrapping; the wrapping direction is opposite to that of the forward wrapping). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). Select **NO_WRAP** when child elements need to be displayed in a single row or column, and **WRAP** or **WRAP_REVERSE** when automatic wrapping is required. The default value is **ARKUI_FLEX_WRAP_NO_WRAP** (no wrapping). When an invalid value is set, the default value is used. |
| .value[2]?.i32 | Alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment; equal spacing between elements), **SPACE_AROUND** (circular alignment; equal spacing on both sides of each element), and **SPACE_EVENLY** (even alignment; equal spacing between elements and on both ends). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when a specific distribution of child elements on the main axis is required. The default value is **ARKUI_FLEX_ALIGNMENT_START** (alignment with the start edge). When an invalid value is set, the default value is used. |
| .value[3]?.i32 | Alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **STRETCH** (stretch to fill), and **BASELINE** (baseline alignment). For details about the mapping between enumerated values and numbers, see [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). Select the corresponding alignment mode when a specific alignment of child elements on the cross axis is required. The default value is **ARKUI_ITEM_ALIGNMENT_START** (alignment with the start edge). When an invalid value is set, the default value is used. |
| .value[4]?.i32 | Alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The value options are as follows: **START** (alignment with the start edge), **CENTER** (center alignment), **END** (alignment with the end edge), **SPACE_BETWEEN** (justified alignment; equal spacing between lines), **SPACE_AROUND** (circular alignment; equal spacing on both sides of each line), and **SPACE_EVENLY** (even alignment; equal spacing between lines and on both ends). For details about the mapping between enumerated values and numbers, see [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). Select the corresponding alignment mode when the **Flex** container requires wrapping and the distribution of multiple lines on the cross axis needs to be controlled. The default value is **ARKUI_FLEX_ALIGNMENT_START** (alignment with the start edge). When an invalid value is set, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). For details about the values and their meanings, see the parameter description. |
| .value[1].i32 | Wrapping rule. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). For details about the values and their meanings, see the parameter description. |
| .value[2].i32 | Alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description. |
| .value[3].i32 | Alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). For details about the values and their meanings, see the parameter description. |
| .value[4].i32 | Alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). For details about the values and their meanings, see the parameter description. |

## NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE = 1008001
```

Spacing between the child components within the **Flex** container. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when the spacing between child components along the main axis and cross axis directions needs to be controlled separately in a **Flex** container, such as when row spacing and column spacing in a grid layout need to be set independently. This addresses the issue where child components in a **Flex** container require different spacing in the main axis and cross axis, providing flexible bidirectional spacing control to achieve more refined layout effects and avoiding the need to set margins for each child component individually.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value ArkUI_AttributeItem are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid, and the actual returned **value** array length is always 2.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Spacing between the child components along the main axis of the **Flex** container, in vp. Default value: **0**.<br>Value range: `[0, +∞)`. Set this parameter to add spacing between child elements along the main axis within the **Flex** container. The value **0** indicates no spacing.<br>When an invalid value is set, the default value is used. |
| .value[1].f32 | Spacing between the child components along the cross axis of the **Flex** container, in vp. Default value: **0**.<br>Value range: `[0, +∞)`. Set this parameter to add spacing between different rows along the cross axis when the **Flex** container requires wrapping. The value **0** indicates no spacing.<br>When an invalid value is set, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between the child components along the main axis of the **Flex** container, in vp. |
| .value[1].f32 | Spacing between the child components along the cross axis of the **Flex** container, in vp. |

## NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER = 1012000
```

Guideline in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when child components in **RelativeContainer** need to be aligned based on guidelines, such as creating horizontal or vertical reference lines for child component locating. This addresses the issue where child components in a **RelativeContainer** container need to be precisely located based on specific reference lines, providing guideline capabilities to simplify the alignment logic in **RelativeContainer** layouts and improve layout precision and maintainability.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Guideline in the **RelativeContainer** component. The parameter type is [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md). Set this parameter when a guideline needs to be defined in **RelativeContainer** for locating child components relative to the guideline. No guideline is set when this parameter is not passed. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Guideline in the **RelativeContainer** component. The parameter type is [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md). If no guideline is set, **NULL** is returned. |

## NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER = 1012001
```

Barrier in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when barriers need to be created in a **RelativeContainer** container to constrain the positions of child components, such as ensuring that a component is always positioned to the left or right of other components. This addresses the issue where dynamic constraint boundaries need to be created based on the positions of other components in a **RelativeContainer** container, providing barrier capabilities to implement more flexible relative layout constraints and meet complex UI layout requirements.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Barrier in the **RelativeContainer** component. The parameter type is [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md). Set this parameter when a barrier needs to be defined in **RelativeContainer** to constrain the layout boundaries of child components. No barrier is set when this parameter is not passed. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Barrier in the **RelativeContainer** component. The parameter type is [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md). When no barrier is set, **NULL** is returned. |