# ToolBarV2Item

```TypeScript
export declare class ToolBarV2Item
```

声明ToolBarV2Item类型。

**起始版本：** 18

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2Item--><!--Device-unnamed-export declare class ToolBarV2Item-End-->

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

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-action?: ToolBarV2ItemAction--><!--Device-ToolBarV2Item-action?: ToolBarV2ItemAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: ToolBarV2ItemOptions)
```

ToolBarV2Item的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-constructor(options: ToolBarV2ItemOptions)--><!--Device-ToolBarV2Item-constructor(options: ToolBarV2ItemOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md) | 是 | 子项信息。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

项的无障碍描述。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-accessibilityDescription?: ResourceStr--><!--Device-ToolBarV2Item-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

项的无障碍重要性级别。

**类型：** string

**默认值：** "auto"

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-accessibilityLevel?: string--><!--Device-ToolBarV2Item-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

项的无障碍文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-accessibilityText?: ResourceStr--><!--Device-ToolBarV2Item-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ToolBarV2ItemText
```

定义文本内容。

**类型：** [ToolBarV2ItemText](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtext-c.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-content: ToolBarV2ItemText--><!--Device-ToolBarV2Item-content: ToolBarV2ItemText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ToolBarV2ItemIconType
```

定义图标资源。

**类型：** [ToolBarV2ItemIconType](arkts-arkui-toolbarv2itemicontype-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-icon?: ToolBarV2ItemIconType--><!--Device-ToolBarV2Item-icon?: ToolBarV2ItemIconType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: ToolBarV2ItemState
```

定义项类型。

**类型：** [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-state?: ToolBarV2ItemState--><!--Device-ToolBarV2Item-state?: ToolBarV2ItemState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
