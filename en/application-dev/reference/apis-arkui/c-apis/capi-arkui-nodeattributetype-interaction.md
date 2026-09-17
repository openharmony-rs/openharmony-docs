# Interaction

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_VISIBILITY

```c
NODE_VISIBILITY
```

**Description**

Defines the visibility attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show or hide the component. The parameter type is {@link ArkUI_Visibility}. The<br>default value is **ARKUI_VISIBILITY_VISIBLE**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: whether the component is shown or hidden. The parameter type is {@link ArkUI_Visibility}. The default value is **ARKUI_VISIBILITY_VISIBLE**.</li> </ul>

**Since**: 12

### NODE_HIT_TEST_BEHAVIOR

```c
NODE_HIT_TEST_BEHAVIOR
```

**Description**

Defines the hit test behavior attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: hit test mode. The parameter type is {@link ArkUI_HitTestMode}. The default value is **<br>ARKUI_HIT_TEST_MODE_DEFAULT**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: hit test mode. The parameter type is **ArkUI_HitTestMode**. The default value is **<br>ARKUI_HIT_TEST_MODE_DEFAULT**.</li> </ul>

**Since**: 12

### NODE_FOCUSABLE

```c
NODE_FOCUSABLE
```

**Description**

Defines the focus attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The value **1** indicates focusable, and **0** indicates not focusable.<br>The default value is *<br>*0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value **1** indicates focusable, and **0** indicates not focusable.</li> </ul>

**Since**: 12

### NODE_DEFAULT_FOCUS

```c
NODE_DEFAULT_FOCUS
```

**Description**

Defines the default focus attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>value[0].i32: The value **1** indicates that the target is the default focus, and **0** indicates that it is<br>not the default focus.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].i32: The value **1** indicates that the target is the default focus, and **0** indicates that it is not the default focus.</li> </ul>

**Since**: 12

### NODE_RESPONSE_REGION

```c
NODE_RESPONSE_REGION
```

**Description**

Defines the touch target attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.</li><br><li>.data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.</li><br><li>.data[2].f32: width of the touch target, in percentage.</li><br><li>.data[3].f32: height of the touch target, in percentage.</li><br><li>.data[4...].f32: Multiple touch targets can be set. The sequence of the parameters is the same as the<br>preceding.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.data[0].f32: X coordinate of the touch point relative to the upper left corner of the component, in vp.</li><br><li>.data[1].f32: Y coordinate of the touch point relative to the upper left corner of the component, in vp.</li><br><li>.data[2].f32: width of the touch target, in percentage.</li><br><li>.data[3].f32: height of the touch target, in percentage.</li><br><li>.data[4...].f32: Multiple touch targets can be set. The sequence of the parameters is the same as the preceding.</li> <li>Note: During configuration, the data array can contain any number of values (all will be accepted), but only the first 20 values can be retrieved.</li> </ul>

**Since**: 12

### NODE_OVERLAY

```c
NODE_OVERLAY
```

**Description**

Defines the overlay attribute. This attribute can be set, reset, and obtained as required through APIs. You can set the overlay content through .string or .object, with .string having higher priority. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: mask text.</li><br><li>.value[0]?.i32: position of the overlay relative to the component. Optional. The parameter type is<br>{@link ArkUI_Alignment}. The default value is **ARKUI_ALIGNMENT_TOP_START**.</li><br><li>.value[1]?.f32: offset of the overlay relative to the upper left corner of itself on the x-axis, in vp.<br>Optional. The default value is **0** vp.</li><br><li>.value[2]? .f32: offset of the overlay relative to the upper left corner of itself on the y-axis, in vp.<br>Optional. The default value is **0** vp.</li><br><li>.value[3]?.i32: layout direction of the overlay. Optional. The parameter type is {@link ArkUI_Direction}.<br>The default value is **ARKUI_DIRECTION_LTR**.<br>In most scenarios, this parameter should be set to **Auto**, which allows the system to automatically handle<br>the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **<br>LTR** (left-to-right) or **RTL** (right-to-left). It is supported since API version 21.</li><br><li>.object: node tree used for overlay. The parameter type is {@link ArkUI_NodeHandle}, and the default value<br>is **nullptr**. It is supported since API version 21.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: mask text.</li><br><li>.value[0].i32: position of the overlay relative to the component. The parameter type is<br>{@link ArkUI_Alignment}. The default value is **ARKUI_ALIGNMENT_TOP_START**.</li><br><li>.value[1].f32: offset of the overlay relative to the upper left corner of itself on the x-axis, in vp.</li><br><li>.value[2].f32: offset of the overlay relative to the upper left corner of itself on the y-axis, in vp.</li><br><li>.value[3].i32: layout direction of the overlay. The parameter type is {@link ArkUI_Direction}. The default<br>value is **ARKUI_DIRECTION_LTR**. It is supported since API version 21.</li><br><li>.object: node tree used for overlay. The parameter type is {@link ArkUI_NodeHandle}. It is supported since API version 21.</li> </ul>

