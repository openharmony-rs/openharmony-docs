# Interaction

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_VISIBILITY

```c
NODE_VISIBILITY
```

**Description**

Visibility attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show or hide the component. The parameter type is [ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility). The default value is **ARKUI_VISIBILITY_VISIBLE**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the component is shown or hidden. The parameter type is [ArkUI_Visibility](capi-common-attributes-h.md#arkui_visibility). Default value: **ARKUI_VISIBILITY_VISIBLE**. The meaning of each enumerated value and its corresponding number are as follows: **ARKUI_VISIBILITY_VISIBLE(0)** indicates visible, **ARKUI_VISIBILITY_HIDDEN(1)**<br>indicates hidden but occupying space, and **ARKUI_VISIBILITY_NONE(2)** indicates hidden and not occupying space.</li> </ul>

**Since**: 12

### NODE_HIT_TEST_BEHAVIOR

```c
NODE_HIT_TEST_BEHAVIOR
```

**Description**

Hit test behavior attribute, which can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Hit test mode. The parameter type is [ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode). The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Hit test mode. The parameter type is [ArkUI_HitTestMode](capi-common-attributes-h.md#arkui_hittestmode). The default value is **ARKUI_HIT_TEST_MODE_DEFAULT**.</li> </ul>

**Since**: 12

### NODE_FOCUSABLE

```c
NODE_FOCUSABLE
```

**Description**

Focus attribute, which controls whether the component can gain focus. It is applicable to scenarios such as keyboard navigation and accessibility assistance. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite. The default value is **0**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite.</li> </ul>

**Since**: 12

### NODE_DEFAULT_FOCUS

```c
NODE_DEFAULT_FOCUS
```

**Description**

Default focus attribute, which can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the focus is the default one. The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the focus is the default one. The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.</li> </ul>

**Since**: 12

### NODE_RESPONSE_REGION

```c
NODE_RESPONSE_REGION
```

**Description**

Touch target attribute, which can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.</li> <li>.data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.</li> <li>.data[2].f32: Width of the touch target, in percentage.</li> <li>.data[3].f32: Height of the touch target, in percentage.</li> <li>.data[4...].f32: Multiple touch targets that can be set. The sequence of the parameters is the same as the preceding.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.</li> <li>.data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.</li> <li>.data[2].f32: Width of the touch target, in percentage.</li> <li>.data[3].f32: Height of the touch target, in percentage.</li> <li>.data[4...].f32: Multiple touch targets that can be set. The sequence of the parameters is the same as the preceding.</li> <li>Note: During configuration, the data array can contain any number of values (all will be accepted), but only the first 20 values can be retrieved.</li> </ul>

**Since**: 12

### NODE_OVERLAY

```c
NODE_OVERLAY
```

**Description**

Overlay attribute, which can be set, reset, and obtained as required through APIs. You can set the overlay content through **.string** or **.object**, with **.string** having higher priority. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: Overlay text.</li> <li>.value[0]?.i32: Position of the overlay relative to the component. This parameter is optional. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.</li> <li>.value[1]?.f32: Offset of the overlay relative to the upper left corner of itself on the x-axis, in vp. This parameter is optional. The default value is **0** vp.</li> <li>.value[2]?.f32: Offset of the overlay relative to the upper left corner of itself on the y-axis, in vp. This parameter is optional. The default value is **0** vp.</li> <li>.value[3]?.i32: Layout direction of the overlay. This parameter is optional. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**. In most scenarios, this parameter should be set to **Auto**, which allows the system to automatically handle the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **<br>LTR** (left-to-right) or **RTL** (right-to-left). It is supported since API version 21.</li> <li>.object: Node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md). The default value is **<br>nullptr**. It is supported since API version 21.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: Overlay text.</li> <li>.value[0].i32: Position of the overlay relative to the component. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**.</li> <li>.value[1].f32: Offset of the overlay relative to the upper left corner of itself on the x-axis, in vp.</li> <li>.value[2].f32: Offset of the overlay relative to the upper left corner of itself on the y-axis, in vp.</li> <li>.value[3].i32: Layout direction of the overlay. The parameter type is [ArkUI_Direction](capi-layout-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_LTR**. It is supported since API version 21.</li> <li>.object: Node tree used for overlay. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md). It is supported since API version 21.</li> </ul>

**Since**: 12

### NODE_FOCUS_STATUS

```c
NODE_FOCUS_STATUS
```

**Description**

Component focus status. This attribute can be set and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Component focus status. The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Component focus status. The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.</li> <li>Note: Setting the parameter to **0** shifts focus from the currently focused component on the current level of the page to the root container.</li> </ul>

**Since**: 12

### NODE_FOCUS_ON_TOUCH

```c
NODE_FOCUS_ON_TOUCH
```

**Description**

Whether the component is focusable on touch. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_VISIBLE_AREA_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_CHANGE_RATIO = 93
```

**Description**

Visible area ratio (visible area/total area of the component) threshold for invoking the visible area change event of the component. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[...].f32: Threshold array. The value ranges from 0 to 1.</li> <li>.object: Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[...].f32: Threshold array.</li> <li>.object: Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li> </ul>

**Since**: 12

### NODE_FOCUS_BOX

```c
NODE_FOCUS_BOX = 96
```

**Description**

Style of the system focus box for this component. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Distance of the focus box from the component's edge. A positive number indicates the outside, and a negative number indicates the inside. The value cannot be in percentage.</li> <li>.value[1].f32: Width of the focus box. Negative numbers and percentages are not supported.</li> <li>.value[2].u32: Color of the focus box.</li> </ul>

**Since**: 12

### NODE_CLICK_DISTANCE

```c
NODE_CLICK_DISTANCE = 97
```

**Description**

Moving distance limit for the component-bound click gesture. This attribute can be set as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Distance threshold within which the finger is allowed to move when a click gesture is recognized, in vp. The value range is [0, +∞). If the value is less than 0, the default value is used. The default value is infinite. A smaller value is suitable for scenarios requiring high click precision, and a larger value is suitable for scenarios requiring high click fault tolerance.</li> </ul>

**Since**: 12

### NODE_TAB_STOP

```c
NODE_TAB_STOP = 98
```

**Description**

Whether the focus can be placed on the component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite. The default value is **0**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite.</li> </ul>

**Since**: 14

### NODE_NEXT_FOCUS

```c
NODE_NEXT_FOCUS = 101
```

**Description**

Next focus node.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Focus movement direction, as defined in [ArkUI_FocusMove](capi-common-attributes-h.md#arkui_focusmove).</li> <li>.object: Next focus node. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> </ul>

**Since**: 18

### NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102
```

**Description**

Threshold ratio for triggering a visible area change event. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Parameters for visible area change events. The parameter type is [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md).</li> <li>Note: The visible area change callback is not a real-time callback. The actual callback interval may differ from the expected interval due to system load and other factors. The interval between two visible area change callbacks will not be less than the expected update interval. If the provided expected interval is too short, the actual callback interval will be determined by the system load. By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].</li> </ul>

