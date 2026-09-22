# PolylineOptions

```TypeScript
declare interface PolylineOptions
```

Describes the options of the polyline.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

Height, in the range [0, +∞).

Default value: **0**

Default unit: vp

If the given value is less than 0, the default value is used. The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width, in the range [0, +∞).

Default value: **0**

Default unit: vp

If the given value is less than 0, the default value is used. The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
