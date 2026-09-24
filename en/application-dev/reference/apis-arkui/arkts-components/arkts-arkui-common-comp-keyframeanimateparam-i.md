# KeyframeAnimateParam

```TypeScript
declare interface KeyframeAnimateParam
```

Provides animation configuration options.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish?: () => void
```

Callback invoked when the animation playback is complete. This API is called after the keyframe animation has played for the specified number of times. If transition animations are disabled in developer options, or if a **UIAbility** switches from the foreground to the background, any ongoing finite keyframe animation will stop immediately and trigger the playback completion callback.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Overall delay of the animation, in milliseconds. By default, the animation is played without delay.

Default value: **0**.

**NOTE:** 

A value greater than 0 means to begin the animation after the specified amount of time has elapsed.

A value less than 0 means to begin the animation in advance. If the absolute value of **delay** is less than the actual animation duration, the animation starts its first frame from the state at the absolute value. If the absolute value of **delay** is greater than or equal to the actual animation duration, the animation starts its first frame from the end state. The actual animation duration is equal to the duration of a single animation multiplied by the number of animation playback times.

**Type:** number

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expectedFrameRateRange

```TypeScript
expectedFrameRateRange?: ExpectedFrameRateRange
```

Expected frame rate range of the animation.

Default value: {min:0, max:0, expected:0} (following the application's frame rate)

**NOTE:** 

After a valid expected frame rate is set, the system collects the configured frame rate and divides the frequency on the rendering pipeline. The actual frame rate may be different from the expected one configured. It is limited by the system capability and screen refresh rate.

**Type:** [ExpectedFrameRateRange](arkts-arkui-common-comp-expectedframeraterange-i.md)

**Default:** { min: 0, expected: 0, max: 0 }

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

Number of times that the animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times. The value **0** indicates that there is no animation.

Default value: **1**.

Value range: [–1, +∞).

**NOTE:** 

- Floating-point values will be rounded down to integers. For example, if the value set is 1.2, **1** will be used.

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
