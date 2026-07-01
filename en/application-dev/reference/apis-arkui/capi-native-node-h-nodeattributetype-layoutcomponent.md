# ArkUI_NodeAttributeType (Layout Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for layout components.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_STACK_ALIGN_CONTENT

```c
NODE_STACK_ALIGN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_STACK = 1000000
```

Alignment mode of the child components in the container. This attribute can be set, reset, and obtained as required through APIs. If this attribute and the universal attribute **NODE_ALIGNMENT** are both set, whichever is set later takes effect.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).|

## NODE_COLUMN_ALIGN_ITEMS

```c
NODE_COLUMN_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_COLUMN = 1006000
```

Horizontal alignment mode of child components in the **Column** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment). The default value is **ARKUI_HORIZONTAL_ALIGNMENT_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment).|

## NODE_COLUMN_JUSTIFY_CONTENT

```c
NODE_COLUMN_JUSTIFY_CONTENT = 1006001
```

Vertical alignment mode of child components in the **Column** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).|

## NODE_LINEAR_LAYOUT_SPACE

```c
NODE_LINEAR_LAYOUT_SPACE = 1006002
```

Spacing between the child components of **Column** or **Row**. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp. The default value is **0**.<br>Value range: [0, +∞).<br>If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp.|

## NODE_LINEAR_LAYOUT_REVERSE

```c
NODE_LINEAR_LAYOUT_REVERSE = 1006003
```

Whether the child components along the main axis in **Column** or **Row** are arranged reversely. This attribute can be set, reset, and obtained through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the child components along the main axis are arranged reversely. The default value is **false**. If the value is **true**, the child components are arranged reversely along the main axis. If the value is **false**, the child components are arranged in normal order along the main axis.<br>If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the child components along the main axis are arranged reversely.|

## NODE_ROW_ALIGN_ITEMS

```c
NODE_ROW_ALIGN_ITEMS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ROW = 1007000
```

Vertical alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment). The default value is **ARKUI_VERTICAL_ALIGNMENT_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the child components. The parameter type is [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment).|

## NODE_ROW_JUSTIFY_CONTENT

```c
NODE_ROW_JUSTIFY_CONTENT = 1007001
```

Horizontal alignment mode of child components in the **Row** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the child components. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment).|

## NODE_FLEX_OPTION

```c
NODE_FLEX_OPTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_FLEX = 1008000
```

**Flex** attributes, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.i32 | Direction in which child components are arranged within the **Flex** container. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection). The default value is **ARKUI_FLEX_DIRECTION_ROW**.|
| .value[1]?.i32 | Arrangement rule. The parameter type is [ArkUI_FlexWrap](capi-layout-h.md#arkui_flexwrap). The default value is **ARKUI_FLEX_WRAP_NO_WRAP**.|
| .value[2]?.i32 | Alignment mode along the main axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.|
| .value[3]?.i32 | Alignment mode along the cross axis. The parameter type is [ArkUI_ItemAlignment](capi-layout-h.md#arkui_itemalignment). The default value is **ARKUI_ITEM_ALIGNMENT_START**.|
| .value[4]?.i32 | Alignment mode for multi-line content when there is extra space in the cross axis. The parameter type is [ArkUI_FlexAlignment](capi-layout-h.md#arkui_flexalignment). The default value is **ARKUI_FLEX_ALIGNMENT_START**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Direction in which child components are arranged within the **Flex** container.|
| .value[1].i32 | Wrapping rule.|
| .value[2].i32 | Alignment mode along the main axis.|
| .value[3].i32 | Alignment mode along the cross axis.|
| .value[4].i32 | Alignment mode for multi-line content when there is extra space in the cross axis.|

## NODE_FLEX_SPACE

```c
NODE_FLEX_SPACE = 1008001
```

Spacing between the child components within the **Flex** container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
**size** in the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is invalid.<br>

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Spacing between the child components along the main axis of the **Flex** container, in vp. The default value is **0**.<br>Value range: [0, +∞).<br>If an invalid value is set, the default value is used.|
| .value[1].f32 | Spacing between the child components along the cross axis of the **Flex** container, in vp. The default value is **0**.<br>Value range: [0, +∞).<br>If an invalid value is set, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between the child components along the main axis of the **Flex** container, in vp.|
| .value[1].f32 | Spacing between the child components along the cross axis of the **Flex** container, in vp.|

## NODE_RELATIVE_CONTAINER_GUIDE_LINE

```c
NODE_RELATIVE_CONTAINER_GUIDE_LINE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RELATIVE_CONTAINER = 1012000
```

Guideline in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Guideline in the **RelativeContainer** component. The parameter type is [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Guideline in the **RelativeContainer** component. The parameter type is [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md).|

## NODE_RELATIVE_CONTAINER_BARRIER

```c
NODE_RELATIVE_CONTAINER_BARRIER = 1012001
```

Barrier in the **RelativeContainer** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Barrier in the **RelativeContainer** component. The parameter type is [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Barrier in the **RelativeContainer** component. The parameter type is [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md).|
