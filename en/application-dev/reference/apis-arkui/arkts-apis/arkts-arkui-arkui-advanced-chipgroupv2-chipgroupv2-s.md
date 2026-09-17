# ChipGroupV2

Defines chipGroupV2.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Build function for ChipGroupV2

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## $items

```TypeScript
$items?: Callback<ChipGroupV2Items>
```

Two-way binding callback method for ChipV2 item.

**Type:** Callback&lt;[ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md)&gt;

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## $selectedIndexes

```TypeScript
$selectedIndexes?: Callback<Array<number>>
```

Two-way binding callback method for selected ChipV2 item indexes.

**Type:** Callback&lt;Array&lt;number&gt;&gt;

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipGroupPadding

```TypeScript
chipGroupPadding?: ChipGroupV2Padding
```

ChipGroupV2 padding (only support top and bottom).

**Type:** [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupV2Space
```

Left and right inner margins and spacing between ChipV2.

**Type:** [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupV2Items
```

ChipV2 item.

**Type:** [ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md)

**Since:** 26.0.0

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemStyle

```TypeScript
itemStyle?: ChipGroupV2ItemStyle
```

ChipV2 item style.

**Type:** [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

Support multiple ChipV2 item selection.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

Callback method when the chipV2 status changes

**Type:** Callback&lt;Array&lt;number&gt;&gt;

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes?: Array<number>
```

Selected ChipV2 item indexes.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

The builder function which will be rendered in the suffix of ChipGroupV2.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
