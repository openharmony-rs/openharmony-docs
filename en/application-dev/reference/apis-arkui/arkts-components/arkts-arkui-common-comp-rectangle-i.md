# Rectangle

```TypeScript
declare interface Rectangle
```

The data type used to describe a rectangular area.

> **NOTE:** 
> 
> - **x** and **y** can be set to a positive or negative percentage value. For example, when **x** is set to
> **'100%'**, the touch target is the offset from the right edge of the component by the component's width. When
> **x** is set to **'-100%'**, the touch target is the offset from the left edge of the component by the component's
> width. When **y** is set to **'100%'**, the touch target is the offset from the bottom edge of the component by the
> component's height. When **y** is set to **'-100%'**, the touch target is the offset from the top edge of the
> component by the component's height.
> 
> - **width** and **height** can only be set to positive percentage values. When **width** is set to **'100%'**, the width of the touch target is equal to that of the component. For example, if the width of a component is 100 vp,
> **'100%'** indicates that the width of the touch target is also 100 vp. When **height** is set to **'100%'**, the
> height of the touch target is equal to that of the component.
> 
> - The percentage is measured relative to the component itself.
> 
> - When the parent component has [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) set to **true**, child component interaction is affected by the parent component's response region. Children outside the parent component's response region won't respond to gestures or events.
> 
> - **width** and **height** do not support **calc()** dynamic calculations.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

Height of the touch target.

Default value: **'100%'**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width of the touch target.

Default value: **'100%'**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: Length
```

X coordinate of the touch point relative to the upper left corner of the component.

Default value: **0vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: Length
```

Y coordinate of the touch point relative to the upper left corner of the component.

Default value: **0vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
