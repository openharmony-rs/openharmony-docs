# 交互事件

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TOUCH_EVENT

```c
NODE_TOUCH_EVENT = 0
```

**描述：**

Defines the gesture event type.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 12

### NODE_EVENT_ON_APPEAR

```c
NODE_EVENT_ON_APPEAR
```

**描述：**

Defines the mount event.<br> This event is triggered when the component is mounted and displayed. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_EVENT_ON_DISAPPEAR

```c
NODE_EVENT_ON_DISAPPEAR
```

**描述：**

Defines the unmount event.<br> This event is triggered when the component is unmounted and hidden. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_EVENT_ON_AREA_CHANGE

```c
NODE_EVENT_ON_AREA_CHANGE
```

**描述：**

Defines the area change event.<br> This event is triggered when the component's size, position, or any other attribute that may affect its display area changes. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: original width of the target element, in vp.<br>The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: original height of the target element, in vp.<br>The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[2].f32</b>: original X coordinate of the target element's upper left corner<br>relative to the parent element's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[3].f32</b>: original Y coordinate of the target element's upper left corner<br>relative to the parent element's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[4].f32</b>: original X coordinate of the target element's upper left corner<br>relative to the page's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[5].f32</b>: original Y coordinate of the target element's upper left corner<br>relative to the page's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[6].f32</b>: new width of the target element, in vp. The value is a number.</li><br><li><b>ArkUI_NodeComponentEvent.data[7].f32</b>: new height of the target element, in vp. The value is a number.</li><br><li><b>ArkUI_NodeComponentEvent.data[8].f32</b>: new X coordinate of the target element's upper left corner relative<br>to the parent element's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[9].f32</b>: new Y coordinate of the target element's upper left corner relative<br>to the parent element's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[10].f32</b>: new X coordinate of the target element's upper left corner relative<br>to the page's, in vp. The value type is number.</li><br><li><b>ArkUI_NodeComponentEvent.data[11].f32</b>: new Y coordinate of the target element's upper left corner relative to the page's, in vp. The value type is number.</li> </ul>

**起始版本：** 12

### NODE_ON_FOCUS

```c
NODE_ON_FOCUS
```

**描述：**

Defines the focus event.<br> This event is triggered when the component obtains the focus. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_ON_BLUR

```c
NODE_ON_BLUR
```

**描述：**

Defines the blur event.<br> This event is triggered when the component loses the focus. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_ON_CLICK

```c
NODE_ON_CLICK
```

**描述：**

Defines the click event.<br> This event is triggered when the component is clicked. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 12 parameters:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: X coordinate of the click relative to the upper left corner of the<br>clicked component's original area, in vp.</li><br><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: Y coordinate of the click relative to the upper left corner of the<br>clicked component's original area, in vp.</li><br><li><b>ArkUI_NodeComponentEvent.data[2].f32</b>: event timestamp. It is the interval between the time when the event<br>is triggered and the time when the system starts, in microseconds.</li><br><li><b>ArkUI_NodeComponentEvent.data[3].i32</b>: event input device. The value <b>1</b> indicates the mouse,</li><br><li><b>2</b> indicates the touchscreen, and <b>4</b> indicates the key.</li><br><li><b>ArkUI_NodeComponentEvent.data[4].f32</b>: X coordinate of the click relative to the upper left corner of the<br>application window, in vp.</li><br><li><b>ArkUI_NodeComponentEvent.data[5].f32</b>: Y coordinate of the click relative to the upper left corner of the<br>application window, in vp.</li><br><li><b>ArkUI_NodeComponentEvent.data[6].f32</b>: X coordinate of the click relative to the upper left corner of the<br>application screen, in vp.</li><br><li><b>ArkUI_NodeComponentEvent.data[7].f32</b>: Y coordinate of the click relative to the upper left corner of the application screen, in vp.</li> </ul>

**起始版本：** 12

### NODE_ON_TOUCH_INTERCEPT

```c
NODE_ON_TOUCH_INTERCEPT
```

**描述：**

Defines event interception.<br> This event is triggered when the component is touched. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 12

### NODE_EVENT_ON_VISIBLE_AREA_CHANGE

```c
NODE_EVENT_ON_VISIBLE_AREA_CHANGE
```

**描述：**

Defines the visible area change event.<br> This event is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering this event, you must set <b>NODE_VISIBLE_AREA_CHANGE_RATIO</b>. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total area<br>changes compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates a<br>decrease.</li><br><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked.</li> </ul>

**起始版本：** 12

### NODE_ON_HOVER

```c
NODE_ON_HOVER
```

**描述：**

Defines the event triggered when the mouse pointer is moved over or away from the component.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: whether the mouse pointer is hovered over the component. The value <b>1</b> indicates that the mouse pointer is hovered over the component, and <b>0</b> indicates that the mouse pointer is moved away from the component.</li> </ul>

**起始版本：** 12

### NODE_ON_MOUSE

```c
NODE_ON_MOUSE
```

**描述：**

Defines the click event.<br> This event is triggered when the component is clicked by a mouse device button or when the mouse pointer moves within the component. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 12

### NODE_EVENT_ON_ATTACH

```c
NODE_EVENT_ON_ATTACH
```

**描述：**

Defines the attach event.<br> This event is triggered when the component is attached. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_EVENT_ON_DETACH

```c
NODE_EVENT_ON_DETACH
```

**描述：**

Defines the detach event.<br> This event is triggered when the component is detached. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**起始版本：** 12

### NODE_ON_KEY_EVENT

```c
NODE_ON_KEY_EVENT = 21
```

**描述：**

Defines the event triggered when a key event occurs.<br> The callback can be triggered during interactions with a focused window using an external keyboard or other input device. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**起始版本：** 14

