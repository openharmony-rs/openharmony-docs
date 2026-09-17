# Navigation Related Components

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_ARC_ALPHABET_INDEXER_EVENT_ON_SELECT

```c
NODE_ARC_ALPHABET_INDEXER_EVENT_ON_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_ALPHABET_INDEXER
```

**Description**

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_ARC_ALPHABET_INDEXER</b> instance changes.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 26.1.0

### NODE_SWIPER_EVENT_ON_CHANGE

```c
NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER
```

**Description**

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_SWIPER</b> instance changes.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_ANIMATION_START

```c
NODE_SWIPER_EVENT_ON_ANIMATION_START
```

**Description**

Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance starts.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains five parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li><br><li>ArkUI_NodeComponentEvent.data[2].f32: offset of the currently displayed element relative to the<br>start position of the swiper along the main axis.</li><br><li>ArkUI_NodeComponentEvent.data[3].f32: offset of the target element relative to the start position<br>of the swiper along the main axis.</li><br><li>ArkUI_NodeComponentEvent.data[4].f32: hands-off velocity.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_ANIMATION_END

```c
NODE_SWIPER_EVENT_ON_ANIMATION_END
```

**Description**

Defines the event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance ends.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_GESTURE_SWIPE

```c
NODE_SWIPER_EVENT_ON_GESTURE_SWIPE
```

**Description**

Defines the event triggered on a frame-by-frame basis when the page is turned by a swipe in this <b>ARKUI_NODE_SWIPER</b> instance.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL

```c
NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL
```

**Description**

Define the <b>ARKUI_NODE_SWIPER</b> to listen for Swiper page slide events. Instruction: 1. If the {@link ArkUI_SwiperDisplayModeType} attribute is set to <br>ARKUI_SWIPER_DISPLAY_MODE_AUTO_LINEAR, the interface does not take effect. <br>2, circular scenario, set prevMargin and nextMargin attributes, <br>so that Swiper front and back end display the same page, the interface does not take effect. <br>3. During page sliding, the ContentDidScrollCallback callback is <br>triggered frame-by-frame for all pages in the window. <br>For example, when there are two pages in the window with subscripts 0 and 1, <br>callbacks with index values 0 and 1 are triggered twice per frame. <br>4, set the swipeByGroup parameter of the displayCount property to <br>true if at least one page in the same group is in the window, <br>A callback is triggered for all pages in the group. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains four parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: indicates the index of the Swiper component,<br>which is consistent with the index change in the onChange event.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: The index of a page in the window.</li><br><li>ArkUI_NodeComponentEvent.data[2].f32: The proportion of page movement relative to<br>the start position of the Swiper spindle (selectedIndex corresponds to the start position of the page).</li><br><li>ArkUI_NodeComponentEvent.data[3].f32: The length of the page in the axis direction.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_SELECTED

```c
NODE_SWIPER_EVENT_ON_SELECTED = 1001005
```

**Description**

Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed. This event is triggered under the following scenarios: 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning. 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or <b>NODE_SWIPER_SWIPE_TO_INDEX</b>. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently selected element.</li> </ul>

**Since**: 18

### NODE_SWIPER_EVENT_ON_UNSELECTED

```c
NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006
```

**Description**

Defines the event triggered when the selected index of the <b>ARKUI_NODE_SWIPER</b> changed. This event is triggered under the following scenarios: 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning. 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or <b>NODE_SWIPER_SWIPE_TO_INDEX</b>. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: the index of the element becomes unselected.</li> </ul>

**Since**: 18

### NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL

```c
NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007
```

**Description**

Defines the event triggered when content in the swiper component will scroll. Instructions: Before page scrolling, the </b>ContentWillScrollCallback</b> callback is invoked. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains three parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: the index value of the current child page.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: the index value of the child page that will display.</li><br><li>ArkUI_NodeComponentEvent.data[2].f32: the sliding offset of each frame. Positive numbers indicating slide backward(e.g. from index=1 to index=0), negative numbers indicating slide forward(e.g. from index=0 to index=1).</li> </ul>

**Since**: 15

### NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED

```c
NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008
```

**Description**

Defines the <b>ARKUI_NODE_SWIPER</b> scroll state change event. This event is triggered when the scroll state of the <b>Swiper</b> component changes during user dragging, during the animation phase after the user lifts their finger, or upon stopping of scrolling. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: current scroll state. The parameter type is<br>{@link ArkUI_ScrollState}.</li> </ul>

**Since**: 20

### NODE_ARC_SWIPER_EVENT_ON_CHANGE

```c
NODE_ARC_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SWIPER
```

**Description**

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_ARC_SWIPER</b> instance changes.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 26.1.0

### NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START

```c
NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START
```

**Description**

Defines the event triggered when the switching animation of this <b>ARKUI_NODE_ARC_SWIPER</b> instance starts.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains five parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li><br><li>ArkUI_NodeComponentEvent.data[2].f32: offset of the currently displayed element relative to the<br>start position of the swiper along the main axis.</li><br><li>ArkUI_NodeComponentEvent.data[3].f32: offset of the target element relative to the start position<br>of the swiper along the main axis.</li><br><li>ArkUI_NodeComponentEvent.data[4].f32: hand-off velocity.</li> </ul>

**Since**: 26.1.0

### NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END

```c
NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END
```

**Description**

Defines the event triggered when the switching animation of this <b>ARKUI_NODE_ARC_SWIPER</b> instance ends.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 26.1.0

### NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE

```c
NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE
```

**Description**

Defines the event triggered on a frame-by-frame basis when the page is turned by a swipe in this <b>ARKUI_NODE_ARC_SWIPER</b> instance.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li><br><li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 26.1.0


