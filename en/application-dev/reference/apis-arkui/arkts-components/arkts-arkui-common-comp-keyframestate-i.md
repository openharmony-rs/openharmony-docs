# KeyframeState

```TypeScript
declare interface KeyframeState
```

Provides keyframe configuration options.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: () => void
```

Closure function of the state at the time of the keyframe, that is, the state to be reached at the time of the keyframe.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

Animation curve used by the keyframe.

You are advised to specify the curve using the **Curve** or **ICurve** type.

For the string type, this parameter indicates an animation interpolation curve. For available values, see the **curve** parameter in [AnimateParam](arkts-arkui-common-comp-animateparam-i.md).

Default value: **Curve.EaseInOut**

**NOTE:** 

Because the [springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md), [responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md), and [interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md) curves do not have effective duration settings, they are not supported.

**Type:** Curve &#124; string &#124; [ICurve](arkts-arkui-common-comp-icurve-i.md)

**Default:** Curve.EaseInOut

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

Duration of the keyframe animation, in ms.

Value range: [0, +∞)

**NOTE:** 

- If this parameter is set to a value less than 0, the value **0** is used.  
- Floating-point values will be rounded down to integers. For example, if the value set is 1.2, **1** will be used.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
