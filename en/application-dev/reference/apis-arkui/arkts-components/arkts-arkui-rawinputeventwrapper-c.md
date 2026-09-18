# RawInputEventWrapper

Raw input event wrapper class.

Provides a unified interface to access different types of input events, ensuring type safety and backward compatibility.

This class encapsulates either a raw **MouseEvent**, **TouchEvent**, or **KeyEvent** object and provides type-safe methods for access.

This class is an abstract class. Developers cannot create instances on their own. The system automatically creates an instance and passes it to the callback when the input event listener is triggered.

> **NOTE:** 
> 
> Since the listener is executed before events are dispatched to specific components, some fields in the event will
> not provide valid values: the trigger object [target](arkts-arkui-eventtarget-i.md), coordinates relative to the component
> [x](arkts-arkui-mouseevent-i.md#x) and [y](arkts-arkui-mouseevent-i.md#y), [getCurrentLocalPosition](arkts-arkui-touchobject-i.md#getcurrentlocalposition)
> and [stopPropagation](arkts-arkui-touchevent-i.md#stoppropagation) methods, [preventDefault](arkts-arkui-touchevent-i.md#preventdefault) and
> [getHistoricalPoints](arkts-arkui-touchevent-i.md#gethistoricalpoints) methods of **TouchEvent**, as well as the [metaKey](arkts-arkui-keyevent-i.md#metakey)
> attribute and [getModifierKeyState](arkts-arkui-keyevent-i.md#getmodifierkeystate) method of **KeyEvent**.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## asKeyEvent

```TypeScript
asKeyEvent(): KeyEvent | null
```

Obtains the key event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [KeyEvent](arkts-arkui-keyevent-i.md) &#124; null | Key event object if it is a key event, or **null** otherwise. |

## asMouseEvent

```TypeScript
asMouseEvent(): MouseEvent | null
```

Obtains the mouse event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MouseEvent](arkts-arkui-mouseevent-i.md) &#124; null | Mouse event object if it is a mouse event, or **null** otherwise. |

## asTouchEvent

```TypeScript
asTouchEvent(): TouchEvent | null
```

Obtains the touch event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TouchEvent](arkts-arkui-touchevent-i.md) &#124; null | Touch event object if it is a touch event, or **null** otherwise. |

## isKeyEvent

```TypeScript
isKeyEvent(): boolean
```

Checks whether the event is a key event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether it is a key event. Returns **true** if it is a key event, and **false** otherwise. |

## isMouseEvent

```TypeScript
isMouseEvent(): boolean
```

Checks whether the event is a mouse event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether it is a mouse event. Returns **true** if it is a mouse event, and **false** otherwise. |

## isTouchEvent

```TypeScript
isTouchEvent(): boolean
```

Checks whether the event is a touch event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether it is a touch event. Returns **true** if it is a touch event, and **false** otherwise. |
