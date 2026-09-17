# DragEvent

Provides information about the drag event.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableInternalDropAnimation

```TypeScript
enableInternalDropAnimation(configuration: string): void
```

Sets whether to enable the system's built-in drop animation effect. This API is available only to system applications and can only be used during the **onDrop** phase.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configuration | string | Yes | the internal drop animation's configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [190003](../errorcode-drag-event.md#190003-operation-not-allowed-in-the-current-phase) | Operation not allowed for current phase. |

## executeFollowHandMorphDropAnimation

```TypeScript
executeFollowHandMorphDropAnimation(onAnimationFinished: Callback<void>, animationOption?: string): void
```

Sets a callback to be executed after the follow-hand morph drop animation is completed. This callback is triggered by the system after the drag framework animation ends. This callback uses an asynchronous callback.

> **NOTE:** 
> 
> 1. This API takes effect only when [dragAnimationType](#draganimationtype) is set to **DragAnimationType.FOLLOW_HAND_MORPH**.
> 
> 2. Do not implement logic unrelated to the animation in the callback to avoid affecting execution efficiency.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onAnimationFinished | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; | Yes | Callback triggered after the drag framework animation ends. |
| animationOption | string | No | Drop animation parameters.<br>The parameter is a JSON string containing the following fields:<br>**CubicCurveEnable**: boolean, indicating whether to enable the cubic curve animation. Set to **true** to enable it, or **false** to disable it.<br>**SpringEnable**: boolean, indicating whether to enable the spring animation. Set to **true** to enable it, or **false** to disable it.<br> **dropAnimationCurve**: number[], indicating the drop animation curve parameters. Its meaning depends on **SpringEnable** and **CubicCurveEnable** (with **SpringEnable** having higher priority). When **SpringEnable** is **true**, the array length is 3, in the format of [response, dampingRatio, blendDuration], corresponding to the spring curve parameters of [curves.springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md). When **SpringEnable** is **false** and **CubicCurveEnable** is **true**, the array length is 4, in the format of [x1, y1, x2, y2], corresponding to the cubic Bezier curve control point parameters of [curves.cubicBezierCurve](../arkts-apis/arkts-arkui-curves-cubicbeziercurve-f.md).<br>**NOTE:** **SpringEnable** takes priority over **CubicCurveEnable**. When both are **true**, the spring animation prevails. When neither **SpringEnable** nor **CubicCurveEnable** is correctly set, the default spring animation is used.<br> **dropPosition**: number[], indicating the drop position coordinates. The array length is 2, in the format of [x, y], in px, representing the target position coordinates of the dragged element when it drops. Value range: (-∞, +∞).<br>**dropSize**: number[], indicating the drop size. The array length is 2, in the format of [width, height], in px, representing the target size of the dragged element when it drops. Value range: (0, +∞). |

## dragAnimationType

```TypeScript
dragAnimationType?: DragAnimationType
```

Sets the drag animation type. This attribute can only be set during the [onDragStart](arkts-arkui-commonmethod-c.md#ondragstart) phase and can be obtained in the [onDragStart](arkts-arkui-commonmethod-c.md#ondragstart), [onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-commonmethod-c.md#ondragmove), [onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave), [onDrop](arkts-arkui-commonmethod-c.md#ondrop), and [onDragEnd](arkts-arkui-commonmethod-c.md#ondragend) callbacks.

Default value: **DEFAULT**

**System API:** This is a system API.

**Type:** [DragAnimationType](arkts-arkui-draganimationtype-e-sys.md)

**Default:** DragAnimationType.DEFAULT

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
