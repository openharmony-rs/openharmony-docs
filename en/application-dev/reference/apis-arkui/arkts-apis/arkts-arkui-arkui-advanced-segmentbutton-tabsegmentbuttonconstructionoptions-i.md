# TabSegmentButtonConstructionOptions

```TypeScript
interface TabSegmentButtonConstructionOptions extends CommonSegmentButtonOptions
```

Creates a SegmentButtonOptions object of the tab type.

Inherits from [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md).

**Inheritance/Implementation:** TabSegmentButtonConstructionOptions extends [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)

**Since:** 11

<!--Device-unnamed-interface TabSegmentButtonConstructionOptions extends CommonSegmentButtonOptions--><!--Device-unnamed-interface TabSegmentButtonConstructionOptions extends CommonSegmentButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons: ItemRestriction<SegmentButtonTextItem>
```

Button information.

**Type:** [ItemRestriction](arkts-arkui-itemrestriction-t.md)&lt;[SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabSegmentButtonConstructionOptions-buttons: ItemRestriction<SegmentButtonTextItem>--><!--Device-TabSegmentButtonConstructionOptions-buttons: ItemRestriction<SegmentButtonTextItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
