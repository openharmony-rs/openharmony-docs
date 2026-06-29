# ArkUI_NodeAttributeType (Interaction Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3; @zju_ljz-->
<!--Designer: @hehongyang3; @lanshouren-->
<!--Tester: @liuli0427; @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for interaction, including touch testing, response hot zone, focus control, safe zone extension, visible area listening, and focus movement.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_HIT_TEST_BEHAVIOR

```c
NODE_HIT_TEST_BEHAVIOR = 26
```

Hit test behavior attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Hit test mode. The parameter type is [ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode). The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Hit test mode. The parameter type is [ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode). The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.|

## NODE_DEFAULT_FOCUS

```c
NODE_DEFAULT_FOCUS = 40
```

Default focus attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the focus is the default one. The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the focus is the default one. The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.|

## NODE_RESPONSE_REGION

```c
NODE_RESPONSE_REGION = 41
```

Touch target attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

> **NOTE**
> During configuration, the data array can contain any number of values (all will be accepted), but only the first 20 values can be retrieved.

**Parameters**

| Name| Description|
| -- | -- |
| .data[0].f32 | X coordinate of the touch point relative to the upper left corner of the component, in vp.|
| .data[1].f32 | Y coordinate of the touch point relative to the upper left corner of the component, in vp.|
| .data[2].f32 | Width of the touch target, in percentage.|
| .data[3].f32 | Height of the touch target, in percentage.|
| .data[4...].f32 | Multiple touch targets that can be set. The sequence of the parameters is the same as the preceding.|

**Returns**

| Type| Description|
| -- | -- |
| .data[0].f32 | X coordinate of the touch point relative to the upper left corner of the component, in vp.|
| .data[1].f32 | Y coordinate of the touch point relative to the upper left corner of the component, in vp.|
| .data[2].f32 | Width of the touch target, in percentage.|
| .data[3].f32 | Height of the touch target, in percentage.|
| .data[4...].f32 | Multiple touch targets that can be set. The sequence of the parameters is the same as the preceding.|

## NODE_OVERLAY

```c
NODE_OVERLAY = 42
```

Overlay attribute, which can be set, reset, and obtained as required through APIs. You can set the overlay content through **.string** or **.object**, with **.string** having higher priority.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .string | Overlay text.|
| .value[0]?.i32 | Position of the overlay relative to the component. This parameter is optional. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.|
| .value[1]?.f32 | Offset of the overlay relative to the upper left corner of itself on the x-axis, in vp. This parameter is optional. The default value is **0** vp.|
| .value[2]?.f32 | Offset of the overlay relative to the upper left corner of itself on the y-axis, in vp. This parameter is optional. The default value is **0** vp.|
| .value[3]?.i32 | Layout direction of the overlay. This parameter is optional. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**.<br>In most scenarios, this parameter should be set to **Auto**, which allows the system to automatically handle the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **LTR** (left-to-right) or **RTL** (right-to-left). It is supported since API version 21.|
| .object | Node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). The default value is **nullptr**. It is supported since API version 21.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Overlay text.|
| .value[0].i32 | Position of the overlay relative to the component. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.|
| .value[1].f32 | Offset of the overlay relative to the upper left corner of itself on the x-axis, in vp.|
| .value[2].f32 | Offset of the overlay relative to the upper left corner of itself on the y-axis, in vp.|
| .value[3].i32 | Layout direction of the overlay. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**. It is supported since API version 21.|
| .object | Node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md). It is supported since API version 21.|

## NODE_FOCUS_STATUS

```c
NODE_FOCUS_STATUS = 66
```

Component focus status. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

> **NOTE**
> Setting the parameter to **0** shifts focus from the currently focused component on the current level of the page to the root container.

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Component focus status. The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Component focus status. The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.|

## NODE_FOCUS_ON_TOUCH

```c
NODE_FOCUS_ON_TOUCH = 84
```

Whether the component is focusable on touch. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.|

## NODE_EXPAND_SAFE_AREA

```c
NODE_EXPAND_SAFE_AREA = 92
```