**Since**: 12

### NODE_FOCUS_STATUS

```c
NODE_FOCUS_STATUS
```

**Description**

Defines the component focus status. This attribute can be set and obtained as required through APIs. <br>Note: Setting the parameter to **0** shifts focus from the currently focused component on the current level of the page to the root container. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The value **1** indicates that the component gains focus and **0** indicates that the<br>component loses focus.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value **1** indicates that the component gains focus and **0** indicates that the component loses focus.</li> </ul>

**Since**: 12

### NODE_FOCUS_ON_TOUCH

```c
NODE_FOCUS_ON_TOUCH
```

**Description**

Sets whether the component is focusable on touch. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the component is focusable on touch. The value **1** means that the component is<br>focusable on touch, and **0** means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the component is focusable on touch. The value **1** means that the component is focusable on touch, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_VISIBLE_AREA_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_CHANGE_RATIO = 93
```

**Description**

Defines the visible area ratio (visible area/total area of the component) threshold for invoking the visible area change event of the component. **Format of the {@link ArkUI_AttributeItem} parameter for setting the<br>attribute:**<br><ul><br><li>.value[...].f32: threshold array. The value ranges from 0 to 1.</li><br><li>.object: The parameter type is {@link ArkUI_VisibleAreaEventOptions}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[...].f32: threshold array.</li><br><li>.object: The return type is {@link ArkUI_VisibleAreaEventOptions}.</li> </ul>

**Since**: 12

### NODE_FOCUS_BOX

```c
NODE_FOCUS_BOX = 96
```

**Description**

Sets the style of the system focus box for this component. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul> <li>.value[0].f32: distance between the focus box and the edge of the component<br><br>A positive number indicates the outside, and a negative number indicates the inside.<br><br>The value cannot be in percentage.</li><br><li>.value[1].f32: width of the focus box. Negative numbers and percentages are not supported.</li><br><li>.value[2].u32: color of the focus box.</li> </ul>

**Since**: 12

### NODE_CLICK_DISTANCE

```c
NODE_CLICK_DISTANCE = 97
```

**Description**

Defines the moving distance limit for the component-bound tap gesture. This attribute can be set as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul> <li>.value[0].f32: allowed moving distance of a finger, in vp.</li> </ul>

**Since**: 12

### NODE_TAB_STOP

```c
NODE_TAB_STOP = 98
```

**Description**

Sets whether the focus can be placed on this component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the focus can be placed on the current component. The value **1** means that the<br>focus can be placed on the current component, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the focus can be placed on the current component. The value **1** means that the focus can be placed on the current component, and **0** means the opposite.</li> </ul>

**Since**: 14

### NODE_NEXT_FOCUS

```c
NODE_NEXT_FOCUS = 101
```

**Description**

Sets the next focus node. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: focus movement direction, as defined in {@link ArkUI_FocusMove}.</li><br><li>.object: next focus node. The parameter type is {@link ArkUI_NodeHandle}.</li> </ul>

**Since**: 18

### NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102
```

**Description**

Sets the threshold ratio for triggering a visible area change event. <br>Note: The visible area change callback is not a real-time callback. The actual callback interval may differ from the expected interval due to system load and other factors. The interval between two visible area change callbacks will not be less than the expected update interval. If the provided expected interval is too short, the actual callback interval will be determined by the system load. By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective<br>threshold will be [0.0, 0.5]. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: parameters for visible area change events. The parameter type is<br>{@link ArkUI_VisibleAreaEventOptions}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: parameters for visible area change events. The parameter type is<br>{@link ArkUI_VisibleAreaEventOptions}.</li> </ul>

**Since**: 17

### NODE_ENABLE_CLICK_SOUND_EFFECT

```c
NODE_ENABLE_CLICK_SOUND_EFFECT = 110
```

**Description**

Sets whether the component enables the default click sound effect. This API takes effect only on TVs. If the default click sound effect is enabled on other devices, the sound effect is not played. Whether the sound can be played depends on the sound settings of the device. For example, the sound effect is not played in mute mode. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The value can be **1** or **0**. The value **1** indicates that the default click sound<br>effect is enabled, and the value **0** indicates that the default click sound effect is disabled. The default<br>value is **1**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the default click sound effect is enabled for the node. The value can be **1** or **0*<br>*. The value **1** indicates that the default click sound effect is enabled, and the value **0** indicates that the default click sound effect is disabled.</li> </ul>

**Since**: 24

### NODE_HOVER_EFFECT

```c
NODE_HOVER_EFFECT = 112
```

