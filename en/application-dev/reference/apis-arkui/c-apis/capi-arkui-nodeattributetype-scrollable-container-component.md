# Scrollable Container Component

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_SCROLL_BAR_DISPLAY_MODE

```c
NODE_SCROLL_BAR_DISPLAY_MODE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SCROLL
```

**Description**

Scrollbar display mode. This attribute can be set, reset, and obtained as required through APIs. {@link List}, Scroll, and WaterFlow support this attribute since API version 12, and Grid supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: scrollbar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode). The default value is <b>ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO</b> for the <b>List</b>, <b>Grid</b>, and <b>Scroll</b> components, and <b>ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF</b> for the <b>WaterFlow</b> component.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: scrollbar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode).</li> </ul>

**Since**: 12

### NODE_SCROLL_BAR_WIDTH

```c
NODE_SCROLL_BAR_WIDTH
```

**Description**

Width of the scrollbar. This attribute can be set, reset, and obtained as required through APIs. {@link List}, Scroll, and WaterFlow support this attribute since API version 12, and Grid supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width of the scrollbar, in vp. The default value is <b>4</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the scrollbar, in vp.</li> </ul>

**Since**: 12

### NODE_SCROLL_BAR_COLOR

```c
NODE_SCROLL_BAR_COLOR
```

**Description**

Color of the scrollbar. This attribute can be set, reset, and obtained as required through APIs. {@link List}, Scroll, and WaterFlow support this attribute since API version 12, and Grid supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].u32: color of the scrollbar, in 0xARGB format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].u32: color of the scrollbar, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_SCROLL_SCROLL_DIRECTION

```c
NODE_SCROLL_SCROLL_DIRECTION
```

**Description**

Scroll direction. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-scroll-h.md#arkui_scrolldirection). The default value is <b>ARKUI_SCROLL_DIRECTION_VERTICAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: scroll direction. The parameter type is [ArkUI_ScrollDirection](capi-scroll-h.md#arkui_scrolldirection).</li> </ul>

**Since**: 12

### NODE_SCROLL_EDGE_EFFECT

```c
NODE_SCROLL_EDGE_EFFECT
```

**Description**

Effect used at the edges of the component when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_NONE</b>.</li> <li>.value[1]?.i32: whether to enable the scroll effect when the component content size is smaller than the component itself. Optional. The value <b>1</b> means to enable the scroll effect, and <b>0</b> means the opposite. The default value for the List/Grid/WaterFlow component is <b>0</b>, and the default value for the Scroll component is <b>1</b>.</li> <li>.value[2]?.i32: direction in which the effect takes effect. The parameter type is [ArkUI_EffectEdge](capi-scroll-h.md#arkui_effectedge). The default value is <b>ARKUI_EFFECT_EDGE_START \| ARKUI_EFFECT_EDGE_END</b>. This parameter is supported since API version 16.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li> <li>.value[1].i32: whether to enable the scroll effect when the component content size is smaller than the component itself. Optional. The value <b>1</b> means to enable the scroll effect, and <b>0</b> means the opposite.</li> <li>.value[2].i32: edge for which the effect takes effect when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EffectEdge](capi-scroll-h.md#arkui_effectedge). This parameter is supported since API version 16.</li> </ul>

**Since**: 12

### NODE_SCROLL_ENABLE_SCROLL_INTERACTION

```c
NODE_SCROLL_ENABLE_SCROLL_INTERACTION
```

**Description**

Whether to support scroll gestures. When this attribute is set to **0**, scrolling by finger or mouse is not supported, but the scrolling controller API is not affected. <br>The **List**, **Scroll**, and **WaterFlow** components support this attribute since API version 12, and the **Grid** component supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support scroll gestures. The default value is <b>true</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to support scroll gestures.</li> </ul>

**Since**: 12

### NODE_SCROLL_FRICTION

```c
NODE_SCROLL_FRICTION
```

**Description**

Friction coefficient. It applies only to gestures in the scrolling area, and it only indirectly affects the scroll chaining during the inertial scrolling process. <br>The **List**, **Scroll**, and **WaterFlow** components support this attribute since API version 12, and the **Grid** component supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: friction coefficient. The default value is <b>0.6</b> for non-wearable devices and <b>0.9</b> for wearable devices.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: friction coefficient.</li> </ul>

**Since**: 12

### NODE_SCROLL_SNAP

```c
NODE_SCROLL_SNAP
```

**Description**

Scroll snapping mode of the Scroll component. This attribute can be set, reset, and obtained as required through APIs. If both swipe-to-turn-pages and scroll snapping are set, scroll snapping takes effect first, and swipe-to-turn-pages does not take effect. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode for the scroll snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign). The default value is <b>ARKUI_SCROLL_SNAP_ALIGN_NONE</b>.</li> <li>.value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the <b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between the start edge and the first snap point. The default value is <b>true</b>. It is valid only when there are multiple snap points.</li> <li>.value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the <b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between the end edge and the last snap point. The default value is <b>true</b>. It is valid only when there are multiple snap points.</li> <li>.value[3...].f32: snap points for the <b><Scroll></b> component. Each snap point defines the offset from an edge to which the <b><Scroll></b> component can scroll.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode for the scroll snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign).</li> <li>.value[1].i32: whether to enable the snap to start feature. When scroll snapping is defined for the <b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between the start edge and the first snap point.</li> <li>.value[2].i32: Whether to enable the snap to end feature. When scroll snapping is defined for the <b><Scroll></b> component, setting this attribute to <b>false</b> enables the component to scroll between the end edge and the last snap point.</li> <li>.value[3...].f32: snap points for the <b><Scroll></b> component. Each snap point defines the offset from an edge to which the <b><Scroll></b> component can scroll.</li> </ul>

**Since**: 12

### NODE_SCROLL_NESTED_SCROLL

```c
NODE_SCROLL_NESTED_SCROLL
```

**Description**

