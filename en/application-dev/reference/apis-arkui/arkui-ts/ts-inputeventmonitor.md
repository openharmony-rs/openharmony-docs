# Global Basic Input Event Listening
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-03T02:45:44.025Z pushedAt=2026-11-13T01:06:00.015Z nl=1 -->

Listens for basic input events and uniformly intercepts and filters input events before they are dispatched by [UIContext](../arkts-apis-uicontext-uicontext.md). This is applicable to scenarios that require unified control before events reach components, such as global shortcut key handling, input security filtering, and unified blocking of mouse, touch, or key input on specific pages. For usage examples, see [addLocalInputEventMonitor](../arkts-apis-uicontext-uicontext.md#addlocalinputeventmonitor).

**Since**: 26.0.0

## InputEventMonitor

Defines an identifier object for an input event listener.

This object is created and returned by the system and serves as the unique identifier of the listener.

> **NOTE**
>
> - The object is an empty object that does not contain any accessible members.
> - Developers cannot construct this object directly. It can only be obtained by registering through the [addLocalInputEventMonitor](../arkts-apis-uicontext-uicontext.md#addlocalinputeventmonitor) API.
> - It is used to verify the identity when subsequently calling [removeLocalInputEventMonitor](../arkts-apis-uicontext-uicontext.md#removelocalinputeventmonitor) to unregister.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

## InputEventListener

type InputEventListener = (event: RawInputEventWrapper) => InputEventInterceptResult

Defines the callback function type for the input event listener.

> **NOTE**
>
> - RawInputEventWrapper is an abstract class. Developers cannot create an instance using the `new` operator.
> - The system automatically creates an instance when an event is triggered and passes it to the callback function through this parameter.
> - The current callback parameter `event` encapsulates only the following raw input event types: [MouseEvent](ts-universal-mouse-key.md#mouseevent), [TouchEvent](ts-universal-events-touch.md#touchevent), and [KeyEvent](ts-universal-events-key.md#keyevent). Developers can obtain the corresponding event object through [asMouseEvent](#asmouseevent), [asTouchEvent](#astouchevent), and [asKeyEvent](#askeyevent).
> - Do not perform time-consuming operations (such as complex computation or network requests) in the callback, as this may cause the application to freeze.
> - The listener executes synchronously on the UI thread and directly blocks the event processing flow. It is recommended to perform only local condition checks and simple computations that do not block the UI thread.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | ---- |
| event | [RawInputEventWrapper](#rawinputeventwrapper) | Yes | Input event wrapper, automatically created and passed by the system. Developers do not need to create it manually. |

**Return value**

| Type | Description |
| -------- | ---- |
| [InputEventInterceptResult](#inputeventinterceptresult) | Event interception result. |

## InputEventInterceptResult

Defines the input event intercept result API, which is used by the listener callback [InputEventListener](#inputeventlistener) to return a decision on whether to block event propagation.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | ---- | ---- | ---- |
| action | [InputEventInterceptAction](ts-appendix-enums.md#inputeventinterceptaction) | No | No | Input event interception action.<br>CONTINUE: allows the event to continue being delivered to the UI framework.<br>BLOCK: blocks the event from being delivered to the UI framework. |

## RawInputEventWrapper

Defines the raw input event wrapper class.

Provides a unified API for accessing different types of input events, ensuring type safety and backward compatibility.

This class encapsulates raw **MouseEvent**, **TouchEvent**, or **KeyEvent** objects and provides access through type-safe methods.

This class is abstract, and you cannot create its instances. The system automatically creates an instance when an input event listener is triggered and passes the instance to the callback function.

**Since**: 26.0.0

> **NOTE**
>
> Since the listener is executed before events are dispatched to specific components, the following fields and methods in the event will not provide valid values: the target object [target](ts-universal-events-click.md#eventtarget8), coordinates relative to the component ([x](ts-universal-mouse-key.md#attributes), [y](ts-universal-mouse-key.md#attributes)), the [getCurrentLocalPosition](ts-universal-events-touch.md#getcurrentlocalposition) and [stopPropagation](ts-universal-events-touch.md#touchevent) methods, the [preventDefault](ts-universal-events-touch.md#touchevent) and [getHistoricalPoints](ts-universal-events-touch.md#gethistoricalpoints10) methods of **TouchEvent**, and the [metaKey](ts-universal-events-key.md#attributes) property and [getModifierKeyState](ts-universal-events-key.md#getmodifierkeystate12) method of **KeyEvent**.

**Example**

```ts
const listener: InputEventListener = (wrapper: RawInputEventWrapper) => {
  // Use type judgment and obtain the event object.
  if (wrapper.isMouseEvent()) {
    const mouseEvent = wrapper.asMouseEvent()!;
    console.info(`Mouse: (${mouseEvent.windowX}, ${mouseEvent.windowY})`);
    return { action: InputEventInterceptAction.CONTINUE };
  }
  if (wrapper.isTouchEvent()) {
    const touchEvent = wrapper.asTouchEvent()!;
    console.info(`Touch: ${touchEvent.touches.length} points`);
    return { action: InputEventInterceptAction.CONTINUE };
  }
  if (wrapper.isKeyEvent()) {
    const keyEvent = wrapper.asKeyEvent()!;
    console.info(`Key: ${keyEvent.keyText}`);
    return { action: InputEventInterceptAction.CONTINUE };
  }
  return { action: InputEventInterceptAction.CONTINUE };
};
```

### isMouseEvent

isMouseEvent(): boolean

Checks whether this is a mouse event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| boolean | Whether this is a mouse event. Returns **true** if it is a mouse event; returns **false** otherwise. |

### isTouchEvent

isTouchEvent(): boolean

Checks whether it is a touch event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| boolean | Whether it is a touch event. The value **true** is returned if it is a touch event; otherwise, **false** is returned. |

### isKeyEvent

isKeyEvent(): boolean

Determines whether this is a key event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| boolean | Whether this is a key event. **true** if this is a key event; **false** otherwise. |

### asMouseEvent

asMouseEvent(): MouseEvent \| null

Obtains the mouse event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| [MouseEvent](ts-universal-mouse-key.md#mouseevent) \| null | Obtains the mouse event. If the event is a mouse event, the event object is returned; otherwise, null is returned. Since the listener is executed before the event is dispatched to a specific component, fields such as the target object and the coordinates x and y relative to the component in the returned MouseEvent cannot provide valid values. |

### asTouchEvent

asTouchEvent(): TouchEvent \| null

Obtains the touch event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| [TouchEvent](ts-universal-events-touch.md#touchevent) \| null | Obtains the touch event. If it is a touch event, returns the event object; otherwise, returns null. Since the listener is executed before the event is dispatched to a specific component, methods such as getCurrentLocalPosition, stopPropagation, preventDefault, and getHistoricalPoints in the returned TouchEvent cannot provide valid values. |

### asKeyEvent

asKeyEvent(): KeyEvent \| null

Obtains the key event.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | ---- |
| [KeyEvent](ts-universal-events-key.md#keyevent) \| null | Obtains the key event. If it is a key event, returns the event object; otherwise, returns null. Since the listener is executed before the event is dispatched to a specific component, the metaKey property and getModifierKeyState method in the returned KeyEvent cannot provide valid values. |
