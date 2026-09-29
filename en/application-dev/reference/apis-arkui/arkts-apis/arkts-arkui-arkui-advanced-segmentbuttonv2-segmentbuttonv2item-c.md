# SegmentButtonV2Item

```TypeScript
export declare class SegmentButtonV2Item
```

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class SegmentButtonV2Item--><!--Device-unnamed-export declare class SegmentButtonV2Item-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: SegmentButtonV2ItemOptions)
```

Constructs a **SegmentButtonV2ItemOptions** instance.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-constructor(options: SegmentButtonV2ItemOptions)--><!--Device-SegmentButtonV2Item-constructor(options: SegmentButtonV2ItemOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | Yes | Configuration parameters for the segmented button item. |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

[Accessibility description](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription) of the segmented button item.

Default value: **""**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-accessibilityDescription?: ResourceStr--><!--Device-SegmentButtonV2Item-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the segmented button item [accessibilityLevel](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel).

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** string

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-accessibilityLevel?: string--><!--Device-SegmentButtonV2Item-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

[Accessibility text](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext) of the segmented button item.

Default value: **""**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-accessibilityText?: ResourceStr--><!--Device-SegmentButtonV2Item-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

Whether the segmented button item is enabled.

Default value: **true**

**true**: enabled. **false**: disabled.

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-enabled: boolean--><!--Device-SegmentButtonV2Item-enabled: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Image icon of the segmented button item.

Default value: **undefined**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-icon?: ResourceStr--><!--Device-SegmentButtonV2Item-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconModifier

```TypeScript
iconModifier?: ImageModifier
```

Image icon modifier for the segmented button item.

Default value: **undefined**

**Type:** [ImageModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-iconModifier?: ImageModifier--><!--Device-SegmentButtonV2Item-iconModifier?: ImageModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isHybrid

```TypeScript
get isHybrid(): boolean
```

Checks whether the segmented button item has text and icon configured. Difference from [hasHybrid](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md#hashybrid): **hasHybrid** checks whether the component contains mixed icon and text items, while this API checks whether a single item has text and icon configured.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-get isHybrid(): boolean--><!--Device-SegmentButtonV2Item-get isHybrid(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol?: Resource
```

HM Symbol icon of the segmented button item.

Default value: **undefined**

**Type:** [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-symbol?: Resource--><!--Device-SegmentButtonV2Item-symbol?: Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolModifier

```TypeScript
symbolModifier?: SymbolGlyphModifier
```

HM Symbol icon modifier for the segmented button item.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-symbolModifier?: SymbolGlyphModifier--><!--Device-SegmentButtonV2Item-symbolModifier?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Text of the segmented button item.

Default value: **undefined**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-text?: ResourceStr--><!--Device-SegmentButtonV2Item-text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textModifier

```TypeScript
textModifier?: TextModifier
```

Text modifier for the segmented button item.

Default value: **undefined**

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SegmentButtonV2Item-textModifier?: TextModifier--><!--Device-SegmentButtonV2Item-textModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
