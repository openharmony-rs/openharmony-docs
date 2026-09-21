# ImageAnimator properties/events

```TypeScript
declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md#common), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md#common), the following events are supported.

**Inheritance/Implementation:** ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration(value: number)
```

Sets the playback duration. This attribute does not take effect when a separate duration is set for any of the image frames.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Playback duration.<br>If the value is **0**, no image is played.<br>If the display duration allocated per image is shorter than a single frame interval, playback anomalies may occur.<br>If it is set to a negative value, the default value is used.<br>The value change takes effect only at the start of the next cycle.<br>Unit: ms<br>Default value: **1000** |

## fillMode

```TypeScript
fillMode(value: FillMode)
```

Sets the status before and after execution of the animation in the current playback direction. The status after execution of the animation is jointly determined by the **fillMode** and **reverse** attributes. For example, if **fillMode** is set to **Forwards**, the target will retain the state defined by the last keyframe encountered during execution. In this case, if **reverse** is set to **false**, the target will retain the state defined by the last keyframe encountered in the forward direction, that is, the last image; if **reverse** is set to **true**, the target will retain the state defined by the last keyframe encountered in the backward direction, that is, the first image.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FillMode](../arkts-apis/arkts-arkui-fillmode-e.md) | Yes | Status before and after execution of the animation in the current playback direction.<br>Default value: **FillMode.Forwards** |

## fixedSize

```TypeScript
fixedSize(value: boolean)
```

Sets whether the image size is fixed at the component size.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the image size is fixed at the component size.<br> **true**: The image size is fixed at the component size. In this case, the width, height, top, and left attributes of the image are invalid.<br> **false**: The width, height, top, and left attributes of each image must be set separately. If the image size does not match the component size, the image will not be stretched.<br>Default value: **true** |

## images

```TypeScript
images(value: Array<ImageFrameInfo>)
```

Sets image frame information. Dynamic update is not supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ImageFrameInfo](arkts-arkui-imageanimator-comp-imageframeinfo-i.md)&gt; | Yes | Image frame information. The information of each frame includes the path, size, position, and playback duration of an image. For details, see [ImageFrameInfo](arkts-arkui-imageanimator-comp-imageframeinfo-i.md).<br> Default value: **[]**<br> Note: If the input array is too large, memory usage may increase. Therefore, as the controller of memory usage, be sure to assess potential memory consumption before passing in the data to avoid issues such as insufficient memory. |

## iterations

```TypeScript
iterations(value: number)
```

Sets the number of times that the animation is played.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. Values less than **-1** are treated as the default value. When the value is a floating-point number, it is rounded down.<br>Default value: **1** |

## monitorInvisibleArea

```TypeScript
monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute
```

Sets whether the component should automatically pause or resume based on its visibility, using the system's [onVisibleAreaChange] [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) event.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorInvisibleArea | boolean | Yes | Whether the component should automatically pause or resume based on its visibility, using the system's [onVisibleAreaChange] [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) event.<br> With the value **true**, when the component's [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) is **Running**, the component automatically pauses once it becomes invisible and resumes playback if it becomes visible again, based on the **onVisibleAreaChange** event.<br>With the value **false**, the pause and playback of the component are not affected by **onVisibleAreaChange**.<br>Default value: **false**<br> **NOTE:** <br>When this parameter is dynamically changed from **true** to **false**, the component will resume from its last paused state based on the current [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md).<br>Changes to this property do not affect the custom [state](#state) value. |

## onCancel

```TypeScript
onCancel(event: () => void)
```

Triggered when the animation playback returns to the initial state.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation playback returns to the initial state. |

## onFinish

```TypeScript
onFinish(event: () => void)
```

Triggered when the animation playback completes or stops.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation playback completes or stops. |

## onPause

```TypeScript
onPause(event: () => void)
```

Triggered when the animation playback is paused.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation playback is paused. |

## onRepeat

```TypeScript
onRepeat(event: () => void)
```

Triggered when the animation playback is repeated.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation playback is repeated. |

## onStart

```TypeScript
onStart(event: () => void)
```

Triggered when the animation starts to play.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation starts to play. |

## preDecode

```TypeScript
preDecode(value: number)
```

Sets the number of images to be pre-decoded.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Currently, no substitute is
> available.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of images to be pre-decoded. For example, the value **2** indicates that two images following the currently playing one are pre-decoded.<br>Default value: **0** |

## reverse

```TypeScript
reverse(value: boolean)
```

Sets the playback direction.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Playback direction.<br>The value **false** indicates that images are played from the first one to the last one, and **true** indicates that images are played from the last one to the first one.<br>Default value: **false** |

## state

```TypeScript
state(value: AnimationStatus)
```

Sets the playback state of the animation.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) | Yes | Playback state of the animation.<br>Default value: **AnimationStatus.Initial** |
