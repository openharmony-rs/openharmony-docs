# LineOptions

```TypeScript
interface LineOptions
```

Describes the options of the line.

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

Height.

If the value is an abnormal value or is not set, the height of the drawing area is automatically calculated based on **startPoint** and **endPoint**.

Default unit: vp

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

Width.

If the value is an abnormal value or is not set, the width of the drawing area is automatically calculated based on **startPoint** and **endPoint**.

Default unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
