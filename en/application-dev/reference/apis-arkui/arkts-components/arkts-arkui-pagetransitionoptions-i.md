# PageTransitionOptions

Parameters of the exit or entrance animation.

@interface PageTransitionOptions

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

Animation delay.

Unit: ms

Default value: **0**

**NOTE:** 

If no match is found, the default page transition effect is used (which may vary according to the device). To disable the default page transition effect, set **duration** to **0**.

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

Unit: ms

Default value: **1000**

Value range: [0, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: RouteType
```

Route type for the page transition effect to take effect.

Default value: **RouteType.None**

**Type:** [RouteType](arkts-arkui-routetype-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