Nested scrolling attribute, which can be set, reset, and obtained as required through APIs. The **List**, **Scroll**, and **WaterFlow** components support this attribute since API version 12, and the **Grid** component supports this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: nested scrolling option when the component scrolls forward. The parameter type is [ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode).</li> <li>.value[1].i32: nested scrolling option when the component scrolls backward. The parameter type is [ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: nested scrolling option when the component scrolls forward. The parameter type is [ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode).</li> <li>.value[1].i32: nested scrolling option when the component scrolls backward. The parameter type is [ArkUI_ScrollNestedMode](capi-scroll-h.md#arkui_scrollnestedmode).</li> </ul>

**Since**: 12

### NODE_SCROLL_OFFSET

```c
NODE_SCROLL_OFFSET
```

**Description**

Position to scroll to for the Scroll component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: horizontal scrolling offset, in vp.</li> <li>.value[1].f32: vertical scrolling offset, in vp.</li> <li>.value[2]?.i32: scrolling duration, in milliseconds. Optional.</li> <li>.value[3]?.i32: scrolling curve. Optional. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is <b>ARKUI_CURVE_EASE</b>.</li> <li>.value[4]?.i32: whether to enable the default spring animation. Optional. The default value <b>0</b> means not to enable the default spring animation.</li> <li>.value[5]?.i32: whether to convert the scroll animation to an overshoot animation when the boundary is reached. Optional.</li> <li>.value[6]?.i32: whether the component can stop at an overscrolled position. This parameter is supported since API version 20.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: horizontal scrolling offset, in vp.</li> <li>.value[1].f32: vertical scrolling offset, in vp.</li> </ul>

**Since**: 12

### NODE_SCROLL_EDGE

```c
NODE_SCROLL_EDGE
```

**Description**

Edge position to scroll to for the Scroll component. This attribute can be set and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: edge position to scroll to. The parameter type is [ArkUI_ScrollEdge](capi-scroll-h.md#arkui_scrolledge).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the container at the edge position. The value <b>-1</b> means that the container is not at the edge position. If the container is at the edge position, the parameter type is [ArkUI_ScrollEdge](capi-scroll-h.md#arkui_scrolledge).</li> </ul>

**Since**: 12

### NODE_SCROLL_ENABLE_PAGING

```c
NODE_SCROLL_ENABLE_PAGING
```

**Description**

Whether to enable the swipe-to-turn-pages feature. This attribute can be set, reset, and obtained as required through APIs. If both enablePaging and scrollSnap are set, scrollSnap takes effect preferentially, and enablePaging does not take effect. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the swipe-to-turn-pages feature. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable the swipe-to-turn-pages feature.</li> </ul>

**Since**: 12

### NODE_SCROLL_PAGE

```c
NODE_SCROLL_PAGE
```

**Description**

Scrolls to the next or previous page. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Indicates whether to scroll to next page. Value 0 indicates scroll to next page and value 1 indicates scroll to previous page.</li> <li>.value[1]?.i32: Indicates whether to enable animation. Value 1 indicates enable and 0 indicates disable.</li> </ul>

**Since**: 12

### NODE_SCROLL_BY

```c
NODE_SCROLL_BY
```

**Description**

Scrolling distance. The **List**, **Scroll**, and **WaterFlow** components support this attribute since API version 12. The **Grid** component supports this attribute since API version 26.0.0. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Horizontal scrolling distance in vp.</li> <li>.value[1].f32: Vertical scrolling distance in vp.</li> </ul>

**Since**: 12

### NODE_SCROLL_FLING

```c
NODE_SCROLL_FLING
```

**Description**

Performs inertial scrolling based on the initial velocity passed in. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Initial velocity of inertial scrolling. Unit: vp/s. If the value specified is 0, it is considered as invalid, and the scrolling for this instance will not take effect. If the value is positive, the scroll will move downward; if the value is negative, the scroll will move upward.</li> </ul>

**Since**: 13

### NODE_SCROLL_FADING_EDGE

```c
NODE_SCROLL_FADING_EDGE
```

**Description**

Edge fade effect for the scrollable component. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the fading effect on edges. The value 0 means to disable the fading effect, and 1 means to enable it.</li> <li>.value[1]?.f32: length of the fading effect on edges, in vp. Default value: 32.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the fading effect on edges is enabled. The value 0 means that the fading effect is disabled, and 1 means that it is enabled.</li> <li>.value[1].f32: length of the fading effect on edges, in vp.</li> </ul>

**Since**: 14

### NODE_SCROLL_SIZE

```c
NODE_SCROLL_SIZE
```

**Description**

Total size of all child components when fully expanded in the scrollable component. <br>The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: total width of all child components when fully expanded in the scrollable component. The default unit is vp.</li> <li>.value[1].f32: total height of all child components when fully expanded in the scrollable component. The default unit is vp. When <b>NODE_PADDING</b>, <b>NODE_MARGIN</b>, or <b>NODE_BORDER_WIDTH</b> is set, the values are rounded to the nearest pixel when being converted from vp to px. The returned values are calculated based on these rounded pixel values.</li> </ul>

**Since**: 14

### NODE_SCROLL_CONTENT_START_OFFSET

```c
NODE_SCROLL_CONTENT_START_OFFSET
```

**Description**

Offset from the start of the content of the scrollable component. List supports this attribute since API version 15, and Grid, Scroll, and WaterFlow support this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: offset from the start of the content, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: offset from the start of the content, in vp.</li> </ul>

**Since**: 15

### NODE_SCROLL_CONTENT_END_OFFSET

```c
NODE_SCROLL_CONTENT_END_OFFSET
```

**Description**

Offset from the end of the content of the scrollable component. List supports this attribute since API version 15, and Grid, Scroll, and WaterFlow support this attribute since API version 22. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: offset from the end of the content, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: offset from the end of the content, in vp.</li> </ul>

**Since**: 15

### NODE_SCROLL_FLING_SPEED_LIMIT

```c
NODE_SCROLL_FLING_SPEED_LIMIT = 1002019
```

**Description**

Maximum initial velocity at the start of the fling animation that occurs after gesture-driven scrolling ends. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum starting fling speed, Unit: vp/s</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum starting fling speed, Unit: vp/s</li> </ul>

**Since**: 18

### NODE_SCROLL_CLIP_CONTENT

```c
NODE_SCROLL_CLIP_CONTENT = 1002020
```

**Description**

Content clipping area for the scrollable component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: clip content mode. The parameter type is [ArkUI_ContentClipMode](capi-scroll-h.md#arkui_contentclipmode). The default value is <b>ARKUI_CONTENT_CLIP_MODE_BOUNDARY</b> for the <b>Grid</b> and <b>Scroll</b> components, and <b>ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY</b> for the <b>List</b> and <b>WaterFlow</b> components.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: clip content mode. The parameter type is [ArkUI_ContentClipMode](capi-scroll-h.md#arkui_contentclipmode).</li> </ul>

**Since**: 18

### NODE_SCROLL_BACK_TO_TOP

```c
NODE_SCROLL_BACK_TO_TOP = 1002021
```

**Description**

Whether to scroll back to the top when the status bar is clicked for the scrollable component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the scrollable scrolls back to top when status bar is clicked. The value <b>1</b> means to scroll back to top, and <b>0</b> means the opposite. The default value is <b>0</b> for API versions earlier than 18. For API version 18 and later, the default value is <b>0</b> for the horizontal scroll direction and <b>1</b> for the vertical scroll direction.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the scrollable scrolls back to top when status bar is clicked.</li> </ul>

**Since**: 15

### NODE_SCROLL_BAR_MARGIN

```c
NODE_SCROLL_BAR_MARGIN = 1002022
```

**Description**

Margin of the scrollbar. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: start margin of the scrollbar, in vp. The default value is <b>0</b>.</li> <li>.value[1].f32: end margin of the scrollbar, in vp. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: start margin of the scrollbar, in vp.</li> <li>.value[1].f32: end margin of the scrollbar, in vp.</li> </ul>

**Since**: 20

### NODE_SCROLL_MAX_ZOOM_SCALE

```c
NODE_SCROLL_MAX_ZOOM_SCALE = 1002023
```

**Description**

Maximum zoom scale for scrollable content. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum zoom scale to set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: current maximum zoom scale.</li> </ul>

**Since**: 20

### NODE_SCROLL_MIN_ZOOM_SCALE

```c
NODE_SCROLL_MIN_ZOOM_SCALE = 1002024
```

**Description**

Minimum zoom scale for scrollable content. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum zoom scale to set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: current minimum zoom scale.</li> </ul>

**Since**: 20

### NODE_SCROLL_ZOOM_SCALE

```c
NODE_SCROLL_ZOOM_SCALE = 1002025
```

**Description**

Zoom scale for scrollable content. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: zoom scale to set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: current zoom scale.</li> </ul>

**Since**: 20

### NODE_SCROLL_ENABLE_BOUNCES_ZOOM

```c
NODE_SCROLL_ENABLE_BOUNCES_ZOOM = 1002026
```

**Description**

Whether to enable the zoom bounce effect when the scaling exceeds the limits. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits. The value <b>1</b> means to enable the effect, and <b>0</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable the zoom bounce effect when the scaling exceeds the limits. The value <b>1</b> means to enable the effect, and <b>0</b> means the opposite.</li> </ul>

**Since**: 20

### NODE_SCROLL_ENABLE_SCROLL_WITH_MOUSE

```c
NODE_SCROLL_ENABLE_SCROLL_WITH_MOUSE = 1002027
```

**Description**

Sets whether dragging scrolling with the left mouse button pressed is supported.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether dragging scrolling with the left mouse button pressed is supported. <b>0</b>: no; <b>1</b>: yes. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether dragging scrolling with the left mouse button pressed is supported. <b>0</b>: no; <b>1</b>: yes.</li> </ul>

**Since**: 26.0.0

### NODE_SCROLL_AUTO_ADJUST_MARGIN

```c
NODE_SCROLL_AUTO_ADJUST_MARGIN = 1002028
```

**Description**

Whether the scrollbar automatically adjusts its margin to avoid the area of the **NODE_PADDING**, **NODE_SCROLL_CONTENT_START_OFFSET**, or **NODE_SCROLL_CONTENT_END_OFFSET** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to automatically adjust the margin of the scrollbar. <b>0</b>: yes; <b>1</b>: no. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to automatically adjust the margin of the scrollbar. <b>0</b>: yes; <b>1</b>: no.</li> </ul>

**Since**: 26.0.0

### NODE_SCROLL_BAR_HEIGHT

```c
NODE_SCROLL_BAR_HEIGHT = 1002029
```

**Description**

Scrollbar height. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height of the scrollbar track, in vp. Default value: adaptive to the height of the scrollable component. Value range: The value must be greater than or equal to 0. If set to a value less than 0, the default value is used. If set to 0, the scrollbar is not displayed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height of the scrollbar track, in vp.</li> </ul>

**Since**: 26.0.0

### NODE_LIST_DIRECTION

```c
NODE_LIST_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST
```

**Description**

Direction in which the list items are arranged. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-layout-h.md#arkui_axis). The default value is <b>ARKUI_AXIS_VERTICAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: direction in which the list items are arranged. The parameter type is [ArkUI_Axis](capi-layout-h.md#arkui_axis).</li> </ul>

**Since**: 12

### NODE_LIST_STICKY

```c
NODE_LIST_STICKY
```

**Description**

Whether to pin the header to the top or the footer to the bottom in the ListItemGroup component. It is used together with the **ListItemGroup** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to pin the header to the top or the footer to the bottom in the <b><ListItemGroup></b> component. It is used together with the <b><ListItemGroup></b> component. The parameter type is [ArkUI_StickyStyle](capi-list-h.md#arkui_stickystyle). The default value is <b>ARKUI_STICKY_STYLE_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to pin the header to the top or the footer to the bottom in the <b><ListItemGroup></b> component. It is used together with the <b><ListItemGroup></b> component. The parameter type is [ArkUI_StickyStyle](capi-list-h.md#arkui_stickystyle).</li> </ul>

**Since**: 12

### NODE_LIST_SPACE

```c
NODE_LIST_SPACE
```

**Description**

Spacing between list items. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: spacing between list items along the main axis. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: spacing between list items along the main axis.</li> </ul>

**Since**: 12

### NODE_LIST_NODE_ADAPTER

```c
NODE_LIST_NODE_ADAPTER
```

**Description**

Adapter of the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: ArkUI_NodeAdapter object as the adapter.</li> </ul>

**Since**: 12

### NODE_LIST_CACHED_COUNT

```c
NODE_LIST_CACHED_COUNT
```

**Description**

Number of cached items in the adapter of the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of cached items in the list adapter.</li> <li>.value[1]?.i32: whether to show cached items. The value <b>0</b> means to hide cached items, and <b>1</b> means to show cached items. The default value is <b>0</b>. This parameter is supported since API version 15.</li> <li>.value[2]?.i32: maximum cache count. This parameter is supported since API version 22.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of cached items in the list adapter.</li> <li>.value[1].i32: whether to show cached items. The value <b>0</b> means to hide cached items, and <b>1</b> means to show cached items. This parameter is supported since API version 15.</li> <li>.value[2].i32: maximum cache count. This parameter is supported since API version 22.</li> </ul>

**Since**: 12

### NODE_LIST_SCROLL_TO_INDEX

```c
NODE_LIST_SCROLL_TO_INDEX
```

**Description**

Scroll to the specified index. When activating the smooth animation, all items passed through will be loaded and layout calculated, which can lead to performance issues when loading a large number of items.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index value of the target element to be slid to in the current container.</li> <li>.value[1]?.i32: whether there is an action when sliding to the index value of a list item in the list, where 1 indicates an action and 0 indicates no action. Default value: 0.</li> <li>.value[2]?.i32: alignment of the sliding element with the current container. The parameter type is [ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment). The default value is <b>ARKUI_SCROLL_ALIGNMENT_START</b>.</li> <li>.value[3]?.f32: extra offset, in vp. The default value is <b>0</b>. This parameter is supported since API version 15.</li> </ul>

**Since**: 12

### NODE_LIST_ALIGN_LIST_ITEM

```c
NODE_LIST_ALIGN_LIST_ITEM
```

**Description**

Alignment mode of list items along the cross axis when the cross-axis width of the list is greater than the cross-axis width of list items multiplied by the number of lanes. When the list scrolls vertically, the number of lanes is the number of columns; when the list scrolls horizontally, the number of lanes is the number of rows. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode of list items along the cross axis. The parameter type is [ArkUI_ListItemAlignment](capi-list-h.md#arkui_listitemalignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode of list items along the cross axis. The parameter type is [ArkUI_ListItemAlignment](capi-list-h.md#arkui_listitemalignment).</li> </ul>

**Since**: 12

### NODE_LIST_CHILDREN_MAIN_SIZE

```c
NODE_LIST_CHILDREN_MAIN_SIZE = 1003007
```

**Description**

Default main axis size of the child component in **List**. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: The parameter format is [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: The parameter format is [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)</li> </ul>

**Since**: 12

### NODE_LIST_INITIAL_INDEX

```c
NODE_LIST_INITIAL_INDEX = 1003008
```

**Description**

Index of the item displayed at the beginning of the viewport when the current list is loaded for the first time. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index value of the item displayed at the start of the viewport when the current List is loaded for the first time. Default value: 0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index value of the item displayed at the start of the viewport when the current List is loaded for the first time. Default value: 0.</li> </ul>

**Since**: 12

### NODE_LIST_DIVIDER

```c
NODE_LIST_DIVIDER = 1003009
```

**Description**

Style of the divider for the list items. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: divider color, in 0xARGB format.</li> <li>.value[1].f32: stroke width of the divider, in vp.</li> <li>.value[2].f32: distance between the divider and the start of the list, in vp.</li> <li>.value[3].f32: distance between the divider and the end of the list, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: divider color, in 0xARGB format.</li> <li>.value[1].f32: stroke width of the divider, in vp.</li> <li>.value[2].f32: distance between the divider and the start of the list, in vp.</li> <li>.value[3].f32: distance between the divider and the end of the list, in vp.</li> </ul>

**Since**: 12

### NODE_LIST_SCROLL_TO_INDEX_IN_GROUP

```c
NODE_LIST_SCROLL_TO_INDEX_IN_GROUP = 1003010
```

**Description**

Scrolls to the item with the specified index in the specified list item group. When **smooth** is set to **true**, all passed items are loaded and counted in layout calculation. This may result in performance issues if a large number of items are involved. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index of the target list item group in the current list.</li> <li>.value[1].i32: index of the target list item in the list item group.</li> <li>.value[2]?.i32: whether to enable the smooth animation for scrolling to the item with the specified index. The value <b>1</b> means to enable the animation, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.value[3]?.i32: how the item to scroll to is aligned with the container. The parameter type is [ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment). The default value is <b>ARKUI_SCROLL_ALIGNMENT_START</b>.</li> </ul>

**Since**: 15

### NODE_LIST_LANES

```c
NODE_LIST_LANES = 1003011
```

**Description**

Number of lanes in the list. (The number of columns is used when the list is scrolled vertically, and the number of rows is used when the list is scrolled horizontally.) This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: number of lanes in the list. If the maximum and minimum lane widths are set, setting the number of lanes will not take effect.</li> <li>.value[1]?.f32: minimum lane width, in vp.</li> <li>.value[2]?.f32: maximum column width, in vp.</li> <li>.value[3]?.f32: lane spacing, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: number of lanes in the list.</li> <li>.value[1].f32: minimum lane width, in vp.</li> <li>.value[2].f32: maximum column width, in vp.</li> <li>.value[3].f32: lane spacing, in vp.</li> </ul>

**Since**: 15

### NODE_LIST_SCROLL_SNAP_ALIGN

```c
NODE_LIST_SCROLL_SNAP_ALIGN = 1003012
```

**Description**

Alignment mode for scroll snapping in the **List** component. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode for the list snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign). The default value is <b>ARKUI_SCROLL_SNAP_ALIGN_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode for the list snap position. The parameter type is [ArkUI_ScrollSnapAlign](capi-scroll-h.md#arkui_scrollsnapalign).</li> </ul>

**Since**: 15

### NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_LIST_MAINTAIN_VISIBLE_CONTENT_POSITION = 1003013
```

**Description**

Whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **List** component. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the <b>List</b> component. The value <b>0</b> means not to maintain the visible content's position, and <b>1</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the <b>List</b> component. The value <b>0</b> means not to maintain the visible content's position, and <b>1</b> means the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 15

### NODE_LIST_STACK_FROM_END

```c
NODE_LIST_STACK_FROM_END = 1003014
```

**Description**

Whether the **List** component starts layout from the end. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the <b>List</b> component starts layout from the end. The value <b>0</b> means layout starts from the top, and <b>1</b> means layout starts from the end. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the <b>List</b> component starts layout from the end. The value <b>0</b> means layout starts from the top, and <b>1</b> means layout starts from the end. The default value is <b>0</b>.</li> </ul>

**Since**: 19

### NODE_LIST_FOCUS_WRAP_MODE

```c
NODE_LIST_FOCUS_WRAP_MODE = 1003015
```

**Description**

Focus wrap mode of the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: focus wrap mode of the <b>List</b> component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: focus wrap mode of the <b>List</b> component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).</li> </ul>

**Since**: 20

### NODE_LIST_SYNC_LOAD

```c
NODE_LIST_SYNC_LOAD = 1003016
```

**Description**

Whether the **List** component loads child nodes synchronously. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the <b>List</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the <b>List</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul>

**Since**: 20

### NODE_LIST_SCROLL_SNAP_ANIMATION_SPEED

```c
NODE_LIST_SCROLL_SNAP_ANIMATION_SPEED = 1003017
```

**Description**

Scroll snap animation speed for the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: scroll snap animation speed for the <b>List</b> component. The parameter type is [ArkUI_ScrollSnapAnimationSpeed](capi-scroll-h.md#arkui_scrollsnapanimationspeed). Default value: <b>ARKUI_SCROLL_SNAP_ANIMATION_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: scroll snap animation speed for the <b>List</b> component. The parameter type is [ArkUI_ScrollSnapAnimationSpeed](capi-scroll-h.md#arkui_scrollsnapanimationspeed).</li> </ul>

**Since**: 22

### NODE_LIST_LANES_ITEMFILLPOLICY

```c
NODE_LIST_LANES_ITEMFILLPOLICY = 1003018
```

**Description**

Responsive lane layout policy of the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1]?.f32: column spacing. unit: vp. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1].f32: column spacing. unit: vp.</li> </ul>

**Since**: 22

### NODE_LIST_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING

```c
NODE_LIST_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1003019
```

**Description**

Whether the **List** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support empty branch rendering in lazy loading mode. <b>0</b>: Disable empty branch support. Empty branches will not be rendered. <b>1</b>: Enable empty branch support. Empty branches will be rendered as placeholder items. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether empty branch rendering is enabled. <b>0</b>: Disabled. <b>1</b>: Enabled.</li> </ul>

**Since**: 23

### NODE_LIST_BACK_PRESS_BEHAVIOR

```c
NODE_LIST_BACK_PRESS_BEHAVIOR = 1003020
```

**Description**

Behavior of the system back button for the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to collapse the scroll menu when the back button is clicked. 0: no; 1: yes. Default value: 1.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether to collapse the scroll menu when the back button is clicked. 0: no; 1: yes.</li> </ul>

**Since**: 26.0.0

### NODE_LIST_ENABLE_EDIT_MODE

```c
NODE_LIST_ENABLE_EDIT_MODE = 1003021
```

**Description**

Whether to enable the edit mode for the **List** component. After the edit mode is enabled, the check box is displayed by default, and users can swipe with their fingers to select multiple items. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the <b>List</b> component enables edit mode. <b>0</b>: Not editable. <b>1</b>: Editable. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the <b>List</b> component enables edit mode. <b>0</b>: Not editable. <b>1</b>: Editable.</li> </ul>

**Since**: 26.0.0

### NODE_LIST_EDIT_MODE_OPTIONS

```c
NODE_LIST_EDIT_MODE_OPTIONS = 1003022
```

**Description**

Edit mode options of the **List** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether List component uses default multi-selection style. When using default multi-selection style, List displays checkboxes after entering edit mode. 0: Do not use default style, 1: Use default style. Default value: 1</li> <li>.value[1].i32: Whether List component enables two-finger swipe multi-selection. This parameter takes effect after registering [NODE_LIST_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype) event callback. 0: Two-finger swipe gesture cannot make List enter edit mode, but after entering edit mode through other means, single-finger swipe multi-selection in edit mode is not affected. 1: Two-finger swipe gesture can make List enter edit mode from non-edit mode and perform swipe multi-selection. Default value: 1</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether List component uses default multi-selection style. 0: Do not use default style, 1: Use default style.</li> <li>.value[1].i32: Whether List component enables two-finger swipe multi-selection. 0: Not enabled, 1: Enabled.</li> </ul>

**Since**: 26.0.0

### NODE_LIST_ITEM_SWIPE_ACTION

```c
NODE_LIST_ITEM_SWIPE_ACTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM
```

**Description**

Swipe-out component of **ListItem**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Construct using the ArkUI_ListitemSwipeActionOption object.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Construct using the ArkUI_ListitemSwipeActionOption object.</li> </ul>

**Since**: 12

### NODE_LIST_ITEM_GROUP_SET_HEADER

```c
NODE_LIST_ITEM_GROUP_SET_HEADER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LIST_ITEM_GROUP
```

**Description**

Header component of **ListItemGroup**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object to be used as the header of the list item group.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object to be used as the header of the list item group.</li> </ul>

**Since**: 12

### NODE_LIST_ITEM_GROUP_SET_FOOTER

```c
NODE_LIST_ITEM_GROUP_SET_FOOTER
```

**Description**

Footer component of **ListItemGroup**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object to be used as the footer of the list item group.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object to be used as the footer of the list item group.</li> </ul>

**Since**: 12

### NODE_LIST_ITEM_GROUP_SET_DIVIDER

```c
NODE_LIST_ITEM_GROUP_SET_DIVIDER
```

**Description**

Style of the divider for the list items. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the divider, in 0xARGB format.</li> <li>.value[1].f32: stroke width of the divider, in vp.</li> <li>.value[2].f32: distance between the divider and the start of the list, in vp.</li> <li>.value[3].f32: distance between the divider and the end of the list, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the divider, in 0xARGB format.</li> <li>.value[1].f32: stroke width of the divider, in vp.</li> <li>.value[2].f32: distance between the divider and the start of the list, in vp.</li> <li>.value[3].f32: distance between the divider and the end of the list, in vp.</li> </ul>

**Since**: 12

### NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE

```c
NODE_LIST_ITEM_GROUP_CHILDREN_MAIN_SIZE = 1005003
```

**Description**

Default main axis size of the **ListItemGroup** child components. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: The parameter format is [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: The parameter format is [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)</li> </ul>

**Since**: 12

### NODE_LIST_ITEM_GROUP_NODE_ADAPTER

```c
NODE_LIST_ITEM_GROUP_NODE_ADAPTER = 1005004
```

**Description**

Adapter of the ListItemGroup component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: ArkUI_NodeAdapter object as the adapter.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: ArkUI_NodeAdapter object.</li> </ul>

**Since**: 15

### NODE_REFRESH_REFRESHING

```c
NODE_REFRESH_REFRESHING = MAX_NODE_SCOPE_NUM * ARKUI_NODE_REFRESH
```

**Description**

Whether the component is being refreshed. This attribute can be set and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is 1 or 0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is 1 or 0.</li> </ul>

**Since**: 12

### NODE_REFRESH_CONTENT

```c
NODE_REFRESH_CONTENT
```

**Description**

Custom content in the pull-down area. This attribute can be set and reset as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> </ul>

**Since**: 12

### NODE_REFRESH_PULL_DOWN_RATIO

```c
NODE_REFRESH_PULL_DOWN_RATIO = 1009002
```

**Description**

Pull-down follow ratio. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: pull-down hand coefficient, valid value between 0 and 1.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: pull-down hand coefficient, valid value between 0 and 1.</li> </ul>

**Since**: 12

### NODE_REFRESH_OFFSET

```c
NODE_REFRESH_OFFSET = 1009003
```

**Description**

Pull-down offset that triggers refresh. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: pull-down offset, in vp. The default value is <b>64vp</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: pull-down offset, in vp. The default value is <b>64vp</b>.</li> </ul>

**Since**: 12

### NODE_REFRESH_PULL_TO_REFRESH

```c
NODE_REFRESH_PULL_TO_REFRESH = 1009004
```

**Description**

Whether to initiate a refresh when the pull-down distance exceeds the value of refreshOffset. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to initiate a refresh. The value <b>true</b> means to initiate a refresh, and <b>false</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to initiate a refresh. The value <b>1</b> means to initiate a refresh, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_REFRESH_MAX_PULL_DOWN_DISTANCE

```c
NODE_REFRESH_MAX_PULL_DOWN_DISTANCE = 1009005
```

**Description**

Maximum pull-down distance for refreshing. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum pull-down distance, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum pull-down distance, in vp.</li> </ul>

**Since**: 20

### NODE_REFRESH_PULL_UP_TO_CANCEL_REFRESH

```c
NODE_REFRESH_PULL_UP_TO_CANCEL_REFRESH = 1009006
```

**Description**

Whether to enable the pull-up-to-cancel gesture for refreshing operations. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the pull-up gesture cancels refresh. The value <b>1</b> means that the pull-up gesture cancels refresh, and <b>0</b> means the opposite. Default value: <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the pull-up gesture cancels refresh. The value <b>1</b> means that the pull-up gesture cancels refresh, and <b>0</b> means the opposite.</li> </ul>

**Since**: 23

### NODE_WATER_FLOW_LAYOUT_DIRECTION

```c
NODE_WATER_FLOW_LAYOUT_DIRECTION = MAX_NODE_SCOPE_NUM * ARKUI_NODE_WATER_FLOW
```

**Description**

Main axis direction of the **WaterFlow** component layout. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: main axis direction. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: main axis direction. The parameter type is [ArkUI_FlexDirection](capi-layout-h.md#arkui_flexdirection).</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_COLUMN_TEMPLATE

```c
NODE_WATER_FLOW_COLUMN_TEMPLATE
```

**Description**

Number of columns in the water flow layout. If this attribute is not set, one column is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4. You can use columnsTemplate('repeat(auto-fill,track-size)') to automatically calculate the number of columns based on the specified column width (using **track-size**). **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: number of columns in the layout.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: number of columns in the layout.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_ROW_TEMPLATE

```c
NODE_WATER_FLOW_ROW_TEMPLATE
```

**Description**

Number of rows in the water flow layout. If this attribute is not set, one row is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4. You can use rowsTemplate('repeat(auto-fill,track-size)') to automatically calculate the number of rows based on the specified row height (using **track-size**). **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: number of rows in the layout.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: number of rows in the layout.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_COLUMN_GAP

```c
NODE_WATER_FLOW_COLUMN_GAP
```

**Description**

Gap between columns. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: gap between columns, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: gap between columns, in vp.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_ROW_GAP

```c
NODE_WATER_FLOW_ROW_GAP
```

**Description**

Gap between rows. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: gap between lines, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: gap between lines, in vp.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_SECTION_OPTION

```c
NODE_WATER_FLOW_SECTION_OPTION
```

**Description**

Water flow section configuration. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: An index calculated from 0 is converted to an integer, indicating that you want to start changing the position of the group.</li> <li>.object: [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) object.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) object.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_NODE_ADAPTER

```c
NODE_WATER_FLOW_NODE_ADAPTER
```

**Description**

Adapter of the WaterFlow component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: ArkUI_NodeAdapter object as the adapter.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_CACHED_COUNT

```c
NODE_WATER_FLOW_CACHED_COUNT
```

**Description**

Number of cached items in the adapter of the WaterFlow component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of cached items in the water flow adapter.</li> <li>.value[1]?.i32: whether the cached items will be displayed. <b>0</b>: not displayed, <b>1</b>: displayed. Default value: <b>0</b>. This parameter is supported since API version 16.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of cached items in the water flow adapter.</li> <li>.value[1].i32: whether the cached items will be displayed. <b>0</b>: not displayed, <b>1</b>: displayed. Default value: <b>0</b>. This parameter is supported since API version 16.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_FOOTER

```c
NODE_WATER_FLOW_FOOTER
```

**Description**

Custom footer for the **WaterFlow** component. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Parameter type [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_SCROLL_TO_INDEX

```c
NODE_WATER_FLOW_SCROLL_TO_INDEX
```

**Description**

Scroll to the specified index. When activating the smooth animation, all items passed through will be loaded and layout calculated, which can lead to performance issues when loading a large number of items.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The index value of the target element to be slid to in the current container.</li> <li>.value[1].i32: Set whether there is an action when sliding to the index value of a list item in the list, where 1 indicates an action and 0 indicates no action. This parameter is optional, default value is 0.</li> <li>.value[2].i32: Specify the alignment of the sliding element with the current container. The parameter type is [ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment). This parameter is optional, default value is </b>ARKUI_SCROLL_ALIGNMENT_START</b>.</li> <li>.value[3].f32: Extra offset after scrolling to a specified index, in vp. This parameter is optional, the default value is <b>0</b>. If value[3] is positive, it will offset further towards the bottom. If value[3] is negative, it will offset further towards the top. This parameter is supported since API version 23.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE

```c
NODE_WATER_FLOW_ITEM_CONSTRAINT_SIZE
```

**Description**

Size constraints to apply to water flow items, constraining the size range of the child component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum width, in vp.</li> <li>.value[1].f32: maximum width, in vp.</li> <li>.value[2].f32: minimum height, in vp.</li> <li>.value[3].f32: maximum height, in vp.</li> </ul>

**Since**: 12

### NODE_WATER_FLOW_LAYOUT_MODE

```c
NODE_WATER_FLOW_LAYOUT_MODE
```

**Description**

Layout mode for the **WaterFlow** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: waterflow layout mode. The parameter type is [ArkUI_WaterFlowLayoutMode](capi-water-flow-h.md#arkui_waterflowlayoutmode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: waterflow layout mode. The parameter type is [ArkUI_WaterFlowLayoutMode](capi-water-flow-h.md#arkui_waterflowlayoutmode).</li> </ul>

**Since**: 18

### NODE_WATER_FLOW_SYNC_LOAD

```c
NODE_WATER_FLOW_SYNC_LOAD = 1010012
```

**Description**

Whether the **WaterFlow** component loads child nodes synchronously. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the <b>WaterFlow</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the <b>WaterFlow</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul>

**Since**: 20

### NODE_WATER_FLOW_COLUMN_TEMPLATE_ITEMFILLPOLICY

```c
NODE_WATER_FLOW_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1010013
```

**Description**

Responsive column layout policy of the **WaterFlow** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> </ul>

**Since**: 22

### NODE_WATER_FLOW_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING

```c
NODE_WATER_FLOW_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1010014
```

**Description**

Whether the **WaterFlow** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support empty branch rendering in lazy loading mode. <b>0</b>: Disable empty branch support. Empty branches will not be rendered. <b>1</b>: Enable empty branch support. Empty branches will be rendered as placeholder items. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether empty branch rendering is enabled. <b>0</b>: Disabled. <b>1</b>: Enabled.</li> </ul>

**Since**: 26.0.0

### NODE_GRID_COLUMN_TEMPLATE

```c
NODE_GRID_COLUMN_TEMPLATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID
```

**Description**

Number of columns in the **Grid** component. If this attribute is not set, one column is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4. You can use columnsTemplate('repeat(auto-fill,track-size)') to automatically calculate the number of columns based on the specified column width (using **track-size**). **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: number of columns in the layout.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: number of columns in the layout.</li> </ul>

**Since**: 12

### NODE_GRID_ROW_TEMPLATE

```c
NODE_GRID_ROW_TEMPLATE
```

**Description**

Number of rows or the minimum row height in the **Grid** component. If this parameter is not set, one row is used by default. This attribute can be set, reset, and obtained as required through APIs. For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4. You can use rowsTemplate('repeat(auto-fill,track-size)') to automatically calculate the number of rows based on the specified row height (using **track-size**). **repeat**<br>and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: number of rows in the layout.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: number of rows in the layout.</li> </ul>

**Since**: 12

### NODE_GRID_COLUMN_GAP

```c
NODE_GRID_COLUMN_GAP
```

**Description**

Gap between columns. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: gap between columns, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: gap between columns, in vp.</li> </ul>

**Since**: 12

### NODE_GRID_ROW_GAP

```c
NODE_GRID_ROW_GAP
```

**Description**

Gap between rows. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: gap between lines, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: gap between lines, in vp.</li> </ul>

**Since**: 12

### NODE_GRID_NODE_ADAPTER

```c
NODE_GRID_NODE_ADAPTER
```

**Description**

Adapter of the Grid component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: ArkUI_NodeAdapter object as the adapter.</li> </ul>

**Since**: 12

### NODE_GRID_CACHED_COUNT

```c
NODE_GRID_CACHED_COUNT
```

**Description**

Number of cached items in the adapter of the Grid component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of cached items in the grid adapter.</li> <li>.value[1].i32: whether to display cached nodes. 0 means not display, 1 means display. This parameter is optional, default value is 0. [since 26.0.0]</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of cached items in the grid adapter.</li> <li>.value[1].i32: whether to display cached nodes. 0 means not display, 1 means display. [since 26.0.0]</li> </ul>

**Since**: 12

### NODE_GRID_FOCUS_WRAP_MODE

```c
NODE_GRID_FOCUS_WRAP_MODE = 1013006
```

**Description**

Focus wrap mode of the Grid component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: focus wrap mode of the <b>Grid</b> component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: focus wrap mode of the <b>Grid</b> component. The parameter type is [ArkUI_FocusWrapMode](capi-native-type-h.md#arkui_focuswrapmode).</li> </ul>

**Since**: 20

### NODE_GRID_SYNC_LOAD

```c
NODE_GRID_SYNC_LOAD = 1013007
```

**Description**

Whether the Grid component synchronously loads child nodes. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the <b>Grid</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the <b>Grid</b> component synchronously loads child nodes. The value <b>0</b> means loading by frames, and <b>1</b> means synchronous loading.</li> </ul>

**Since**: 20

### NODE_GRID_ALIGN_ITEMS

```c
NODE_GRID_ALIGN_ITEMS = 1013008
```

**Description**

Alignment mode of GridItem in **Grid**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment of <b>GridItem</b> components in the parent <b>Grid</b> container, specified using the [ArkUI_GridItemAlignment](capi-grid-h.md#arkui_griditemalignment) enum. The default value is <b>GRID_ITEM_ALIGNMENT_DEFAULT</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment of <b>GridItem</b> components in the parent <b>Grid</b> container, specified using the [ArkUI_GridItemAlignment](capi-grid-h.md#arkui_griditemalignment) enum.</li> </ul>

**Since**: 22

### NODE_GRID_LAYOUT_OPTIONS

```c
NODE_GRID_LAYOUT_OPTIONS = 1013009
```

**Description**

Layout options of **Grid**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: layout options, with the parameter format of [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: current [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) object.</li> </ul>

**Since**: 22

### NODE_GRID_COLUMN_TEMPLATE_ITEMFILLPOLICY

```c
NODE_GRID_COLUMN_TEMPLATE_ITEMFILLPOLICY = 1013010
```

**Description**

Responsive column layout policy of the **Grid** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> </ul>

**Since**: 22

### NODE_GRID_EDIT_MODE

```c
NODE_GRID_EDIT_MODE = 1013011
```

**Description**

Whether the **Grid** component enters the editing mode. After the component enters the editing mode, you can drag **GridItem** by using the **NODE_GRID_ON_ITEM_DRAG_START** event. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable edit mode for the <b>Grid</b> component. <b>0</b>: Disable edit mode. <b>1</b>: Enable edit mode. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable edit mode for the <b>Grid</b> component. <b>0</b>: Disable edit mode. <b>1</b>: Enable edit mode.</li> </ul>

**Since**: 23

### NODE_GRID_DRAG_ANIMATION

```c
NODE_GRID_DRAG_ANIMATION = 1013012
```

**Description**

Whether to enable the drag animation for **GridItem** in the **Grid** component. This attribute can be set, reset, and obtained as required through APIs. <br>The animation is supported only when the scrolling mode is used (only one of **NODE_GRID_ROW_TEMPLATE** and **NODE_GRID_COLUMN_TEMPLATE** is set). <br>Drag animations are only supported in grids with fixed size rules; scenarios involving spanning across rows or columns are not supported. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the drag animation for <b>GridItem</b> components in the <b>Grid</b> container. <b>0</b>: Disable the drag animation. <b>1</b>: Enable the drag animation. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable the drag animation for <b>GridItem</b> components in the <b>Grid</b> container. <b>0</b>: Disable the drag animation. <b>1</b>: Enable the drag animation.</li> </ul>

**Since**: 23

### NODE_GRID_MULTI_SELECTABLE

```c
NODE_GRID_MULTI_SELECTABLE = 1013013
```

**Description**

Whether to enable mouse-based multi-selection for the **Grid** component. This attribute can be set, reset, and obtained as required through APIs. <br>After enabled, mouse-based multi-selection within the grid will trigger the [NODE_GRID_ITEM_ON_SELECT](capi-native-node-h.md#arkui_nodeeventtype) event of the grid item. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable mouse-based multi-selection. <b>0</b>: Disable mouse-based multi-selection. <b>1</b>: Enable mouse-based multi-selection. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable mouse-based multi-selection. <b>0</b>: Disable mouse-based multi-selection. <b>1</b>: Enable mouse-based multi-selection.</li> </ul>

**Since**: 23

### NODE_GRID_SCROLL_TO_INDEX

```c
NODE_GRID_SCROLL_TO_INDEX = 1013014
```

**Description**

Scroll to the specified index. When activating the smooth animation, all items passed through will be loaded and layout calculated, which can lead to performance issues when loading a large number of items.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index value of the target element to be slid to in the current container.</li> <li>.value[1].i32: whether there is an animation when sliding to the target element, where 1 indicates an animation and 0 indicates no animation. This parameter is optional. Default value: <b>0</b>.</li> <li>.value[2].i32: alignment of the target element with the current container. The parameter type is [ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment). This parameter is optional. The default value is <b>ARKUI_SCROLL_ALIGNMENT_AUTO</b>.</li> <li>.value[3].f32: extra offset after scrolling to a specified index, in vp. This parameter is optional. The default value is <b>0</b>. If value[3] is positive, it will offset further towards the bottom. If value[3] is negative, it will offset further towards the top.</li> </ul>

**Since**: 23

### NODE_GRID_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING

```c
NODE_GRID_SUPPORT_EMPTY_BRANCH_IN_LAZY_LOADING = 1013015
```

**Description**

Whether the **Grid** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support empty branch rendering in lazy loading mode. <b>0</b>: Disable empty branch support. Empty branches will not be rendered. <b>1</b>: Enable empty branch support. Empty branches will be rendered as placeholder items. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether empty branch rendering is enabled. <b>0</b>: Disabled. <b>1</b>: Enabled.</li> </ul>

**Since**: 23

### NODE_GRID_ENABLE_EDIT_MODE

```c
NODE_GRID_ENABLE_EDIT_MODE = 1013016
```

**Description**

Whether to enable the edit mode for the **Grid** component. After the edit mode is enabled, the check box is displayed by default, and users can swipe with their fingers to select multiple items. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the <b>Grid</b> component enables edit mode. <b>0</b>: Not editable. <b>1</b>: Editable. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the <b>Grid</b> component enables edit mode. <b>0</b>: Not editable. <b>1</b>: Editable.</li> </ul>

**Since**: 26.0.0

### NODE_GRID_EDIT_MODE_OPTIONS

```c
NODE_GRID_EDIT_MODE_OPTIONS = 1013017
```

**Description**

Edit mode options of the **Grid** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the <b>Grid</b> component uses default multi-selection style. When using default multi-selection style, <b>Grid</b> displays checkboxes after entering edit mode. <b>0</b>: Do not use the default style, <b>1</b>: Use the default style. Default value: <b>1</b></li> <li>.value[1].i32: Whether the <b>Grid</b> component enables two-finger sliding multi-selection. This parameter takes effect after registering [NODE_GRID_ON_EDIT_MODE_CHANGE](capi-native-node-h.md#arkui_nodeeventtype) event callback. <b>0</b>: Two-finger sliding gesture cannot make <b>Grid</b> enter edit mode, but after entering edit mode through other means, single-finger sliding multi-selection in edit mode is not affected. <b>1</b>: Two-finger sliding gesture can make <b>Grid</b> enter edit mode from non-edit mode and perform sliding multi-selection. Default value: <b>1</b></li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the <b>Grid</b> component uses the default multi-selection style. <b>0</b>: Do not use the default style. <b>1</b>: Use the default style.</li> <li>.value[1].i32: Whether the <b>Grid</b> component enables two-finger sliding multi-selection. <b>0</b>: Disabled. <b>1</b>: Enabled.</li> </ul>

**Since**: 26.0.0

### NODE_GRID_ITEM_STYLE

```c
NODE_GRID_ITEM_STYLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_GRID_ITEM
```

**Description**

Style for **GridItem**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: style of the <b>GridItem</b> component, specified using [ArkUI_GridItemStyle](capi-grid-h.md#arkui_griditemstyle). The default value is <b>GRID_ITEM_STYLE_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: style of the <b>GridItem</b> component, specified using [ArkUI_GridItemStyle](capi-grid-h.md#arkui_griditemstyle).</li> </ul>

**Since**: 22

### NODE_GRID_ITEM_SELECTABLE

```c
NODE_GRID_ITEM_SELECTABLE = 1014001
```

**Description**

Whether **GridItem** can be selected using mouse-based multi-selection. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the <b>GridItem</b> component can be selected using mouse-based multi-selection. <b>0</b>: not selectable. <b>1</b>: selectable. Default value: <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the <b>GridItem</b> component can be selected using mouse-based multi-selection. <b>0</b>: not selectable. <b>1</b>: selectable.</li> </ul>

**Since**: 23

### NODE_GRID_ITEM_SELECTED

```c
NODE_GRID_ITEM_SELECTED = 1014002
```

**Description**

Selection status of **GridItem**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: selected state of the <b>GridItem</b> component. <b>0</b>: not selected. <b>1</b>: selected. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: selected state of the <b>GridItem</b> component. <b>0</b>: not selected. <b>1</b>: selected.</li> </ul>

**Since**: 23

### NODE_ARC_LIST_DIGITAL_CROWN_SENSITIVITY

```c
NODE_ARC_LIST_DIGITAL_CROWN_SENSITIVITY = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_LIST
```

**Description**

Crown sensitivity of the **ArcList** component, which can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: digital crown sensitivity type. The parameter type is [ArkUI_CrownSensitivity](capi-native-type-h.md#arkui_crownsensitivity). Default value: ARKUI_CROWN_SENSITIVITY_MEDIUM</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: digital crown sensitivity type. The parameter type is [ArkUI_CrownSensitivity](capi-native-type-h.md#arkui_crownsensitivity).</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SPACE

```c
NODE_ARC_LIST_SPACE = 1019001
```

**Description**

Sets the interval between child components of ArcList in the main axis direction. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: interval between child components in the main axis direction, in vp. Default value: 0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: interval between child components in the main axis direction.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_CACHED_COUNT

```c
NODE_ARC_LIST_CACHED_COUNT = 1019002
```

**Description**

Number of cached items of the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: cache count.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: cache count.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SCROLL_TO_INDEX

```c
NODE_ARC_LIST_SCROLL_TO_INDEX = 1019003
```

**Description**

Scrolls to the list item corresponding to a specified index value. When the animation is enabled, all passed list items are loaded and counted in layout calculation. This may result in performance issues if a large number of list items are involved. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index of the target element to scroll to in the current container.</li> <li>.value[1]?.i32: whether to enable animation when scrolling to the specified index. Value 1 indicates enable and value 0 indicates disable. Default value: 0.</li> <li>.value[2]?.i32: alignment of the element scrolled to with respect to the current container. The parameter type is [ArkUI_ScrollAlignment](capi-scroll-h.md#arkui_scrollalignment). Default value: ARKUI_SCROLL_ALIGNMENT_START.</li> <li>.value[3]?.f32: additional offset. Default value: 0, unit: vp.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_CHAIN_ANIMATION

```c
NODE_ARC_LIST_CHAIN_ANIMATION = 1019004
```

**Description**

Whether to enable the chain animation effect for the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable chain animation. Value 0 means not to enable, and value 1 means to enable. Default value: 0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable chain animation.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_CHILDREN_MAIN_SIZE

```c
NODE_ARC_LIST_CHILDREN_MAIN_SIZE = 1019005
```

**Description**

Default main axis size of the **ArcList** child component. The attribute can be set and reset through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: parameter format is [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md).</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SET_HEADER

```c
NODE_ARC_LIST_SET_HEADER = 1019006
```

**Description**

Header component of **ArcList**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: use [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object as the ArcList header component.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: use [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object as the ArcList header component.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SCROLL_BAR

```c
NODE_ARC_LIST_SCROLL_BAR = 1019007
```

**Description**

Scroll bar display mode of the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: scroll bar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode). Default value: ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: scroll bar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode).</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SCROLL_BAR_COLOR

```c
NODE_ARC_LIST_SCROLL_BAR_COLOR = 1019008
```

**Description**

Scroll bar color of the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].u32: scroll bar color, in ARGB format. Default value: 0x66182431</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].u32: scroll bar color, in ARGB format.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_SCROLL_BAR_WIDTH

```c
NODE_ARC_LIST_SCROLL_BAR_WIDTH = 1019009
```

**Description**

Sets the width of the scroll bar of ArcList. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: scroll bar width, in vp. Default value: 4. Value range: if the value is less than 0, it is processed as the default value. If the value is 0, the scroll bar will not be displayed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: scroll bar width, in vp.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_ENABLE_SCROLL_INTERACTION

```c
NODE_ARC_LIST_ENABLE_SCROLL_INTERACTION = 1019010
```

**Description**

Whether the **ArcList** component supports scroll gestures. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support scroll gesture. Default value: 1. Value 1 means support, and value 0 means not support.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to support scroll gesture.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_FADING_EDGE

```c
NODE_ARC_LIST_FADING_EDGE = 1019011
```

**Description**

Edge fade effect of the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable fading edge effect. Value 0 means to disable fading edge effect, and value 1 means to enable it. Default value: 0</li> <li>.value[1]?.f32: length of the fading edge effect. Unit: vp. Default value: 32.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable fading edge effect. Value 0 means to disable fading edge effect, and value 1 means to enable it.</li> <li>.value[1].f32: length of the fading edge effect. Unit: vp.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_FRICTION

```c
NODE_ARC_LIST_FRICTION = 1019012
```

**Description**

Friction coefficient of the **ArcList** component, which can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: friction coefficient. Default value: 0.8. Value range: (0, +∞). If the value is less than or equal to 0, it is processed as the default value.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: friction coefficient.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_FLING_SPEED_LIMIT

```c
NODE_ARC_LIST_FLING_SPEED_LIMIT = 1019013
```

**Description**

Maximum initial speed of the fling animation in the **ArcList** component. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum initial velocity at the start of Fling animation. Unit: vp/s. Default value: 9000.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum initial velocity at the start of Fling animation.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_ITEM_AUTO_SCALE

```c
NODE_ARC_LIST_ITEM_AUTO_SCALE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_LIST_ITEM
```

**Description**

Whether to enable automatic scaling for **ArcListItem**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable auto scale. Value 0 means not to enable, and value 1 means to enable. Default value: 1.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable auto scale.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_LIST_ITEM_SWIPE_ACTION

```c
NODE_ARC_LIST_ITEM_SWIPE_ACTION = 1020001
```

**Description**

Swipe-out component of **ArcListItem**. This attribute can be set and reset as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: use [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) object to construct.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_SCROLL_BAR_BIND_SCROLLABLE

```c
NODE_ARC_SCROLL_BAR_BIND_SCROLLABLE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SCROLL_BAR
```

**Description**

Scrollable component bound to **ArcScrollBar**. This attribute can be set, reset, and obtained as required through APIs. <br>The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: use [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object as the scrollable component bound by the scroll bar.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: use [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) object as the scrollable component bound by the scroll bar.</li> </ul>

**Since**: 26.0.0

### NODE_ARC_SCROLL_BAR_DISPLAY_MODE

```c
NODE_ARC_SCROLL_BAR_DISPLAY_MODE = 1021001
```

**Description**

Sets the scroll bar status of ArcScrollBar. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: scroll bar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode). Default value: ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: scroll bar status. The parameter type is [ArkUI_ScrollBarDisplayMode](capi-scroll-h.md#arkui_scrollbardisplaymode).</li> </ul>

**Since**: 26.0.0


