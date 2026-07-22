# SegmentButtonV2Item

**起始版本：** 18

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class SegmentButtonV2Item--><!--Device-unnamed-export declare class SegmentButtonV2Item-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OnSelectedIndexesChange, TabSegmentButtonV2, SegmentButtonV2Items, MultiCapsuleSegmentButtonV2, OnSelectedIndexChange, SegmentButtonV2ItemOptions, SegmentButtonV2Item, CapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: SegmentButtonV2ItemOptions)
```

构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-constructor(options: SegmentButtonV2ItemOptions)--><!--Device-SegmentButtonV2Item-constructor(options: SegmentButtonV2ItemOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | 是 | 分段按钮选项配置参数。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

分段按钮选项的无障碍说明[accessibilityDescription](../arkts-components/arkts-arkui-commonmethod-c.md#accessibilitydescription)。

默认值：""

值为undefined时，按默认值处理。

装饰器类型：@Trace

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-accessibilityDescription?: ResourceStr--><!--Device-SegmentButtonV2Item-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

分段按钮选项的无障碍重要性[accessibilityLevel](../arkts-components/arkts-arkui-commonmethod-c.md#accessibilitylevel)。

默认值："auto"

值为undefined时，按默认值处理。

装饰器类型：@Trace

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-accessibilityLevel?: string--><!--Device-SegmentButtonV2Item-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

分段按钮选项的无障碍文本[accessibilityText](../arkts-components/arkts-arkui-commonmethod-c.md#accessibilitytext)。

默认值：""

值为undefined时，按默认值处理。

装饰器类型：@Trace

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-accessibilityText?: ResourceStr--><!--Device-SegmentButtonV2Item-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

分段按钮选项是否可用。

默认值：true

true：可用；false：不可用。

值为undefined时，按默认值处理。

装饰器类型：@Trace

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-enabled: boolean--><!--Device-SegmentButtonV2Item-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

分段按钮选项图片类型图标。

默认值：undefined

装饰器类型：@Trace

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-icon?: ResourceStr--><!--Device-SegmentButtonV2Item-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconModifier

```TypeScript
iconModifier?: ImageModifier
```

分段按钮选项图片类型图标属性的样式修改器。

默认值：undefined

装饰器类型：@Trace

**类型：** ImageModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-iconModifier?: ImageModifier--><!--Device-SegmentButtonV2Item-iconModifier?: ImageModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isHybrid

```TypeScript
get isHybrid(): boolean
```

检查分段按钮选项是否已配置文本和图标。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-get isHybrid(): boolean--><!--Device-SegmentButtonV2Item-get isHybrid(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol?: Resource
```

分段按钮选项的HM Symbol类型图标。

默认值：undefined

装饰器类型：@Trace

**类型：** Resource

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-symbol?: Resource--><!--Device-SegmentButtonV2Item-symbol?: Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolModifier

```TypeScript
symbolModifier?: SymbolGlyphModifier
```

分段按钮选项HM Symbol类型图标属性样式修改器。

默认值：undefined

装饰器类型：@Trace

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-symbolModifier?: SymbolGlyphModifier--><!--Device-SegmentButtonV2Item-symbolModifier?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

分段按钮选项文本。

默认值：undefined

装饰器类型：@Trace

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-text?: ResourceStr--><!--Device-SegmentButtonV2Item-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textModifier

```TypeScript
textModifier?: TextModifier
```

分段按钮选项文本属性样式修改器。

默认值：undefined

装饰器类型：@Trace

**类型：** TextModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonV2Item-textModifier?: TextModifier--><!--Device-SegmentButtonV2Item-textModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

