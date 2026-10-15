# Interaction Event

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TOUCH_EVENT

```c
NODE_TOUCH_EVENT = 0
```

**Description**

Defines the gesture event type.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 12

### NODE_EVENT_ON_APPEAR

```c
NODE_EVENT_ON_APPEAR
```

**Description**

Mount event. This event is triggered when the component is mounted and displayed. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_EVENT_ON_DISAPPEAR

```c
NODE_EVENT_ON_DISAPPEAR
```

**Description**

Unmount event. This event is triggered when the component is unmounted from the component tree and disappears. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_EVENT_ON_AREA_CHANGE

```c
NODE_EVENT_ON_AREA_CHANGE
```

**Description**

Component area change event. This event is triggered when the component area changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters: <ul> <li>ArkUI_NodeComponentEvent.data[0].f32</b>: original width of the target element, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[1].f32</b>: original height of the target element, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[2].f32</b>: original X coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[3].f32</b>: original Y coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[4].f32</b>: original X coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[5].f32</b>: original Y coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[6].f32</b>: new width of the target element, in vp. The value is a number.</li> <li>ArkUI_NodeComponentEvent.data[7].f32</b>: new height of the target element, in vp. The value is a number.</li> <li>ArkUI_NodeComponentEvent.data[8].f32</b>: new X coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[9].f32</b>: new Y coordinate of the target element's upper left corner relative to the parent element's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[10].f32</b>: new X coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.</li> <li>ArkUI_NodeComponentEvent.data[11].f32</b>: new Y coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.</li> </ul>

**Since**: 12

### NODE_ON_FOCUS

```c
NODE_ON_FOCUS
```

**Description**

Event of obtaining focus. This event is triggered when the component obtains the focus. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_ON_BLUR

```c
NODE_ON_BLUR
```

**Description**

Event of losing focus. This event is triggered when the component loses the focus. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_ON_CLICK

```c
NODE_ON_CLICK
```

**Description**

Click event. This event is triggered when the component is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters: <ul> <li>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the click relative to the upper left corner of the clicked component's original area, in vp.</li> <li>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the click relative to the upper left corner of the clicked component's original area, in vp.</li> <li>ArkUI_NodeComponentEvent.data[2].f32</b>: event timestamp. It is the interval between the time when the event is triggered and the time when the system starts, in microseconds.</li> <li>ArkUI_NodeComponentEvent.data[3].i32</b>: event input device. The value <b>1</b> indicates the mouse, <li>2</b> indicates the touchscreen, and <b>4</b> indicates the key.</li> <li>ArkUI_NodeComponentEvent.data[4].f32</b>: X coordinate of the click relative to the upper left corner of the application window, in vp.</li> <li>ArkUI_NodeComponentEvent.data[5].f32</b>: Y coordinate of the click relative to the upper left corner of the application window, in vp.</li> <li>ArkUI_NodeComponentEvent.data[6].f32</b>: X coordinate of the click relative to the upper left corner of the application screen, in vp.</li> <li>ArkUI_NodeComponentEvent.data[7].f32</b>: Y coordinate of the click relative to the upper left corner of the application screen, in vp.</li> </ul>

**Since**: 12

### NODE_ON_TOUCH_INTERCEPT

```c
NODE_ON_TOUCH_INTERCEPT
```

**Description**

Custom component event interception. This event is triggered when the component is touched. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 12

### NODE_EVENT_ON_VISIBLE_AREA_CHANGE

```c
NODE_EVENT_ON_VISIBLE_AREA_CHANGE
```

**Description**

Visible area change event. This event is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering the event, you need to use <b>NODE_VISIBLE_AREA_CHANGE_RATIO</b> to configure the threshold. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters: <ul> <li>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total area changes compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates a decrease.</li> <li>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked.</li> </ul>

**Since**: 12

### NODE_ON_HOVER

```c
NODE_ON_HOVER
```

**Description**

Event triggered when the mouse pointer moves over or away from the component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter: <ul> <li>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the mouse pointer is hovered over the component. The value <b>1</b> indicates that the mouse pointer is hovered over the component, and <b>0</b> indicates that the mouse pointer is moved away from the component.</li> </ul>

**Since**: 12

### NODE_ON_MOUSE

```c
NODE_ON_MOUSE
```

**Description**

Mouse event. This event is triggered when the component is clicked by a mouse device button or when the mouse pointer moves within the component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 12

### NODE_EVENT_ON_ATTACH

```c
NODE_EVENT_ON_ATTACH
```

**Description**

Attach event. This event is triggered when the component is attached to the component tree. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_EVENT_ON_DETACH

```c
NODE_EVENT_ON_DETACH
```

**Description**

Detach event. This event is triggered when the component is detached from the component tree. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_ON_KEY_EVENT

