# RotationGestureHandler

```TypeScript
declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>
```

Defines the rotation gesture handler object type, which is used to recognize multi-finger rotation interactions on a component. It is suitable for scenarios where an object needs to be rotated or an angle needs to be adjusted, and supports configuring recognition conditions such as the number of triggering fingers, the minimum angle change, and the finger count limit.

**Inheritance/Implementation:** RotationGestureHandler extends GestureHandler&lt;RotationGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>--><!--Device-unnamed-declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RotationGestureHandlerOptions)
```

Constructor used to create a rotation gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)--><!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotationGestureHandlerOptions](arkts-arkui-tapgesture-comp-rotationgesturehandleroptions-i.md) | No | Rotation gesture handler configuration options. Pass this parameter when you need to customize the minimum number of fingers to trigger rotation, the minimum angle change to trigger the rotation gesture, or the finger count check. If this parameter is not passed, the default configuration of the rotation gesture handler is used, for example, two fingers to trigger, a minimum angle change of 1deg, and no check on the number of fingers touching the screen by default. |

<a id="onactioncancel1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): RotationGestureHandler
```

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandler-onActionCancel(event: Callback<void>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionCancel(event: Callback<void>): RotationGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the rotation gesture is cancelled. No gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |

<a id="onactioncancel2"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler
```

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel1), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when the rotation gesture is cancelled. Gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler
```

Sets the callback for rotation gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when rotation gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): RotationGestureHandler
```

Sets the callback for successful rotation gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful rotation gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler
```

Sets the callback for rotation gesture movement updates. The callback is triggered when the rotation gesture moves.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked during rotation gesture movement. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |
