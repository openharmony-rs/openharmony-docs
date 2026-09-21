# MultiShadowOptions

```TypeScript
declare interface MultiShadowOptions
```

Defines shadow style properties.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX?: number | Resource
```

X-axis offset. Unit: vp. Default value: 5.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** 5

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: number | Resource
```

Y-axis offset. Unit: vp. Default value: 5.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** 5

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: number | Resource
```

Shadow blur radius.

The default value varies by API version.

API version 10 and earlier versions: **5**

Since API version 11: **20**

Unit: vp.

A value less than or equal to 0 is handled as the default value.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** 
- API version 10: 5
- API version 11+: 20

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