### NODE_ON_KEY_PRE_IME

```c
NODE_ON_KEY_PRE_IME = 22
```

**描述：**

Defines the event triggered before the input method responds to the key action.<br> If the return value of this callback is <b>true</b>, it is considered that the key event has been consumed, and subsequent event callbacks (<b>keyboardShortcut</b>, input method events, <b>onKeyEvent</b>) will be intercepted and no longer triggered. The callback can be triggered during interactions with a focused window using an external keyboard or other input device. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**起始版本：** 14

### NODE_ON_FOCUS_AXIS

```c
NODE_ON_FOCUS_AXIS = 23
```

**描述：**

Defines the event triggered when the bound component receives a focus axis event after gaining focus.<br> The event callback is triggered by interactions with a joystick and a focused component. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 15

### NODE_DISPATCH_KEY_EVENT

```c
NODE_DISPATCH_KEY_EVENT = 24
```

**描述：**

Dispatch key event on the component node.<br> When the component node receives a key event, this callback will be triggered instead of dispatching event to its children. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**起始版本：** 15

### NODE_ON_AXIS

```c
NODE_ON_AXIS = 25
```

**描述：**

Defines the event triggered when the bound component receives an axis event.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 17

### NODE_ON_CLICK_EVENT

```c
NODE_ON_CLICK_EVENT = 26
```

**描述：**

Defines the event triggered when the bound component is clicked.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>{@link ArkUI_UIInputEvent}.

**起始版本：** 18

### NODE_ON_HOVER_EVENT

```c
NODE_ON_HOVER_EVENT = 27
```

**描述：**

定义鼠标指针移至组件上方或远离组件时触发的事件。 当鼠标指针移到组件上方或远离组件时触发该事件。 当事件回调发生时，{@link ArkUI_NodeEvent}对象中的联合类型为{@link ArkUI_UIInputEvent}。 <br>

**起始版本：** 17

### NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_EVENT = 28
```

**描述：**

Sets the callback for the NODE_EVENT_ON_VISIBLE_AREA_CHANGE event, which limits the callback interval.<br> The callback is triggered when the ratio of the component's visible area to its total area is greater than or less than the threshold. Before registering the callback, you must configure the threshold and update interval using <b>NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO</b>. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: how the ratio of the component's visible area to its total area<br>changes compared to the previous one. The value <b>1</b> indicates an increase, and <b>0</b> indicates<br>a decrease.</li><br><li><b>ArkUI_NodeComponentEvent.data[1].f32</b>: ratio of the component's visible area to its total area when this callback is invoked.</li> </ul>

**起始版本：** 17

### NODE_ON_HOVER_MOVE

```c
NODE_ON_HOVER_MOVE = 29
```

**描述：**

Defines the hover event. The event is triggered when the pointer is hovered by a pen device. within the component. When the event callback occurs, the {@link ArkUI_NodeEvent} object can be obtained from the<br>{@link ArkUI_UIInputEvent} object.

**起始版本：** 15

### NODE_ON_SIZE_CHANGE

```c
NODE_ON_SIZE_CHANGE = 30
```

**描述：**

定义尺寸变化事件，当组件尺寸发生变化时会触发该事件。<br> <br>事件回调发生时，事件参数{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br><br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含四个参数：<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].f32：尺寸组件变化前的宽度。</li><br><li>ArkUI_NodeComponentEvent.data[1].f32：尺寸组件变化前的高度。</li><br><li>ArkUI_NodeComponentEvent.data[2].f32：尺寸组件变化后的宽度。</li><br><li>ArkUI_NodeComponentEvent.data[3].f32：尺寸组件变化后的高度。</li> </ul>

**起始版本：** 21

### NODE_ON_COASTING_AXIS_EVENT

```c
NODE_ON_COASTING_AXIS_EVENT = 31
```

**描述：**

Defines the coasting axis event.<br> The event is triggered when user swipes with two fingers on the touchpad, the system constructs sliding events based on the speed at the moment the fingers are lifted, according to a certain decay curve. You can listen for such events to handle the flick effect immediately after the regular axis events. When the event callback occurs, the {@link ArkUI_UIInputEvent} object can be obtained from the<br>{@link ArkUI_NodeEvent} object through [OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent).<br>And the {@link ArkUI_CoastingAxisEvent} object can be obtained from the {@link ArkUI_UIInputEvent}<br>object through {@link OH_ArkUI_UIInputEvent_GetCoastingAxisEvent}.

**起始版本：** 22

### NODE_ON_CHILD_TOUCH_TEST

```c
NODE_ON_CHILD_TOUCH_TEST = 32
```

**描述：**

Defines the pre-touch test of sub component in touch events. Called to specify how to perform the touch test on the children of this component. The event is triggered when the component is touched. When the event callback occurs, the {@link ArkUI_NodeEvent} object can be obtained from the<br>{@link ArkUI_TouchTestInfo} object.

**起始版本：** 22

### NODE_ON_DIGITAL_CROWN

```c
NODE_ON_DIGITAL_CROWN = 33
```

**描述：**

Defines the crown event. This event is triggered when the crown is rotated. When the event callback occurs, the {@link ArkUI_UIInputEvent} object can be obtained from the<br>{@link ArkUI_NodeEvent} object.

**起始版本：** 24

### NODE_ON_GESTURE_COLLECT_INTERCEPT

```c
NODE_ON_GESTURE_COLLECT_INTERCEPT = 37
```

**描述：**

This callback is invoked when the events and gestures on this node and higher-priority nodes are collected. This callback is used to intervene in the collection result of events and gestures. When the event callback occurs, the {@link ArkUI_GestureCollectInterceptInfo} object can be obtained from the<br>{@link ArkUI_NodeEvent} object.

**起始版本：** 26.0.0


