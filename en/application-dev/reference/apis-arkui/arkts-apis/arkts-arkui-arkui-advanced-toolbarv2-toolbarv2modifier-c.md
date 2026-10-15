# ToolBarV2Modifier

```TypeScript
export declare class ToolBarV2Modifier
```

Provides methods for setting the toolbar height (**height**), background color (**backgroundColor**), left and right padding (**padding**, which takes effect only when the number of items is fewer than five), and whether to display the pressed state effect (**stateEffect**).

**Since:** 18

<!--Device-unnamed-export declare class ToolBarV2Modifier--><!--Device-unnamed-export declare class ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor(backgroundColor: ColorMetrics): ToolBarV2Modifier
```

Sets the background color of the toolbar. This method can be called for custom drawing.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2Modifier-backgroundColor(backgroundColor: ColorMetrics): ToolBarV2Modifier--><!--Device-ToolBarV2Modifier-backgroundColor(backgroundColor: ColorMetrics): ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backgroundColor | [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Yes | toolBarV2's backgroundColor. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | **ToolBarV2Modifier** object after setting the background color, which can be used for chained calls to further customize the toolbar style. |

## height

```TypeScript
height(height: LengthMetrics): ToolBarV2Modifier
```

Sets the height of the toolbar. This method can be called for custom drawing. This height does not include the divider height.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2Modifier-height(height: LengthMetrics): ToolBarV2Modifier--><!--Device-ToolBarV2Modifier-height(height: LengthMetrics): ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | toolBarV2's height. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | **ToolBarV2Modifier** object after setting the height, which can be used for chained calls to other methods to further customize the toolbar style. |

## padding

```TypeScript
padding(padding: LengthMetrics): ToolBarV2Modifier
```

Sets the left and right padding of the toolbar. This method can be called for custom drawing.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2Modifier-padding(padding: LengthMetrics): ToolBarV2Modifier--><!--Device-ToolBarV2Modifier-padding(padding: LengthMetrics): ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| padding | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | left and right padding. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | **ToolBarV2Modifier** object with the padding set, which can be used for chained calls to further customize the toolbar style. |

## stateEffect

```TypeScript
stateEffect(stateEffect: boolean): ToolBarV2Modifier
```

Sets whether to display the pressed state effect.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2Modifier-stateEffect(stateEffect: boolean): ToolBarV2Modifier--><!--Device-ToolBarV2Modifier-stateEffect(stateEffect: boolean): ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stateEffect | boolean | Yes | press status effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | **ToolBarV2Modifier** object with the pressed state effect set, which can be used for chained calls to other methods to further customize the toolbar style. |
