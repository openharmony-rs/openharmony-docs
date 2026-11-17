# ToolBarV2ItemOptions

```TypeScript
export interface ToolBarV2ItemOptions
```

声明ToolBarV2Item的选项。

**起始版本：** 18

<!--Device-unnamed-export interface ToolBarV2ItemOptions--><!--Device-unnamed-export interface ToolBarV2ItemOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## action

```TypeScript
action?: ToolBarV2ItemAction
```

定义点击事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-action?: ToolBarV2ItemAction--><!--Device-ToolBarV2ItemOptions-action?: ToolBarV2ItemAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

项的无障碍描述。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-accessibilityDescription?: ResourceStr--><!--Device-ToolBarV2ItemOptions-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

项的无障碍重要性级别。

**类型：** string

**默认值：** "auto"

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-accessibilityLevel?: string--><!--Device-ToolBarV2ItemOptions-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

项的无障碍文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-accessibilityText?: ResourceStr--><!--Device-ToolBarV2ItemOptions-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ToolBarV2ItemText
```

定义文本内容。

**类型：** [ToolBarV2ItemText](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtext-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-content: ToolBarV2ItemText--><!--Device-ToolBarV2ItemOptions-content: ToolBarV2ItemText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ToolBarV2ItemIconType
```

定义图标资源。

**类型：** [ToolBarV2ItemIconType](arkts-arkui-toolbarv2itemicontype-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-icon?: ToolBarV2ItemIconType--><!--Device-ToolBarV2ItemOptions-icon?: ToolBarV2ItemIconType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: ToolBarV2ItemState
```

定义项类型。

**类型：** [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-state?: ToolBarV2ItemState--><!--Device-ToolBarV2ItemOptions-state?: ToolBarV2ItemState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
