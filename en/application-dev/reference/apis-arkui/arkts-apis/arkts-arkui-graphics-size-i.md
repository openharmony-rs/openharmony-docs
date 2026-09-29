# Size

```TypeScript
export interface Size
```

Returns the width and height of the component. The default unit is vp, but APIs that use the Size type may specify a different unit, in which case the unit specified by the API takes precedence.

**Since:** 11

<!--Device-unnamed-export interface Size--><!--Device-unnamed-export interface Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height: number
```

Height of the component.

Unit: vp.

Value range: [0, +∞).

A negative value is treated as the default value.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Size-height: number--><!--Device-Size-height: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

Width of the component.

Unit: vp.

Value range: [0, +∞).

A negative value is treated as the default value.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Size-width: number--><!--Device-Size-width: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
