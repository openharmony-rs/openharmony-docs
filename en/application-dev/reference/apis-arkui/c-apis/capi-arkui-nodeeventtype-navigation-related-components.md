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

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_ARC_ALPHABET_INDEXER</b> instance changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 26.0.1

### NODE_SWIPER_EVENT_ON_CHANGE

```c
NODE_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER
```

**Description**

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_SWIPER</b> instance changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_ANIMATION_START

```c
NODE_SWIPER_EVENT_ON_ANIMATION_START
```

**Description**

Event triggered when the switching animation of this <b>ARKUI_NODE_SWIPER</b> instance starts.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li> <li>ArkUI_NodeComponentEvent.data[2].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> <li>ArkUI_NodeComponentEvent.data[3].f32: offset of the target element relative to the start position of the swiper along the main axis.</li> <li>ArkUI_NodeComponentEvent.data[4].f32: hands-off velocity.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_ANIMATION_END

```c
NODE_SWIPER_EVENT_ON_ANIMATION_END
```

**Description**

Event triggered when the transition animation of <b>ARKUI_NODE_SWIPER</b> ends.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_GESTURE_SWIPE

```c
NODE_SWIPER_EVENT_ON_GESTURE_SWIPE
```

**Description**

Event triggered on a frame-by-frame basis when the page is turned by a swipe.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL

```c
NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL
```

**Description**

Event triggered when the Swiper page scrolls, which is listened by <b>ARKUI_NODE_SWIPER</b>. Instructions: 1. This API does not work when <b>NODE_SWIPER_DISPLAY_COUNT</b> is set to <b>'auto'</b>. 2. This API does not work when <b>prevMargin</b> and <b>nextMargin</b> are set in such a way that the <b>Swiper</b> frontend and backend display the same page during loop playback. 3. During page scrolling, the <b>ContentDidScrollCallback</b> callback is invoked for all pages in the viewport on a frame-by-frame basis. For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame. 4. When the <b>swipeByGroup</b> parameter of the <b>displayCount</b> attribute is set to <b>true</b>, the callback is invoked for all pages in a group if any page in the group is within the viewport. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the <b>Swiper</b> component, which is the same as the index in the onChange event.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: index of a page in the viewport.</li> <li>ArkUI_NodeComponentEvent.data[2].f32: position of the page relative to the start position of the <b>Swiper</b> component's main axis (start position of the page corresponding to <b>selectedIndex</b>).</li> <li>ArkUI_NodeComponentEvent.data[3].f32: length of the page in the main axis direction.</li> </ul>

**Since**: 12

### NODE_SWIPER_EVENT_ON_SELECTED

```c
NODE_SWIPER_EVENT_ON_SELECTED = 1001005
```

**Description**

Event triggered when the selection changes in the <b>ARKUI_NODE_SWIPER</b> component. This event is triggered in the following scenarios: 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning. 2. When the page is changed programmatically using either <b>NODE_SWIPER_INDEX</b> or <b>NODE_SWIPER_SWIPE_TO_INDEX</b>. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently selected element.</li> </ul>

**Since**: 18

### NODE_SWIPER_EVENT_ON_UNSELECTED

```c
NODE_SWIPER_EVENT_ON_UNSELECTED = 1001006
```

**Description**

Event triggered when the selection changes in the <b>ARKUI_NODE_SWIPER</b> component. This event is triggered when any of the following occurs: 1. When the page switching animation starts after the user lifts their finger after swiping and the swipe meets the threshold for page turning. 2. When the page is changed using either <b>NODE_SWIPER_INDEX</b> or <b>NODE_SWIPER_SWIPE_TO_INDEX</b>. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the element that is about to be hidden.</li> </ul>

**Since**: 18

### NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL

```c
NODE_SWIPER_EVENT_ON_CONTENT_WILL_SCROLL = 1001007
```

**Description**

Event for swipe behavior interception in the <b>ARKUI_NODE_SWIPER</b> component. Usage: The <b>ContentWillScrollCallback</b> callback is triggered before a swipe operation. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element. The value of this parameter is used as the result of the interception event. The value <b>0</b> indicates that interception is performed; the value <b>1</b> indicates that interception is not performed.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li> <li>ArkUI_NodeComponentEvent.data[2].f32: swipe offset per frame. A positive value indicates swiping backward (for example, from index=1 to index=0), and a negative value indicates swiping forward (for example, from index=0 to index=1).</li> </ul>

**Since**: 15

### NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED

```c
NODE_SWIPER_EVENT_ON_SCROLL_STATE_CHANGED = 1001008
```

**Description**

<b>ARKUI_NODE_SWIPER</b> scroll state change event. This event is triggered under the following scenarios: The <b>Swiper</b> transitions between three scroll states: scrolling with the touch, animating after release, and stopped. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: current scroll state. The parameter type is [ArkUI_ScrollState](capi-scroll-h.md#arkui_scrollstate).</li> </ul>

**Since**: 20

### NODE_ARC_SWIPER_EVENT_ON_CHANGE

```c
NODE_ARC_SWIPER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SWIPER
```

**Description**

Defines the event triggered when the index of the currently displayed element of this <b>ARKUI_NODE_ARC_SWIPER</b> instance changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START

```c
NODE_ARC_SWIPER_EVENT_ON_ANIMATION_START
```

**Description**

Triggered when the transition animation of the arc swipe container (<b>ARKUI_NODE_ARC_SWIPER</b>) starts.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: index of the target element to switch to.</li> <li>ArkUI_NodeComponentEvent.data[2].f32: offset of the currently displayed element relative to the start position of the <b>Swiper</b> component along the main axis.</li> <li>ArkUI_NodeComponentEvent.data[3].f32: offset of the target element relative to the start position of the <b>Swiper</b> component along the main axis.</li> <li>ArkUI_NodeComponentEvent.data[4].f32: hands-off velocity.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END

```c
NODE_ARC_SWIPER_EVENT_ON_ANIMATION_END
```

**Description**

Defines the event triggered when the switching animation of this <b>ARKUI_NODE_ARC_SWIPER</b> instance ends.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE

```c
NODE_ARC_SWIPER_EVENT_ON_GESTURE_SWIPE
```

**Description**

Defines the event triggered on a frame-by-frame basis when the page is turned by a swipe in this <b>ARKUI_NODE_ARC_SWIPER</b> instance.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: index of the currently displayed element.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: offset of the currently displayed element relative to the start position of the swiper along the main axis.</li> </ul>

**Since**: 26.0.1