**Description**

Defines the hover effect applied when the component is hovered over. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: hover effect applied when the component is hovered over. The parameter type is<br>{@link ArkUI_HoverEffect}. The default value is **ARKUI_HOVER_EFFECT_AUTO**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: hover effect applied when the component is hovered over. The parameter type is<br>{@link ArkUI_HoverEffect}.</li> </ul>

**Since**: 23

### NODE_FOCUS_SCOPE_ID

```c
NODE_FOCUS_SCOPE_ID = 113
```

**Description**

Configures the container as a focus group with the specified identifier. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: focus scope identifier.</li><br><li>.value[0].i32: whether the scope is a focus group. The default value is **0**. The value can be **1** or **0*<br>*. The value **1** indicates that the component is set as a focus group. The value **0** indicates that the<br>component is not set as a focus group.</li><br><li>.value[1].i32: whether arrow keys can move focus from inside the focus group to outside. This setting only<br>takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The<br>value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0**<br>indicates that arrow keys cannot move focus from inside the focus group to outside.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: focus scope identifier.</li> <li>.value[0].i32: whether the scope is a focus group. The default value is **0**. The value can be **1** or **0*<br>*. The value **1** indicates that the component is set as a focus group. The value **0** indicates that the<br>component is not set as a focus group.</li><br><li>.value[1].i32: whether arrow keys can move focus from inside the focus group to outside. This setting only takes effect when **isGroup** is **true**. The default value is **1**. The value can be **1** or **0**. The value **1** indicates that arrow keys can move focus from inside the focus group to outside, and the value **0**<br>indicates that arrow keys cannot move focus from inside the focus group to outside.</li> </ul>

**Since**: 23

### NODE_FOCUS_SCOPE_PRIORITY

```c
NODE_FOCUS_SCOPE_PRIORITY = 114
```

**Description**

Sets the component focus priority within a specific focus scope. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: focus scope identifier.</li><br><li>.value[0].i32: focus priority within the focus scope. The parameter type is {@link ArkUI_FocusPriority}. The<br>default value is **ARKUI_FOCUS_PRIORITY_AUTO**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: focus scope identifier.</li><br><li>.value[0].i32: focus scope priority. The parameter type is {@link ArkUI_FocusPriority}.</li> </ul>

**Since**: 23

### NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD

```c
NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115
```

**Description**

Sets the distance threshold for click events. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: movement threshold for click events. Value range: (0, +∞) Default value:**+∞**.<br> Unit: vp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: movement threshold for click events.</li> </ul>

**Since**: 23

### NODE_RESPONSE_REGION_LIST

```c
NODE_RESPONSE_REGION_LIST = 116
```

**Description**

Defines the component event response region. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.data[0].i32: event tool type for the response region. The parameter type is<br>{@link ArkUI_ResponseRegionSupportedTool}. Default value:**ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.</li><br><li>.data[1].f32: X coordinate of the pointer position relative to the upper left corner of the component, in vp.<br> The default value is **0.0**.</li><br><li>.data[2].f32: Y coordinate of the pointer position relative to the upper left corner of the component, in vp.<br> The default value is **0.0**.</li><br><li>.data[3].f32: width of the response region, in percentage. The default value is **100.0**.</li><br><li>.data[4].f32: height of the response region, in percentage. The default value is **100.0**.</li><br><li>.data[5...].f32: additional response regions in the same parameter order.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.data[0].i32: event tool type for the response region. The parameter type is<br>{@link ArkUI_ResponseRegionSupportedTool}. Default value:**ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL**.</li> <li>.data[1].f32: X coordinate of the pointer position relative to the upper left corner of the component, in vp.<br> The default value is **0.0**.</li><br><li>.data[2].f32: Y coordinate of the pointer position relative to the upper left corner of the component, in vp.<br> The default value is **0.0**.</li><br><li>.data[3].f32: width of the response region, in percentage. The default value is **100.0**.</li><br><li>.data[4].f32: height of the response region, in percentage. The default value is **100.0**.</li><br><li>.data[5...].f32: additional response regions in the same parameter order.</li> <li>Note: During configuration, the data array can contain any number of values (all will be accepted), but only 20 values can be retrieved. The order of the retrieved data array may be different from that of the settings.</li> </ul>

**Since**: 23

### NODE_MONOPOLIZE_EVENTS

```c
NODE_MONOPOLIZE_EVENTS = 117
```

**Description**

Defines the event monopolization attribute. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The value can be **1** or **0**. The value **1** indicates that the component exclusively<br>handles events. The value **0** indicates that the component does not exclusively handle events.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value can be **1** or **0**. The value **1** indicates that the component exclusively handles events. The value **0** indicates that the component does not exclusively handle events.</li> </ul>

**Since**: 23


