# RotationGestureHandler

```TypeScript
declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>
```

Defines a rotation gesture handler object.

**Inheritance/Implementation:** RotationGestureHandler extends GestureHandler<RotationGestureHandler>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RotationGestureHandlerOptions)
```

Constructor used to create a rotation gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotationGestureHandlerOptions](arkts-arkui-tapgesture-comp-rotationgesturehandleroptions-i.md) | No | Parameters of the rotation gesture handler. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): RotationGestureHandler
```

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the rotation gesture is cancelled. No gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler
```

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked during rotation gesture movement. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Rotation gesture handler object. |
