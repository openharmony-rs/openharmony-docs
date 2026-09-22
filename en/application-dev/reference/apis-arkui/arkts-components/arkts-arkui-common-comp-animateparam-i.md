# AnimateParam

```TypeScript
declare interface AnimateParam
```

Defines parameters related to animation effects.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish?: () => void
```

Callback invoked when the animation playback is complete. If the UIAbility moves from the foreground to the background, any finite loop animation that is still in progress will be immediately terminated, triggering the completion callback.

If the transition animation is disabled in the developer options and **tempo** is set to **+∞**, the callback is executed immediately when the animation playback is complete.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

Animation curve.

You are advised to specify the curve using the **Curve** or **ICurve** type.

When the type is string, it represents an animation interpolation curve, supporting only the following options:

**"linear"**: Changes linearly.

**"ease"**: Slow at both the start and end of an animation; equivalent to cubic-bezier(0.25, 0.1, 0.25, 1.0).

**"ease-in"**: Starts slowly and then accelerates; equivalent to cubic-bezier(0.42, 0.0, 1.0, 1.0).

**"ease-out"**: Starts quickly and then decelerates; equivalent to cubic-bezier(0.0, 0.0, 0.58, 1.0).

**"ease-in-out"**: Accelerates and then decelerates; equivalent to cubic-bezier(0.42, 0.0, 0.58, 1.0).

**"fast-out-slow-in"**: Standard curve, **cubic-bezier(0.4, 0.0, 0.2, 1.0)**

**"linear-out-slow-in"**: Deceleration curve, **cubic-bezier(0.0, 0.0, 0.2, 1.0)**

**"fast-out-linear-in"**: Acceleration curve, **cubic-bezier(0.4, 0.0, 1.0, 1.0)**

**"friction"**: Damping curve, **cubic-bezier(0.2, 0.0, 0.2, 1.0)**

**"extreme-deceleration"**: Extreme deceleration curve, **cubic-bezier(0.0, 0.0, 0.0, 1.0) curve**

**"rhythm"**: Rhythm curve, **cubic-bezier(0.7, 0.0, 0.2, 1.0)**

**"sharp"**: Sharp curve, **cubic-bezier(0.33, 0.0, 0.67, 1.0)**

**"smooth"**: Smooth curve, **cubic-bezier(0.4, 0.0, 0.4, 1.0)**

**"cubic-bezier(x1, y1, x2, y2)"**: Cubic Bezier curve. The values of **x1** and **x2** must be within the range of [0, 1], as in **"cubic-bezier(0.42, 0.0, 0.58, 1.0)"**.

**"steps(number, step-position)"**: Step curve. **number** is required and must be a positive integer. **step-position** is optional and the values **start** and **end** are supported; defaults to end, as in **"steps(3, start)"**.

**"interpolating-spring(velocity,mass,stiffness,damping)"**: For details about the parameters, see [curves.interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md).

**"responsive-spring-motion(response,dampingFraction,overlapDuration)"**: For details about the parameters, see [curves.responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md).

**"spring(velocity,mass,stiffness,damping)"**: For details about the parameters, see [curves.springCurve](../arkts-apis/arkts-arkui-curves-springcurve-f.md).

**"spring-motion(response,dampingFraction,overlapDuration)"**: For details about the parameters, see [curves.springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md).

Default value: **Curve.EaseInOut**

**Type:** Curve &#124; string &#124; [ICurve](arkts-arkui-common-comp-icurve-i.md)

**Default:** Curve.EaseInOut

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Delay of animation playback, in ms. By default, the playback is not delayed.

Default value: **0**

Value range: (-∞, +∞)

Note: 1. A non-negative **delay** defers the start of the animation. A negative **delay** plays the animation ahead of schedule. If the absolute value of **delay** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **delay** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times.

2. Floating-point values are floored to integers. For example, if the value set is 1.2, **1** will be used.

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Animation duration, in ms.

Default value: **1000**

Note: 1. Before API 26.0.0, the maximum animation duration for an ArkTS widget is 1,000 ms; values exceeding this limit are clamped to 1,000 ms. Starting from API version 26.0.0, the maximum animation duration for an ArkTS widget is adjusted to 2,000 ms.

2. To stop the animation of a property, change the property value in an animation closure with a duration of 0.
3. Values less than 0 are clamped to **0**.
4. Floating-point values are floored to integers. For example, if the value set is 1.2, **1** will be used.
5. The **duration** parameter does not take effect when [springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md), [responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md), and [interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md) are configured for **curve**.

**Type:** number

**Default:** 1000

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expectedFrameRateRange

```TypeScript
expectedFrameRateRange?: ExpectedFrameRateRange
```

Expected frame rate range of the animation.

**Type:** [ExpectedFrameRateRange](arkts-arkui-common-comp-expectedframeraterange-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## finishCallbackType

```TypeScript
finishCallbackType?: FinishCallbackType
```

Type of the **onFinish** callback.

Default value: **FinishCallbackType.REMOVED**

**Type:** [FinishCallbackType](arkts-arkui-common-comp-finishcallbacktype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

Number of times that the animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that there is no animation.

Default value: **1**

Value range: [-1, +∞)

Note: Floating-point values are floored to integers. For example, if the value set is 1.2, **1** will be used.

**Type:** number

**Default:** 1

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## playMode

```TypeScript
playMode?: PlayMode
```

Playback mode. By default, the animation is played from the beginning after the playback is complete.

Default value: **PlayMode.Normal**

> **Notes about PlayMode**:
> 
> - **PlayMode.Normal** and **PlayMode.Alternate** are recommended. Under these settings, the first round of the animation is played forwards. If **PlayMode.Reverse** or **PlayMode.AlternateReverse** is used, the first round of the animation is played backwards. In this case, the animation jumps to the end state and then starts from there.
> 
> - When using **PlayMode.Alternate** or **PlayMode.AlternateReverse**, make sure the final state of the animation is the same as the value of the state variable. In other words, make sure the last round of the animation is played forwards. When **PlayMode.Alternate** is used, **iterations** must be set to an odd number. When
> **PlayMode.AlternateReverse** is used, **iterations** must be set to an even number.
> 
> - **PlayMode.Reverse** is not recommended. Under this setting, the animation jumps to the end state at the beginning, and its final state will be different from the value of the state variable.

**Type:** [PlayMode](../arkts-apis/arkts-arkui-playmode-e.md)

**Default:** PlayMode.Normal

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tempo

```TypeScript
tempo?: number
```

Animation playback speed. A larger value indicates faster animation playback, and a smaller value indicates slower animation playback. The value **0** means that there is no animation.

When the value is set to **+∞**, the animation completes in the current frame, and the animation end callback is executed immediately.

Default value: **1.0**

Value range: [0, +∞)

Note: Values less than 0 are clamped to **0**.

**Type:** number

**Default:** 1.0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
