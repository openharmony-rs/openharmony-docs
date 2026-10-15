# PatternLock properties/events

```TypeScript
declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** PatternLockAttribute extends CommonMethod&lt;PatternLockAttribute&gt;

**Since:** 9

<!--Device-unnamed-declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>--><!--Device-unnamed-declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activateCircleStyle

```TypeScript
activateCircleStyle(options: Optional<CircleStyleOptions>)
```

Sets the background circle style for the dots in a grid when they are in the activated state.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-activateCircleStyle(options: Optional<CircleStyleOptions>): PatternLockAttribute--><!--Device-PatternLockAttribute-activateCircleStyle(options: Optional<CircleStyleOptions>): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CircleStyleOptions](arkts-arkui-patternlock-comp-circlestyleoptions-i.md)&gt; | Yes | Background circle style of the dots in the activated state. |

## activeColor

```TypeScript
activeColor(value: ResourceColor)
```

Sets the fill color of the grid dots in the active state, which is the state where a finger passes over a dot but the dot is not yet selected. If this attribute is not set, the default fill color is **'#ff182431'** (dark gray).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-activeColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-activeColor(value: ResourceColor): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the active state. |

## autoReset

```TypeScript
autoReset(value: boolean)
```

Sets whether to reset the component state when the component area is pressed again after password input is complete. If this API is not used to set it, the component state is reset by default.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-autoReset(value: boolean): PatternLockAttribute--><!--Device-PatternLockAttribute-autoReset(value: boolean): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to reset the component state when the component area is pressed again after password input is complete.<br>true: reset the component state (that is, clear the previously entered password); false: do not reset the component state. |

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor)
```

Sets the background color. If this attribute is not set, the background is transparent by default, that is, no background color is applied.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-backgroundColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-backgroundColor(value: ResourceColor): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color. |

## circleRadius

```TypeScript
circleRadius(value: Length)
```

Sets the radius of the grid dots. If this attribute is not set, the default radius is **6vp**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-circleRadius(value: Length): PatternLockAttribute--><!--Device-PatternLockAttribute-circleRadius(value: Length): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Radius of the grid dot.<br>Value range: (0, sideLength/11]. If the value is less than or equal to 0, the default value is used. If the value exceeds the maximum, the maximum value is used. |

## onDotConnect

```TypeScript
onDotConnect(callback: import('../api/@ohos.base').Callback<number>)
```

Invoked when a grid dot is connected during pattern password input.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-onDotConnect(callback: import('../api/@ohos.base').Callback<number>): PatternLockAttribute--><!--Device-PatternLockAttribute-onDotConnect(callback: import('../api/@ohos.base').Callback<number>): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;number&gt; | Yes | Triggered when a grid dot is selected during password input. The callback parameter is the index of the selected grid dot (the dots in the first row are numbered 0, 1, and 2 from left to right; the dots in the second row are numbered 3, 4, and 5 from left to right; the dots in the third row are numbered 6, 7, and 8 from left to right). |

## onPatternComplete

```TypeScript
onPatternComplete(callback: (input: Array<number>) => void)
```

Invoked when the pattern password input is complete.

> **NOTE:** 
> 
> This callback is triggered when password input ends and returns the complete password array. Relationship with
> [onDotConnect](#ondotconnect): onDotConnect is triggered in real time when each dot is
> selected, while onPatternComplete is triggered when input ends. The two can be used together to implement real-
> time feedback and final verification.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-onPatternComplete(callback: (input: Array<number>) => void): PatternLockAttribute--><!--Device-PatternLockAttribute-onPatternComplete(callback: (input: Array<number>) => void): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (input: Array&lt;number&gt;) =&gt; void | Yes | Array of digits representing the indices of the selected grid dots, in the order they were connected. Grid dots are indexed row-wise from top to bottom, left to right: The first row contains indices 0, 1, 2; the second row 3, 4, 5; and the third row 6, 7, 8. |

## pathColor

```TypeScript
pathColor(value: ResourceColor)
```

Sets the color of the connecting lines. If this attribute is not set, the default line color is **'#33182431'** (dark gray with 20% opacity).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-pathColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-pathColor(value: ResourceColor): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the line. |

## pathStrokeWidth

```TypeScript
pathStrokeWidth(value: number | string)
```

Sets the width of the connecting lines. If this attribute is not set, the default line width is **12vp**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-pathStrokeWidth(value: number | string): PatternLockAttribute--><!--Device-PatternLockAttribute-pathStrokeWidth(value: number | string): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Width of the line.<br>Unit: vp <br>Value range: (0, sideLength/3]. If the value is set to 0 or a negative number, the line is not displayed. If the value exceeds the maximum, the maximum value is used. |

## regularColor

```TypeScript
regularColor(value: ResourceColor)
```

Sets the fill color of the grid dots in the unselected state. If this attribute is not set, the default fill color is **'#ff182431'** (dark gray).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-regularColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-regularColor(value: ResourceColor): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the unselected state. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the fill color of the grid dots in the selected state. If this attribute is not set, the default fill color is **'#ff182431'** (dark gray).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-selectedColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-selectedColor(value: ResourceColor): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the selected state. |

## sideLength

```TypeScript
sideLength(value: Length)
```

Sets the width and height of the component (the width and height are equal). If the value is set to **0** or a negative number, the component is not displayed. If this attribute is not set, the default width and height are **288vp**.

> **NOTE:** 
> 
> When the **PatternLock** component has the universal attribute [aspectRatio](arkts-arkui-common-comp-commonmethod-c.md#aspectratio) set
> and the ratio is not equal to 1 (the component is constrained to a rectangle), the nine‑grid pattern is still
> drawn as a square, which exceeds the component's bounds.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PatternLockAttribute-sideLength(value: Length): PatternLockAttribute--><!--Device-PatternLockAttribute-sideLength(value: Length): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width and height of the component.<br>Value range: greater than 0. <br>If the value is set to 0 or a negative number, the component is not displayed. |

## skipUnselectedPoint

```TypeScript
skipUnselectedPoint(skipped: boolean)
```

Sets whether unselected grid dots are skipped when the password path passes over them. If this API is not used to set it, unselected grid dots are selected by default when the password path passes over them.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-PatternLockAttribute-skipUnselectedPoint(skipped: boolean): PatternLockAttribute--><!--Device-PatternLockAttribute-skipUnselectedPoint(skipped: boolean): PatternLockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| skipped | boolean | Yes | Whether to skip the selection of unselected grid dots when the password path passes through them.<br>true: skip the selection; false: select automatically. |
