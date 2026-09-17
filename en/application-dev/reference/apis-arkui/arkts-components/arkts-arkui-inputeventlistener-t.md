# InputEventListener

```TypeScript
declare type InputEventListener = (
  event: RawInputEventWrapper
) => InputEventInterceptResult
```

Input event listener callback type.

> **NOTE:** 
> 
> - **RawInputEventWrapper** is an abstract class. Developers cannot create instances using the `new` operator.
> 
> - The system automatically creates instances when an event is triggered and passes them to the callback through this parameter.
> 
> - The current callback parameter **event** only encapsulates the following raw input event types:[MouseEvent](arkts-arkui-mouseevent-i.md), [TouchEvent](arkts-arkui-touchevent-i.md), [KeyEvent](arkts-arkui-keyevent-i.md). Developers can obtain the corresponding event objects using [asMouseEvent](arkts-arkui-rawinputeventwrapper-c.md#asmouseevent),[asTouchEvent](arkts-arkui-rawinputeventwrapper-c.md#astouchevent), and [asKeyEvent](arkts-arkui-rawinputeventwrapper-c.md#askeyevent).
> 
> - Do not perform time-consuming operations (such as complex calculations or network requests) in the callback, as this may cause application lag.
> 
> - The listener executes synchronously on the UI thread, which directly blocks the event processing flow. It is recommended to only perform simple judgment and calculation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [RawInputEventWrapper](arkts-arkui-rawinputeventwrapper-c.md) | Yes | Input event wrapper. The system automatically creates and passes it. Developers do not need to create it manually. |

**Return value:**

| Type | Description |
| --- | --- |
| [InputEventInterceptResult](arkts-arkui-inputeventinterceptresult-i.md) | Event interception result. |
