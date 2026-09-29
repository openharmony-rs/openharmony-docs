# ToolBarV2ItemOptions

```TypeScript
export interface ToolBarV2ItemOptions
```

Declare the options of ToolBarV2Item

**起始版本：** 18

<!--Device-unnamed-export interface ToolBarV2ItemOptions--><!--Device-unnamed-export interface ToolBarV2ItemOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## action

```TypeScript
action?: ToolBarV2ItemAction
```

Define the action event.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-action?: ToolBarV2ItemAction--><!--Device-ToolBarV2ItemOptions-action?: ToolBarV2ItemAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

The accessibilityDescription of item.

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

The accessibilityLevel of item.

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

The accessibilityText of item.

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

Define text content.

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

Define icon resource.

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

Define item type.

**类型：** [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2ItemOptions-state?: ToolBarV2ItemState--><!--Device-ToolBarV2ItemOptions-state?: ToolBarV2ItemState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
