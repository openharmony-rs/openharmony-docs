# CommonTransition

```TypeScript
declare class CommonTransition<T>
```

Defines the common transition animation for page transitions, which is inherited and used by [PageTransitionEnter](../../../reference/apis-arkui/arkui-ts/ts-page-transition-animation.md#pagetransitionenter) and [PageTransitionExit](../../../reference/apis-arkui/arkui-ts/ts-page-transition-animation.md#pagetransitionexit). It must be configured in the **pageTransition()** function. Both **slide** and **translate** involve position movement: **slide** is suitable for scenarios that require sliding in and out along a preset direction (left/right/up /down/**START**\/**END)** and is simple to use; **translate** is suitable for scenarios that require a custom translation distance and offers higher flexibility. When **slide** and **translate** are set simultaneously, **slide** takes effect by default. **scale** and **opacity** set the scale and opacity effects respectively, and can be combined with the effects above.

**Since:** 7

<!--Device-unnamed-declare class CommonTransition<T>--><!--Device-unnamed-declare class CommonTransition<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a common transition animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonTransition-constructor()--><!--Device-CommonTransition-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity(value: number): T
```

Sets the starting opacity value for entrance or the ending opacity value for exit.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonTransition-opacity(value: number): T--><!--Device-CommonTransition-opacity(value: number): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start opacity value of the entrance animation or the end opacity value of the exit animation.<br>Value range: [0, 1] |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component, used for chained calls. |

## scale

```TypeScript
scale(value: ScaleOptions): T
```

Sets the scaling effect for page transitions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonTransition-scale(value: ScaleOptions): T--><!--Device-CommonTransition-scale(value: ScaleOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md) | Yes | Scale effect during page transition, which is the value at the start point when entering and at the end point when exiting.<br>- **x**: horizontal scale multiple (or scale ratio). <br>- **y**: vertical scale multiple (or scale ratio). <br>- **z**: depth scale multiple (or scale ratio). <br>- **centerX** and **centerY**: scale center point. The default values of **centerX** and **centerY** are **"50%"**, that is, the center point of the page is used as the scale center point by default. <br>- A center point of (0, 0) represents the upper left corner of the page.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component, used for chained calls. |

## slide

```TypeScript
slide(value: SlideEffect): T
```

Sets the slide-in and slide-out effect during page transition. When set simultaneously with **translate**, **slide** takes effect by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonTransition-slide(value: SlideEffect): T--><!--Device-CommonTransition-slide(value: SlideEffect): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SlideEffect](arkts-arkui-pagetransitionenter-comp-slideeffect-e.md) | Yes | Slide-in and slide-out effects for page transitions. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component, used for chained calls. |

## translate

```TypeScript
translate(value: TranslateOptions): T
```

Sets the translation effect for page transitions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonTransition-translate(value: TranslateOptions): T--><!--Device-CommonTransition-translate(value: TranslateOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation effect during page transition, which is the value at the start point when entering and at the end point when exiting. When set simultaneously with **slide**, **slide** takes effect by default.<br>- **x**: horizontal translation distance. <br>- **y**: vertical translation distance. <br>- **z**: z-axis translation distance.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component, used for chained calls. |
