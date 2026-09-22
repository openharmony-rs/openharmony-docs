# ChipGroup

```TypeScript
export declare struct ChipGroup
```

The **ChipGroup** component provides chip group capabilities, supporting single-selection or multi-selection modes, customizable styles, icons, and spacing, as well as selected state management and event callbacks. It is suitable for various scenarios such as file categorization, resource filtering, tag selection, and content grouping, helping developers quickly implement selection functionality while delivering a consistent visual and interactive experience.

> **NOTE:** 
> 
> 1. For the **selectedIndexes** and **multiple** APIs, when **multiple** is set to **false**, if
> **selectedIndexes** is not passed in, the first chip is selected by default. If the provided **selectedIndexes**
> contains more than one element, the chip at the first index is selected by default.
> 
> 2. When using the **suffix** API, the **IconGroupSuffix** API must be imported. If it is not passed in,
> **suffix** will be empty.
> 
> 3. The icon fill colors (**fillColor** and **activatedFillColor**) should be consistent with the font color (**fontColor**). If different colors are needed, use **prefixSymbol** when passing in [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md).

**Since:** 12

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects and can affect the [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) visual properties of the component. When a system material with auto-invert is set, if **fontColor** uses a system-predefined invertible color resource (such as `$r('sys.color.font_primary')`), the color automatically adapts to the inverted color of the material background color. When **backgroundSystemMaterial** is set, **backgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material.

Default value: **undefined**

If **undefined**, no material style is applied.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipGroupPadding

```TypeScript
chipGroupPadding?: ChipGroupPaddingOptions
```

Top and bottom padding of the **ChipGroup**, used to control the overall height. The type is [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md). Pass this parameter when you need to adjust the vertical space occupied by the **ChipGroup** component or match specific UI design requirements.

Default value: **{ top: 14, bottom: 14 }**

Unit: vp

If **undefined**, the default value is used.

**Type:** [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupSpaceOptions
```

Left and right padding and spacing between chips. For details, see [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md). Pass this parameter when the default spacing cannot meet the layout requirements or when the spacing between chips needs to be adjusted according to the UI design.

Default value: **{ itemSpace: 8, startSpace: 16, endSpace: 16 }**

Unit: vp

If **undefined**, the default value is used.

**Type:** [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupItemOptions[]
```

Specific properties of each chip. For details, see [ChipGroupItemOptions[]][ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md).

If **undefined**, ChipGroup is empty by default.

**Type:** [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md)[]

**Since:** 12

**Decorator:** @Require, @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemStyle

```TypeScript
itemStyle?: ChipItemStyle
```

Style of the chip, such as color and size. For details, see [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md). Pass this parameter when you need to customize the appearance of the chip, such as changing the background color, font color, and size.

Default value:

**{size: ChipSize.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'), selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize')}**

If **undefined**, the default value is used.

**Type:** [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

Whether to select multiple chips.

**true**: Multiple chips can be selected, which applies to scenarios where multiple options need to be selected at the same time, such as multi-tag selection and multi-condition filtering. **false**: Only a single chip can be selected, which applies to single-selection scenarios, such as single-item selection.

Default value: **false**

If **undefined**, the default value is used.

**Type:** boolean

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

Callback invoked when the chip state changes, used to listen for changes in the chip selected state. This callback is triggered after the **selectedIndexes** attribute is updated. Developers can obtain the latest selected state in the callback and perform corresponding operations, such as updating the UI, saving selected data, and triggering business logic. Pass this parameter when you need to listen for the user's chip selection operation and execute the corresponding business logic. If not passed, notifications of chip state changes cannot be received.

If **undefined**, this callback is not triggered.

**Type:** Callback&lt;Array&lt;number&gt;&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
selectedBackgroundSystemMaterial?: uiMaterial.Material
```

System material style for the selected state of the component. Different materials have different effects and can affect the [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) visual properties of the component when selected. When a system material with auto-invert is set, if **selectedFontColor** uses a system-predefined invertible color resource (such as `$r('sys.color.font_primary')`), the color automatically adapts to the inverted color of the material background color. When **selectedBackgroundSystemMaterial** is set, **selectedBackgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material.

Default value: **undefined**

If **undefined**, no material style is applied to the selected state.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes?: Array<number>
```

Indexes of the selected chips, counted from 0.

Value range: The index value is a non-negative integer and cannot exceed the length of the **items** array minus 1.

If a negative number, an index value beyond the array range, or a non-integer is passed, the index value does not take effect.

Default value: **[0]**

If **multiple** is **false** and **selectedIndexes** is an empty array, the first chip is selected by default. If **selectedIndexes** contains multiple elements, only the first index takes effect.

If **undefined**, the default value is used.

**Type:** Array&lt;number&gt;

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

Used to customize a builder. To display custom content on the rightmost side of the component, configure the **suffix** attribute. When using the **suffix** attribute, reference the [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) API.

When not passed by default, there is no suffix.

If **undefined**, there is no suffix.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
