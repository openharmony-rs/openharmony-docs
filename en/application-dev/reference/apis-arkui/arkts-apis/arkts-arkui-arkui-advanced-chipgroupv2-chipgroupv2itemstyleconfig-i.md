# ChipGroupV2ItemStyleConfig

```TypeScript
export interface ChipGroupV2ItemStyleConfig
```

Defines the common attribute configuration of **ChipV2**.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Background color of **ChipV2**.

Default value: **$r('sys.color.ohos_id_color_button_normal')**

If the value is **undefined**, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, no material style is applied.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Font color of **ChipV2**.

Default value: **$r('sys.color.ohos_id_color_text_primary')**

If the value is **undefined**, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ColorMetrics
```

Background color of **ChipV2** when selected. After this attribute is set, when the **ChipV2** is selected, the background is filled with this color, replacing the **backgroundColor** in the unselected state.

Default value: **$r('sys.color.ohos_id_color_emphasize')**

If the value is **undefined**, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
selectedBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component in the selected state. After this attribute is set, when the **ChipV2** is selected, this material style is applied, replacing the **backgroundSystemMaterial** in the unselected state. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, no material style is applied.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ColorMetrics
```

Font color of **ChipV2** when selected. After this attribute is set, when the **ChipV2** is selected, the label text is displayed in this color, replacing the **fontColor** in the unselected state.

Default value: **$r('sys.color.ohos_id_color_text_primary_contrary')**

If the value is **undefined**, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipV2Size | SizeT<LengthMetrics>
```

Size of **ChipV2**. When using this attribute, import the **ChipV2Size** type from the **ChipV2** component.

Default value: **ChipV2Size.NORMAL**

If the value is **undefined**, the default value is used.

**Type:** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) &#124; [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
