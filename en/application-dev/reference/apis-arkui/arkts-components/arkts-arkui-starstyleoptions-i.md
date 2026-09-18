# StarStyleOptions

Provides style settings for the selected, unselected, and partially selected stars in the **Rating** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## backgroundUri

```TypeScript
backgroundUri: ResourceStr
```

Image path for the unselected star. You can use the default system image or a custom image.

Resource configuration is supported since API version 20. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## foregroundUri

```TypeScript
foregroundUri: ResourceStr
```

Image path for the selected star. You can use the default system image or a custom image.

Resource configuration is supported since API version 20. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryUri

```TypeScript
secondaryUri?: ResourceStr
```

Image path for the partially selected star. You can use the default system image or a custom image.

Resource configuration is supported since API version 20. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
