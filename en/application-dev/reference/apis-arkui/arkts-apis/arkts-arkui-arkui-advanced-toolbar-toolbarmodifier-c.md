# ToolBarModifier

```TypeScript
export declare class ToolBarModifier
```

Provides methods for setting the toolbar height, background color, left and right padding (takes effect only when the number of items is less than 5), and whether to display the pressed state (**stateEffect**).

**Since:** 13

<!--Device-unnamed-export declare class ToolBarModifier--><!--Device-unnamed-export declare class ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor(backgroundColor: ResourceColor): ToolBarModifier
```

Sets the toolbar background color.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarModifier-backgroundColor(backgroundColor: ResourceColor): ToolBarModifier--><!--Device-ToolBarModifier-backgroundColor(backgroundColor: ResourceColor): ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backgroundColor | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Toolbar background color.<br>Default value: **$r('sys.color.ohos_id_color_toolbar_bg')** |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | Returns the current **ToolBarModifier** object, which supports chained calls. |

## height

```TypeScript
height(height: LengthMetrics): ToolBarModifier
```

Sets the toolbar height. This height does not include the divider line height.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarModifier-height(height: LengthMetrics): ToolBarModifier--><!--Device-ToolBarModifier-height(height: LengthMetrics): ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | Height of the toolbar.<br>The default height of the toolbar is 56 vp, which does not include the divider. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | Returns the current **ToolBarModifier** object, which supports chained calls. |

## padding

```TypeScript
padding(padding: LengthMetrics): ToolBarModifier
```

Sets the left and right padding of the toolbar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarModifier-padding(padding: LengthMetrics): ToolBarModifier--><!--Device-ToolBarModifier-padding(padding: LengthMetrics): ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| padding | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | Left and right padding of the toolbar. Takes effect only when the number of items is less than 5.<br>By default, the toolbar padding is 24 vp when the number of items is less than 5, and 0 vp when the number of items is 5 or more. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | Returns the current **ToolBarModifier** object, which supports chained calls. |

## stateEffect

```TypeScript
stateEffect(stateEffect: boolean): ToolBarModifier
```

Sets whether to display the pressed state effect.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarModifier-stateEffect(stateEffect: boolean): ToolBarModifier--><!--Device-ToolBarModifier-stateEffect(stateEffect: boolean): ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stateEffect | boolean | Yes | Whether to display the pressed state effect on the toolbar.<br>The value **true** means to display the pressed state effect on the toolbar, and **false** means the opposite. <br>Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | Returns the current **ToolBarModifier** object, which supports chained calls. |
