# StarStyleOptions

```TypeScript
declare interface StarStyleOptions
```

Provides style settings for the selected, unselected, and partially selected stars in the **Rating** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-declare interface StarStyleOptions--><!--Device-unnamed-declare interface StarStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## backgroundUri

```TypeScript
backgroundUri: ResourceStr
```

Image path for the unselected star. You can use the default system image or a custom image.

Since API version 20, this parameter supports **Resource** configuration. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StarStyleOptions-backgroundUri: ResourceStr--><!--Device-StarStyleOptions-backgroundUri: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## foregroundUri

```TypeScript
foregroundUri: ResourceStr
```

Image path for the selected star. You can use the default system image or a custom image.

Since API version 20, this parameter supports **Resource** configuration. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StarStyleOptions-foregroundUri: ResourceStr--><!--Device-StarStyleOptions-foregroundUri: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryUri

```TypeScript
secondaryUri?: ResourceStr
```

Image path for the partially selected star. You can use the default system image or a custom image. If this parameter is not set, **backgroundUri** is used preferentially. The effect is the same as that when only **foregroundUri** and **backgroundUri** are set.

Since API version 20, this parameter supports **Resource** configuration. For details, see [Example 3: Setting the Rating Style Through Resource Configuration](../../../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md#example-3-setting-the-rating-style-through-resource-configuration).

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StarStyleOptions-secondaryUri?: ResourceStr--><!--Device-StarStyleOptions-secondaryUri?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