**Since**: 17

### NODE_ENABLE_CLICK_SOUND_EFFECT

```c
NODE_ENABLE_CLICK_SOUND_EFFECT = 110
```

**Description**

Whether the component enables the default click sound effect. This enumerated value takes effect only on TVs. If the default click sound effect is enabled on other devices, the sound effect is not played. Whether the sound can be played depends on the sound settings of the device. For example, the sound effect is not played in mute mode. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the component enables the default click sound effect. The value **1** indicates that the default click sound effect is enabled, and the value **0** indicates the opposite. The default value is **1**. </li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the component enables the default click sound effect. The value **1** indicates that the default click sound effect is enabled, and the value **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_HOVER_EFFECT

```c
NODE_HOVER_EFFECT = 112
```

**Description**

Hover effect applied when the component is hovered over. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect). The default value is **ARKUI_HOVER_EFFECT_AUTO**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Hover effect applied when the component is hovered over. The parameter type is [ArkUI_HoverEffect](capi-common-attributes-h.md#arkui_hovereffect).</li> </ul>

**Since**: 23

### NODE_FOCUS_SCOPE_ID

```c
NODE_FOCUS_SCOPE_ID = 113
```

**Description**

Sets the container as a focus group with the specified identifier. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: Focus scope identifier.</li> <li>.value[0].i32: Whether the scope is a focus group. The default value is **0**. The value can be **1** or **<br>0**. The value **1** indicates that the component is set as a focus group, and the value **0** indicates that the opposite.</li> <li>.value[1].i32: Whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0**<br>indicates the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: Focus scope identifier.</li> <li>.value[0].i32: Whether the scope is a focus group. The default value is **0**. The value can be **1** or **<br>0**. The value **1** indicates that the component is set as a focus group, and the value **0** indicates that the opposite.</li> <li>.value[1].i32: Whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0**<br>indicates the opposite.</li> </ul>

**Since**: 23

### NODE_FOCUS_SCOPE_PRIORITY

```c
NODE_FOCUS_SCOPE_PRIORITY = 114
```

**Description**

Component focus priority within a specific focus scope. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: Focus scope identifier.</li> <li>.value[0].i32: Focus priority within the focus scope. The parameter type is [ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority). The default value is **ARKUI_FOCUS_PRIORITY_AUTO**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: Focus scope identifier.</li> <li>.value[0].i32: Focus priority within the focus scope. The parameter type is [ArkUI_FocusPriority](capi-common-attributes-h.md#arkui_focuspriority).</li> </ul>

**Since**: 23

### NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD

```c
NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115
```

**Description**

Distance threshold for click events. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Movement threshold for click events. If the value specified is less than or equal to 0, it will be converted to the default value. The value range is (0, +∞). The default value is **+∞**. The unit is vp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Movement threshold for click events.</li> <li>Note: If finger movement exceeds the preset distance limit, click event recognition will fail.</li> </ul>

**Since**: 23

### NODE_RESPONSE_REGION_LIST

```c
NODE_RESPONSE_REGION_LIST = 116
```

**Description**

Component event response region. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].i32: Event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool). The default value is **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.</li> <li>.data[1].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.</li> <li>.data[2].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.</li> <li>.data[3].f32: Width of the response region, in percentage. The default value is **100.0**.</li> <li>.data[4].f32: Height of the response region, in percentage. The default value is **100.0**.</li> <li>.data[5...].f32: Multiple response regions that can be set. The sequence of the parameters is the same as the preceding.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].i32: Event tool type for the response region. The parameter type is [ArkUI_ResponseRegionSupportedTool](capi-common-attributes-h.md#arkui_responseregionsupportedtool). The default value is **ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.</li> <li>.data[1].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.</li> <li>.data[2].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp. The default value is **0.0**.</li> <li>.data[3].f32: Width of the response region, in percentage. The default value is **100.0**.</li> <li>.data[4].f32: Height of the response region, in percentage. The default value is **100.0**.</li> <li>.data[5...].f32: Multiple response regions that can be set. The sequence of the parameters is the same as the preceding.</li> <li>Note: During configuration, the data array can contain any number of values (all will be accepted), but only 20 values can be retrieved. The order of the retrieved data array may be different from that of the settings.</li> </ul>

**Since**: 23

### NODE_MONOPOLIZE_EVENTS

```c
NODE_MONOPOLIZE_EVENTS = 117
```

**Description**

Event monopolization attribute, which can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether event monopolization is set for the component. The value can be **1** or **0**. The value **1** indicates that event monopolization is set for the component, and the value **0** indicates the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether event monopolization is set for the component. The value can be **1** or **0**. The value **1** indicates that event monopolization is set for the component, and the value **0** indicates the opposite.</li> </ul>

**Since**: 23


