# TapGestureHandler

```TypeScript
declare class TapGestureHandler extends GestureHandler<TapGestureHandler>
```

Defines the tap gesture handler object type, which is used to recognize tap interactions on a component. It is suitable for touch scenarios such as single tap, multiple taps, or multi-finger tap, and supports configuring recognition conditions such as the tap count and the number of triggering fingers.

**Inheritance/Implementation:** TapGestureHandler extends GestureHandler&lt;TapGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class TapGestureHandler extends GestureHandler<TapGestureHandler>--><!--Device-unnamed-declare class TapGestureHandler extends GestureHandler<TapGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: TapGestureHandlerOptions)
```

Constructor used to create a tap gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)--><!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TapGestureHandlerOptions](arkts-arkui-tapgesture-comp-tapgesturehandleroptions-i.md) | No | Tap gesture handler configuration options. Pass this parameter when you need to customize the number of consecutive taps, the number of fingers that trigger the tap, the finger count check, or the tap gesture movement threshold. If this parameter is not passed, the default tap gesture handler configuration is used, for example, the number of consecutive taps is 1, the number of fingers that trigger the tap is 1, and the number of fingers touching the screen is not checked by default. |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): TapGestureHandler
```

Sets the callback for successful tap gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): TapGestureHandler--><!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): TapGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful tap gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [TapGestureHandler](arkts-arkui-tapgesture-comp-tapgesturehandler-c.md) | Tap gesture handler object. |
