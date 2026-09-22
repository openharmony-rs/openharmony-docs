# NavDestinationTransition

```TypeScript
declare interface NavDestinationTransition
```

Defines a custom transition animation for the **NavDestination** component.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve
```

Curve type of the animation.

Default value: Curve.EaseInOut](ts-appendix-enums.md#curve)

**Type:** Curve

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Delay of the transition animation.

Default value: **0** (in milliseconds)

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Duration of the transition animation.

Default value: **1000** (in milliseconds)

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: Callback<void>
```

Closure function specifying the transition animation. The system generates the corresponding transition animation based on the modifications to the component's UI state within the closure. For details, see **event** in [animateTo](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto).

**Type:** Callback&lt;void&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: Callback<void>
```

Callback triggered when the transition animation ends.

**Type:** Callback&lt;void&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
