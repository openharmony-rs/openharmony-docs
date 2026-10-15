# PageTransitionOptions

```TypeScript
declare interface PageTransitionOptions
```

Defines the parameters of the exit/entrance animation.

**Since:** 7

<!--Device-unnamed-declare interface PageTransitionOptions--><!--Device-unnamed-declare interface PageTransitionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

Animation curve.

It is recommended to specify it in the form of **Curve** or **ICurve**.

When the type is string, it is the animation interpolation curve. For details about the value, see the **curve** parameter of [AnimateParam](arkts-arkui-common-comp-animateparam-i.md).

Default value: **Curve.Linear**

**Type:** Curve &#124; string &#124; ICurve

**Default:** Curve.Linear

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PageTransitionOptions-curve?: Curve | string | ICurve--><!--Device-PageTransitionOptions-curve?: Curve | string | ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Animation delay.

Unit: ms

Default value: **0**

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PageTransitionOptions-delay?: number--><!--Device-PageTransitionOptions-delay?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Duration of the animation.

Unit: ms

Default value: **1000**

Value range: [0, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PageTransitionOptions-duration?: number--><!--Device-PageTransitionOptions-duration?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: RouteType
```

Route type for which the page transition effect takes effect.

Default value: **RouteType.None**.

**Note:** 

When multiple [PageTransitionEnter](arkts-arkui-pagetransitionenter-comp.md) or [PageTransitionExit](arkts-arkui-pagetransitionenter-comp-con.md#pagetransitionexit) components are configured in the **pageTransition** function, they take effect according to the **RouteType** matching rule: the system selects the last matching component from all configured **PageTransitionEnter**\/ **PageTransitionExit** components based on the current route operation type (**Push** or **Pop**); if no component matches, the system default page transition effect is used (which may vary by device). If multiple **PageTransitionEnter** components match the same **RouteType**, the last configured one takes effect; if multiple **PageTransitionExit** components match the same **RouteType**, the last configured one takes effect. **RouteType.None** matches all route types.

Value selection principle: **None** indicates that it takes effect for all route types; **Push** takes effect only for push routes; **Pop** takes effect only for pop routes.

**Type:** [RouteType](arkts-arkui-pagetransitionenter-comp-routetype-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PageTransitionOptions-type?: RouteType--><!--Device-PageTransitionOptions-type?: RouteType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
