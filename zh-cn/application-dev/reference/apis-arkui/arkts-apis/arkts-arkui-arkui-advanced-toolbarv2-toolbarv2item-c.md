# ToolBarV2Item

```TypeScript
export declare class ToolBarV2Item
```

Declare type ToolBarV2Item

**起始版本：** 18

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2Item--><!--Device-unnamed-export declare class ToolBarV2Item-End-->

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

The accessibilityDescription of item.

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

The accessibilityLevel of item.

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

The accessibilityText of item.

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

Define text content.

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

Define icon resource.

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

Define item type.

**类型：** [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-ToolBarV2Item-state?: ToolBarV2ItemState--><!--Device-ToolBarV2Item-state?: ToolBarV2ItemState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
