# PatternLock properties/events

```TypeScript
declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>
```

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

In addition to the [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md), the following events are supported.

**Inheritance/Implementation:** PatternLockAttribute extends CommonMethod<PatternLockAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activateCircleStyle

```TypeScript
activateCircleStyle(options: Optional<CircleStyleOptions>)
```

Sets the background circle style for the dots in a grid when they are in the activated state.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CircleStyleOptions](arkts-arkui-patternlock-comp-circlestyleoptions-i.md)&gt; | Yes | Background circle style of the dots in the activated state. |

## activeColor

```TypeScript
activeColor(value: ResourceColor)
```

Sets the fill color of the grid dot in the activated state, which is when the dot is highlighted but not selected.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the activated state.<br>Default value: **'#ff182431'** |

## autoReset

```TypeScript
autoReset(value: boolean)
```

Sets whether to allow the user to reset the component status (that is, clear the input) by touching the component again after the input is complete.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to allow the user to reset the component status (that is, clear the input) by touching the component again after the input is complete.<br>**true**: yes; **false**: no<br>Default value: **true** |

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor)
```

Sets the background color.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color. |

## circleRadius

```TypeScript
circleRadius(value: Length)
```

Sets the radius of the dots in a grid. If this attribute is set to **0** or a negative value, the default value is used.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Radius of the dots in a grid.<br>Default value: **6vp**<br>Value range: (0, sideLength/11]. If the value is less than or equal to **0**, the default value is used. If the value exceeds the maximum value, the maximum value is used. |

## onDotConnect

```TypeScript
onDotConnect(callback: import('../api/@ohos.base').Callback<number>)
```

Invoked when a grid dot is connected during pattern password input.

The callback parameter is an array of digits, where each digit represents the index of a selected grid dot, listed in the order they were connected. Grid dots are indexed row-wise from top to bottom, left to right: The first row contains indices 0, 1, 2; the second row 3, 4, 5; and the third row 6, 7, 8.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;number&gt; | Yes | Invoked when a grid dot is connected during pattern password input. |

## onPatternComplete

```TypeScript
onPatternComplete(callback: (input: Array<number>) => void)
```

Invoked when the pattern password input is complete.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (input: Array&lt;number&gt;) =&gt; void | Yes | Array of digits representing the indices of the selected grid dots, in the order they were connected. Grid dots are indexed row-wise from top to bottom, left to right: The first row contains indices 0, 1, 2; the second row 3, 4, 5; and the third row 6, 7, 8. |

## pathColor

```TypeScript
pathColor(value: ResourceColor)
```

Sets the path color.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Path color.<br>Default value: **'#33182431'** |

## pathStrokeWidth

```TypeScript
pathStrokeWidth(value: number | string)
```

Sets the width of the path stroke. If this attribute is set to **0** or a negative value, the path stroke is not displayed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Width of the path stroke.<br>Value constraint: (0, sideLength/3]. Default value: 12. <br>Unit: vp. |

## regularColor

```TypeScript
regularColor(value: ResourceColor)
```

Sets the fill color of the grid dot in the unselected state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the unselected state.<br>Default value: **'#ff182431'** |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Fill color of the grid dot in the selected state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the grid dot in the selected state.<br>Default value: **'#ff182431'** |

## sideLength

```TypeScript
sideLength(value: Length)
```

Sets the width and height (same value) of the component. If this attribute is set to **0** or a negative number, the component is not displayed.

> **NOTE:** 
> 
> When the **PatternLock** component has the universal attribute [aspectRatio](arkts-arkui-common-comp-commonmethod-c.md#aspectratio) set
> and the ratio is not equal to 1 (the component is constrained to a rectangle), the nine‑grid pattern is still
> drawn as a square, which exceeds the component's bounds.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width and height of the component. Default value: **288vp** |

## skipUnselectedPoint

```TypeScript
skipUnselectedPoint(skipped: boolean)
```

Sets whether unselected dots in the grid are automatically skipped when the password path passes over them.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| skipped | boolean | Yes | Whether unselected dots in the grid are automatically skipped when the password path passes over them.<br>**true** to skip the unselected dots when the password path passes over them; **false** otherwise. Default value: **false** |
