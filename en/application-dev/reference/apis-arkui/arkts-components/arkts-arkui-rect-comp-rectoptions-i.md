# RectOptions

```TypeScript
declare interface RectOptions
```

Describes the drawing attributes of the **Rect** component.

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

Height, with the value range greater than or equal to 0.

Default value: **0**

Default unit: vp.

Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Length | Array<any>
```

Rounded corner radius. The radius of each of the four corners can be set separately, with the value range greater than or equal to 0.

This attribute has an effect similar to that of **radiusWidth**\/**radiusHeight**. When used together, it takes precedence over **radiusWidth**\/**radiusHeight**.

Default value: **0**

Default unit: vp.

Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; Array&lt;any&gt;

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width, with the value range greater than or equal to 0.

Default value: **0**

Default unit: vp.

Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
