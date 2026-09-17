# sharedTransitionOptions

Parameters of the shared element transition animation.

> **NOTE:** 
> 
> **motionPath** is effective only when **type** is set to **SharedTransitionEffectType.Exchange**.
> 
> When **type** is set to **SharedTransitionEffectType.Exchange**, the effect focuses on smooth transition of the
> position and size of matching shared elements, which can be visually observed through the component's border. The
> transition, however, does not involve content properties, which will abruptly change to the target page's values at
> the end of the animation. For example, if a **Text** component has different **fontSize** values on two pages, the
> font size will snap to the target page's value once the shared transition animation completes.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

Animation curve.

You are advised to specify the curve using the **Curve** or **ICurve** type.

For the string type, this parameter indicates an animation interpolation curve. For available values, see the **curve** parameter in [AnimateParam](arkts-arkui-animateparam-i.md).

Default value: **Curve.Linear**

**Type:** [Curve](../arkts-apis/arkts-arkui-curve-e.md) &#124; string &#124; [ICurve](arkts-arkui-icurve-i.md)

**Default:** Curve.Linear

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Delay of animation playback.

Default value: **0**

Unit: ms

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Animation duration.

Default value: **1000**

Unit: ms

Value range: [0, +∞)

**Type:** number

**Default:** 1000

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## motionPath

```TypeScript
motionPath?: MotionPathOptions
```

Motion path.

**Type:** [MotionPathOptions](arkts-arkui-motionpathoptions-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: SharedTransitionEffectType
```

Animation type.

Default value: **SharedTransitionEffectType.Exchange**

**Type:** [SharedTransitionEffectType](../arkts-apis/arkts-arkui-sharedtransitioneffecttype-e.md)

**Default:** SharedTransitionEffectType.Exchange

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## zIndex

```TypeScript
zIndex?: number
```

Z-axis.

Value range: (-∞, +∞)

Default value: **0**

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
