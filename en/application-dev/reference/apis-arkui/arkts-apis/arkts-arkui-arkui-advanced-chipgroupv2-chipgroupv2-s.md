# ChipGroupV2

```TypeScript
export declare struct ChipGroupV2
```

The **ChipGroupV2** component provides a chip group container that supports single or multiple selection, custom styles and spacing, and custom suffix content. It is suitable for scenarios such as file or resource content categorization, tag selection, and filtering, helping you quickly build visually appealing and interactive chip group UIs.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can control component data and state more flexibly, achieving more efficient UI refresh.

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

Constructs an advanced **ChipGroupV2** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## $items

```TypeScript
$items?: Callback<ChipGroupV2Items>
```

Bidirectional binding callback for the **ChipV2** item. Pass in this callback when you need to listen for or modify the **ChipV2** item list.

Default value: **undefined**, meaning no callback is triggered.

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

Bidirectional binding callback for the selected **ChipV2** indexes. Pass in this callback when you need to listen for or modify the selected **ChipV2** indexes.

Default value: **undefined**, meaning no callback is triggered.

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

Top and bottom padding of **ChipGroupV2**, used to control the overall height. The type is [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md).

Default value: **{ top: 14, bottom: 14 }**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupV2Space
```

Left and right padding and spacing between ChipV2 items. After setting, you can adjust the left and right padding of **ChipGroupV2** and the spacing between **ChipV2** items. Increasing the spacing makes the layout looser, while decreasing it makes the layout more compact. For details, see [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md).

Default value: **{ itemSpace: 8, startSpace: 16, endSpace: 16 }**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupV2Items
```

Specific attributes of a **ChipV2**. For details, see [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md).

When the value is **undefined** or an empty array, **ChipGroupV2** does not render the internal [ChipV2](arkts-arkui-arkui-advanced-chipv2-chipv2-s.md).

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

Style of **ChipV2**, such as color and size. For details, see [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md).

Default value:

**{size: ChipV2Size.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'), selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize')}**

When the value is **undefined**, the default value is used.

The icon fill colors ([fillColor](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md) and [activatedFillColor](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md)) are consistent with the corresponding font colors: in the unselected state, **fillColor** is consistent with [fontColor](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md); in the selected state, **activatedFillColor** is consistent with [selectedFontColor](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md). To set different colors, use [prefixSymbolIcon](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) and [suffixSymbolIcon](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) when passing in **items**.

**Type:** [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

Whether to select multiple **ChipV2** items.

**true**: multiple **ChipV2** items can be selected; **false**: only a single **ChipV2** can be selected.

Default value: **false**

When the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

Callback invoked when the **ChipV2** state changes, used to respond to changes in the **ChipV2** selection state. Pass in this callback when you need to listen for **ChipV2** selection state changes.

Trigger scenario: triggered when the user taps a **ChipV2** to change its selection state, returning the array of indexes of the currently selected **ChipV2** items.

Default value: **undefined**, meaning no event is triggered.

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

Indexes of the selected **ChipV2** items.

Value range: the index value must be an integer greater than or equal to 0 and less than the length of the items array. Indexes outside this range do not take effect.

Default value: **[0]**

When the value is **undefined**, the default value is used.

When **multiple** is **false**, if **selectedIndexes** is not passed in, the first **ChipV2** is selected by default; if the passed in **selectedIndexes** has multiple elements, the **ChipV2** of the first index is selected by default.

When **multiple** is **true**, if **selectedIndexes** is not passed in, the first **ChipV2** is selected by default; if the passed in **selectedIndexes** has multiple elements, all **ChipV2** items of the corresponding indexes are selected.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

Custom builder. To display custom content on the far right of the component, configure the **suffix** attribute. When using the **suffix** attribute, reference the [ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md) API.

Default value: **undefined**, meaning no custom content is displayed on the far right.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