```c
NODE_ON_KEY_EVENT = 21
```

**Description**

Event triggered when a key event occurs. The callback can be triggered during interactions with a focused window using an external keyboard or other input device. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**Since**: 14

### NODE_ON_KEY_PRE_IME

```c
NODE_ON_KEY_PRE_IME = 22
```

**Description**

Event triggered before the input method responds to the key action. If the return value of this callback is <b>true</b>, the key event is considered consumed, and subsequent event callbacks (<b>keyboardShortcut</b>, input method events, <b>onKeyEvent</b>) will be intercepted and no longer triggered. The callback can be triggered during interactions with a focused window using an external keyboard or other input device. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**Since**: 14

### NODE_ON_FOCUS_AXIS

```c
NODE_ON_FOCUS_AXIS = 23
```

**Description**

Event triggered when the bound component receives a focus axis event after gaining focus. The event callback is triggered by interactions with a joystick and a focused component. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 15

### NODE_DISPATCH_KEY_EVENT

```c
NODE_DISPATCH_KEY_EVENT = 24
```

**Description**

Component key event re-dispatch event. When a component node receives a key event, this callback is triggered instead of dispatching the event to its child nodes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**Since**: 15

### NODE_ON_AXIS

```c
NODE_ON_AXIS = 25
```

**Description**

Defines the event triggered when the bound component receives an axis event.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 17

### NODE_ON_CLICK_EVENT

```c
NODE_ON_CLICK_EVENT = 26
```

**Description**

Event triggered when the bound component is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md).

**Since**: 18

### NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28
```

**Description**

Sets the callback for the NODE_EVENT_ON_VISIBLE_AREA_CHANGE event, which limits the callback interval.<br> The callback is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering the event, you need to use <b>NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO</b> to configure the threshold and update interval. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters: <ul> <li>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total area changes compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates a decrease.</li> <li>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked.</li> </ul>

**Since**: 17

### NODE_ON_HOVER_MOVE

```c
NODE_ON_HOVER_MOVE = 29
```

**Description**

Hover event. This event is triggered when the stylus pointer hovers over the component. When the event callback occurs, the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object can be obtained from the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object.

**Since**: 15

### NODE_ON_SIZE_CHANGE

```c
NODE_ON_SIZE_CHANGE = 30
```

**Description**

Size change event. This event is triggered when the component size changes. <br>When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains four parameters: <ul> <li>ArkUI_NodeComponentEvent.data[0].f32</b>: width of the component before the size change.</li> <li>ArkUI_NodeComponentEvent.data[1].f32</b>: height of the component before the size change.</li> <li>ArkUI_NodeComponentEvent.data[2].f32</b>: width of the component after the size change.</li> <li>ArkUI_NodeComponentEvent.data[3].f32</b>: height of the component after the size change.</li> </ul>

**Since**: 21

### NODE_ON_COASTING_AXIS_EVENT

```c
NODE_ON_COASTING_AXIS_EVENT = 31
```

**Description**

Coasting axis event. When a user slides two fingers on the touchpad for a certain distance and quickly lifts the fingers, the system continuously constructs the event based on the speed at which the fingers are lifted and a certain attenuation curve. You can listen to this type of events to handle the fling effect after the normal scrolling axis event. When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object through [OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent). And the [ArkUI_CoastingAxisEvent](capi-arkui-eventmodule-arkui-coastingaxisevent.md) object can be obtained from the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object through [OH_ArkUI_UIInputEvent_GetCoastingAxisEvent](capi-ui-input-event-h.md#oh_arkui_uiinputevent_getcoastingaxisevent).

**Since**: 22

### NODE_ON_CHILD_TOUCH_TEST

```c
NODE_ON_CHILD_TOUCH_TEST = 32
```

**Description**

Pre-touch test event of a child component. This event is called to specify how to perform a touch test on the child component of the current component. This event is triggered when the component is touched. When the event callback occurs, you can obtain the [ArkUI_TouchTestInfo](capi-arkui-eventmodule-arkui-touchtestinfo.md) object from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object by calling [OH_ArkUI_NodeEvent_GetTouchTestInfo](capi-native-node-h.md#oh_arkui_nodeevent_gettouchtestinfo).

**Since**: 22

### NODE_ON_DIGITAL_CROWN

```c
NODE_ON_DIGITAL_CROWN = 33
```

**Description**

Defines the crown event. This event is triggered when the crown is rotated. When the event callback occurs, the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 24

### NODE_ON_GESTURE_COLLECT_INTERCEPT

```c
NODE_ON_GESTURE_COLLECT_INTERCEPT = 37
```

**Description**

This callback is invoked when the events and gestures on this node and higher-priority nodes are collected. This callback is used to intervene in the collection result of events and gestures. <br> When the event callback occurs, the [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 26.0.0


