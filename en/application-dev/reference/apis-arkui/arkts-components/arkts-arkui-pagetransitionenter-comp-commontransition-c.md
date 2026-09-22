# CommonTransition

```TypeScript
declare class CommonTransition<T>
```

Defines a common transition animation for page transitions.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a common transition animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity(value: number): T
```

Sets the starting opacity value for entrance or the ending opacity value for exit.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Starting opacity value for entrance or the ending opacity value for exit.<br>Value range: [0, 1] |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## scale

```TypeScript
scale(value: ScaleOptions): T
```

Sets the scaling effect for page transitions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md) | Yes | Scaling effect for page transitions, specifying the start value for entrance and the end value for exit.<br>- **x**: scale factor along the x-axis.<br>- **y**: scale factor along the y-axis.<br>- **z**: scale factor along the z-axis.<br>- **centerX** and **centerY**: scaling center. The default values are both **"50%"**, meaning the center of the page is used as the scaling center by default.<br>- If the center point is (0, 0), it refers to the upper left corner of the component.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## slide

```TypeScript
slide(value: SlideEffect): T
```

Sets the slide-in and slide-out effects for page transitions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SlideEffect](arkts-arkui-pagetransitionenter-comp-slideeffect-e.md) | Yes | Slide-in and slide-out effects for page transitions. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## translate

```TypeScript
translate(value: TranslateOptions): T
```

Sets the translation effect for page transitions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation effect for page transitions, specifying the start value for entrance and the end value for exit. When this parameter is set together with **slide**, the latter takes effect by default.<br>- **x**: translation distance along the x-axis.<br>- **y**: translation distance along the y-axis.<br>- **z**: translation distance along the y-axis.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
