# SegmentButtonV2ItemOptions

```TypeScript
export interface SegmentButtonV2ItemOptions
```

Defines segmented button item options.

> **Description**
> 
> 1. If both **symbol** and **icon** are configured, **symbol** takes precedence.
> 
> 2. If both **symbol** and **symbolModifier** are configured with HM Symbol resources, the resources specified by
> **symbolModifier** take precedence.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

[Accessibility description](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription) of the segmented button item.

Default value: **""**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the segmented button item. For details, see [accessibilityLevel](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel).

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text of the segmented button item. For details, see [accessibilityText](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext).

Default value: **""**

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the segmented button item is available.

Default value: **true**

**true**: available; **false**: unavailable.

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Image icon of the segmented button item.

Default value: **undefined**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconModifier

```TypeScript
iconModifier?: ImageModifier
```

Style modifier for the image icon of the segmented button item.

Default value: **undefined**

**Type:** [ImageModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol?: Resource
```

HM Symbol icon of the segmented button item.

Default value: **undefined**

**Type:** [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolModifier

```TypeScript
symbolModifier?: SymbolGlyphModifier
```

Style modifier for the HM Symbol icon of the segmented button item.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Text of the segmented button item.

Default value: **undefined**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textModifier

```TypeScript
textModifier?: TextModifier
```

Text modifier for the segmented button item.

Default value: **undefined**

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