Safe area to be expanded to. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.u32 | Types of the expanded safe area, which are enumerated values of [ArkUI_SafeAreaType](capi-native-type-h.md#arkui_safeareatype). Example: **ARKUI_SAFE_AREA_TYPE_SYSTEM \| ARKUI_SAFE_AREA_TYPE_CUTOUT**.|
| .value[1]?.u32 | Edges for expanding the safe area, which are enumerated values of [ArkUI_SafeAreaEdge](capi-native-type-h.md#arkui_safeareaedge). Example: **ARKUI_SAFE_AREA_EDGE_TOP \| ARKUI_SAFE_AREA_EDGE_BOTTOM**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Types of the expanded safe area.|
| .value[1].u32 | Edges for expanding the safe area.|

## NODE_VISIBLE_AREA_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_CHANGE_RATIO = 93
```

Visible area ratio (visible area/total area of the component) threshold for invoking the visible area change event of the component.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| .value[...].f32 | Threshold array. The value ranges from 0 to 1.|
| .?object | Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[...].f32 | Threshold array.|
| .object | Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).|

## NODE_FOCUS_BOX

```c
NODE_FOCUS_BOX = 96
```

Style of the system focus box for this component.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Distance of the focus box from the component's edge. A positive number indicates the outside, and a negative number indicates the inside. The value cannot be in percentage.|
| .value[1].f32 | Width of the focus box. Negative numbers and percentages are not supported.|
| .value[2].u32 | Color of the focus box.|

## NODE_TAB_STOP

```c
NODE_TAB_STOP = 98
```

Whether the focus can be placed on the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite.|

## NODE_NEXT_FOCUS

```c
NODE_NEXT_FOCUS = 101
```

Next focus node.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Focus movement direction, as defined in [ArkUI_FocusMove](capi-common-attributes-h.md#arkui_focusmove).|
| .object | Next focus node The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|

## NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102
```

Threshold ratio for triggering a visible area change event.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 17

> **NOTE**
> The visible area change callback is not a real-time callback. The actual callback interval may differ from the expected interval due to system load and other factors. The interval between two visible area change callbacks will not be less than the expected update interval. If the provided expected interval is too short, the actual callback interval will be determined by the system load. By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].

**Parameters**

| Name| Description|
| -- | -- |
| .object | Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).|

## NODE_ENABLE_CLICK_SOUND_EFFECT

```c
NODE_ENABLE_CLICK_SOUND_EFFECT = 110
```

Whether the component enables the default click sound effect. This enumerated value takes effect only on TVs. If the default click sound effect is enabled on other devices, the sound effect is not played. Whether the sound can be played depends on the sound settings of the device. For example, the sound effect is not played in mute mode.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component enables the default click sound effect. The value **1** indicates that the default click sound effect is enabled, and the value **0** indicates the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component enables the default click sound effect. The value **1** indicates that the default click sound effect is enabled, and the value **0** indicates the opposite.|

## NODE_HOVER_EFFECT

```c
NODE_HOVER_EFFECT = 112
```

Hover effect applied when the component is hovered over. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect). The default value is **ARKUI_HOVER_EFFECT_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect).|

## NODE_FOCUS_SCOPE_ID

```c
NODE_FOCUS_SCOPE_ID = 113
```

Sets the container as a focus group with the specified identifier. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .string | Focus scope identifier.|
| .value[0].i32 | Whether the scope is a focus group. The default value is **0**. The value can be **1** or **0**. The value **1** indicates that the component is set as a focus group, and the value **0** indicates that the opposite.|
| .value[1].i32 | Whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Focus scope identifier.|
| .value[0].i32 | Whether the scope is a focus group. The default value is **0**. The value can be **1** or **0**. The value **1** indicates that the component is set as a focus group, and the value **0** indicates that the opposite.|
| .value[1].i32 | Whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0** indicates the opposite.|

## NODE_FOCUS_SCOPE_PRIORITY

```c
NODE_FOCUS_SCOPE_PRIORITY = 114
```

Component focus priority within a specific focus scope. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .string | Focus scope identifier.|
| .value[0].i32 | Focus priority within the focus scope. The parameter type is [ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority). The default value is **ARKUI_FOCUS_PRIORITY_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Focus scope identifier.|
| .value[0].i32 | Focus priority within the focus scope. The parameter type is [ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority).|

## NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD

```c
NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115
```

Distance threshold for click events. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Movement threshold for click events. The value range is (0, +∞). The default value is **+∞**. The unit is vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Movement threshold for click events.|

## NODE_RESPONSE_REGION_LIST

```c
NODE_RESPONSE_REGION_LIST = 116
```

Component event response region. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

> **NOTE**
> During configuration, the data array can contain any number of values (all will be accepted), but only 20 values can be retrieved. The order of the retrieved data array may be different from that of the settings.

**Parameters**

| Name| Description|
| -- | -- |
| .data[0].i32 | Event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool). The default value is **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.|
| .data[1].f32 | X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.|
| .data[2].f32 | Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.|
| .data[3].f32 | Width of the response area, in percentage. The default value is **100.0**.|
| .data[4].f32 | Height of the response area, in percentage. The default value is **100.0**.|
| .data[5...].f32 | Multiple response regions that can be set. The sequence of the parameters is the same as the preceding.|

**Returns**

| Type| Description|
| -- | -- |
| .data[0].i32 | Event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool). The default value is **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.|
| .data[1].f32 | X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.|
| .data[2].f32 | Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.|
| .data[3].f32 | Width of the response area, in percentage. The default value is **100.0**.|
| .data[4].f32 | Height of the response area, in percentage. The default value is **100.0**.|
| .data[5...].f32 | Multiple response regions that can be set. The sequence of the parameters is the same as the preceding.|

## NODE_MONOPOLIZE_EVENTS

```c
NODE_MONOPOLIZE_EVENTS = 117
```

Event monopolization attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether event monopolization is set for the component. The value can be **1** or **0**. The value **1** indicates that event monopolization is set for the component, and the value **0** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether event monopolization is set for the component. The value can be **1** or **0**. The value **1** indicates that event monopolization is set for the component, and the value **0** indicates the opposite.|
