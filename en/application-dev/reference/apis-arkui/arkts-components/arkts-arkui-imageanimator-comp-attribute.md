# ImageAnimator properties/events

```TypeScript
declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>

**Since:** 7

<!--Device-unnamed-declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>--><!--Device-unnamed-declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration(value: number)
```

Sets the playback duration. When any frame in [images](#images) has its own duration set, this attribute does not take effect.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-duration(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-duration(value: number): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Playback duration.<br>If the value is 0, no image is played.<br>If the display duration allocated per image is shorter than a single frame interval, playback anomalies may occur.<br>If it is set to a negative value, the default value **1000** is used.<br>The value change takes effect only at the start of the next cycle.<br>Unit: ms<br>Default value: **1000** |

## fillMode

```TypeScript
fillMode(value: FillMode)
```

Sets the status before and after execution of the animation in the current playback direction. The status after execution of the animation is jointly determined by the **fillMode** and **reverse** attributes. For example, if **fillMode** is set to **Forwards**, the target will retain the state defined by the last keyframe encountered during execution. In this case, if **reverse** is set to **false**, the target will retain the state defined by the last keyframe encountered in the forward direction, that is, the last image; if **reverse** is set to **true**, the target will retain the state defined by the last keyframe encountered in the backward direction, that is, the first image.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-fillMode(value: FillMode): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-fillMode(value: FillMode): ImageAnimatorAttribute-End-->

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

<!--Device-ImageAnimatorAttribute-fixedSize(value: boolean): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-fixedSize(value: boolean): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the image size is fixed at the component size.<br> **true**: The image size is fixed at the component size. In this case, the width, height, top, and left attributes of the image are invalid. <br> **false**: The width, height, top, and left attributes of each image must be set separately. If the image size does not match the component size, the image will not be stretched. <br>Default value: **true** |

## images

```TypeScript
images(value: Array<ImageFrameInfo>)
```

Sets image frame information. Dynamic update is not supported; otherwise, issues such as display disorder, abnormal frame switching, or memory increase may occur. (This attribute is designed for non-dynamic update, and modifications at runtime are not guaranteed to take effect.)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-images(value: Array<ImageFrameInfo>): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-images(value: Array<ImageFrameInfo>): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ImageFrameInfo](arkts-arkui-imageanimator-comp-imageframeinfo-i.md)&gt; | Yes | Image frame information. The information of each frame includes the path, size, position, and playback duration of an image. For details, see [ImageFrameInfo](arkts-arkui-imageanimator-comp-imageframeinfo-i.md). <br>Default value: **[]** <br> Note: If the input array is too large, memory usage may increase. Therefore, as the controller of memory usage, be sure to assess potential memory consumption before passing in the data to avoid issues such as insufficient memory. |

## interpolation

```TypeScript
interpolation(value: ImageInterpolation)
```

Sets the interpolation effect of the frame images. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-ImageAnimatorAttribute-interpolation(value: ImageInterpolation): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-interpolation(value: ImageInterpolation): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageInterpolation](arkts-arkui-image-comp-imageinterpolation-e.md) | Yes | Interpolation effect of the frame images.<br>Default value: **ImageInterpolation.Low**<br>When set to **undefined**, the value is treated as **ImageInterpolation.Low**. |

## iterations

```TypeScript
iterations(value: number)
```

Sets the number of times that the animation is played.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ImageAnimatorAttribute-iterations(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-iterations(value: number): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of times that the animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. Values less than **-1** are treated as the default value. When the value is a floating-point number, it is rounded down.<br> Default value: **1** |

## monitorInvisibleArea

```TypeScript
monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute
```

Sets whether the component should automatically pause or resume based on its visibility, using the system's [onVisibleAreaChange] [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) event.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-ImageAnimatorAttribute-monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorInvisibleArea | boolean | Yes | Whether the component should automatically pause or resume based on its visibility, using the system's **onVisibleAreaChange**. When this parameter is set to **true**, the component controls pause and playback based on the visibility determination of the system's [onVisibleAreaChange] [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange). When the component's running state is [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md).Running, playback is automatically paused if the component is determined to be invisible, and automatically resumed if it is determined to be visible. When this parameter is set to **false**, the pause and playback of the component are not affected by **onVisibleAreaChange**.<br>Default value: **false** <br> **NOTE:** <br>When the value of this parameter is dynamically changed from **true** to **false**, the component is processed based on the current [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) state.<br> For example, if the current state is **Running** and playback is paused due to the invisible callback of [onVisibleAreaChange] [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange), after the value is changed from **true** to **false**, the component resumes playback from the position where it was last paused.<br>The pause and playback operations caused by this parameter do not change the [state](#state) value set by the user. |

## onCancel

```TypeScript
onCancel(event: () => void)
```

Triggered when the animation is canceled (that is, **state** is set to [AnimationStatus.Initial](../arkts-apis/arkts-arkui-animationstatus-e.md)). After triggering, the image display returns to the first frame (forward playback) or the last frame (reverse playback). The difference from [onFinish](#onfinish) is that **onCancel** returns to the **Initial** state, while **onFinish** corresponds to the state where the animation ends naturally or stops (**Stopped**).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-onCancel(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onCancel(event: () => void): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation is canceled (that is, **state** is set to **AnimationStatus.Initial**). After triggering, the image display returns to the first frame (forward playback) or the last frame (reverse playback). |

## onFinish

```TypeScript
onFinish(event: () => void)
```

Triggered when the animation playback completes (all iterations set by **iterations** are played and the animation ends naturally) or stops (**state** is switched to [AnimationStatus.Stopped](../arkts-apis/arkts-arkui-animationstatus-e.md)). When the animation is in the [AnimationStatus.Initial](../arkts-apis/arkts-arkui-animationstatus-e.md) state, returning to the initial state does not trigger this event; instead, **onCancel** is triggered.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-onFinish(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onFinish(event: () => void): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation playback completes (all iterations set by **iterations** are played and the animation ends naturally) or stops (**state** is switched to **AnimationStatus.Stopped**). |

## onPause

```TypeScript
onPause(event: () => void)
```

Triggered when the animation playback is paused.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-onPause(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onPause(event: () => void): ImageAnimatorAttribute-End-->

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

<!--Device-ImageAnimatorAttribute-onRepeat(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onRepeat(event: () => void): ImageAnimatorAttribute-End-->

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

<!--Device-ImageAnimatorAttribute-onStart(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onStart(event: () => void): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the animation starts to play. |

## reverse

```TypeScript
reverse(value: boolean)
```

Sets the playback direction.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-reverse(value: boolean): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-reverse(value: boolean): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Playback direction.<br>The value **false** indicates that images are played from the first one to the last one, and **true** indicates that images are played from the last one to the first one.<br>Which frame is retained after the animation ends is also related to the [fillMode](#fillmode) attribute. For details, see the description of **fillMode**.<br>Default value: **false** |

## state

```TypeScript
state(value: AnimationStatus)
```

Sets the playback state of the animation.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageAnimatorAttribute-state(value: AnimationStatus): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-state(value: AnimationStatus): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) | Yes | Playback state.<br>Default value: **AnimationStatus.Initial** |

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

<!--Device-ImageAnimatorAttribute-preDecode(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-preDecode(value: number): ImageAnimatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of images to be pre-decoded. For example, the value **2** indicates that two images following the currently playing one are pre-decoded, to improve performance.<br>Default value: **0** |
