# ChipGroupV2ItemStyle

```TypeScript
export declare class ChipGroupV2ItemStyle
```

Defines the common attribute class of **ChipV2**.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ChipGroupV2ItemStyle--><!--Device-unnamed-export declare class ChipGroupV2ItemStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemStyleConfig)
```

A constructor used to create a **ChipGroupV2ItemStyle** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)--><!--Device-ChipGroupV2ItemStyle-constructor(config: ChipGroupV2ItemStyleConfig)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | Yes | Style configuration of the **ChipGroupV2** item. |

## backgroundColor

```TypeScript
public backgroundColor?: ColorMetrics
```

Background color of **ChipV2**.

Default value: **$r('sys.color.ohos_id_color_button_normal')**

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public backgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public backgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
public backgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, no material style is applied.

Decorator: **@Trace**

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-public backgroundSystemMaterial?: uiMaterial.Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
public fontColor?: ColorMetrics
```

Font color of **ChipV2**.

Default value: **$r('sys.color.ohos_id_color_text_primary')**

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public fontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public fontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
public selectedBackgroundColor?: ColorMetrics
```

Background color of **ChipV2** when selected. After this attribute is set, when the **ChipV2** is selected, the background is filled with this color, replacing the **backgroundColor** in the unselected state.

Default value: **$r('sys.color.ohos_id_color_emphasize')**

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public selectedBackgroundColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public selectedBackgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
public selectedBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component in the selected state. After this attribute is set, when the **ChipV2** is selected, this material style is applied, replacing the **backgroundSystemMaterial** in the unselected state. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, no material style is applied.

Decorator: **@Trace**

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public selectedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2ItemStyle-public selectedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
public selectedFontColor?: ColorMetrics
```

Font color of **ChipV2** when selected. After this attribute is set, when the **ChipV2** is selected, the label text is displayed in this color, replacing the **fontColor** in the unselected state.

Default value: **$r('sys.color.ohos_id_color_text_primary_contrary')**

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public selectedFontColor?: ColorMetrics--><!--Device-ChipGroupV2ItemStyle-public selectedFontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: ChipV2Size | SizeT<LengthMetrics>
```

Size of **ChipV2**.

Default value: **ChipV2Size.NORMAL**

If the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) &#124; [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ChipGroupV2ItemStyle-public size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipGroupV2ItemStyle-public size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
