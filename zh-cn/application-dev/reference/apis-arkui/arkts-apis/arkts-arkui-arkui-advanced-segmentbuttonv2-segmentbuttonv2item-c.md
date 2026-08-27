# SegmentButtonV2Item

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: SegmentButtonV2ItemOptions)
```

构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | 是 | 分段按钮选项配置参数。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

分段按钮选项无障碍说明accessibilityDescription。默认值：""值为undefined时，按默认值处理。装饰器类型：@Trace

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

分段按钮选项无障碍重要性accessibilityLevel。默认值："auto"值为undefined时，按默认值处理。装饰器类型：@Trace

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

分段按钮选项的无障碍文本accessibilityText。默认值：""值为undefined时，按默认值处理。装饰器类型：@Trace

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

分段按钮选项是否可用。默认值：true true：可用；false：不可用。值为undefined时，按默认值处理。装饰器类型：@Trace

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

分段按钮选项图片类型图标。默认值：undefined装饰器类型：@Trace

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconModifier

```TypeScript
iconModifier?: ImageModifier
```

分段按钮选项图片类型图标属性的样式修改器。默认值：undefined装饰器类型：@Trace

**类型：** ImageModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isHybrid

```TypeScript
get isHybrid(): boolean
```

检查分段按钮选项是否已配置文本和图标。与[hasHybrid](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md#hashybrid)的区别：hasHybrid用于检查整个选项集合是否包含图文混合选项，本接口用于检查单个选 项是否已配置文本和图标。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol?: Resource
```

分段按钮选项的HM Symbol类型图标。默认值：undefined装饰器类型：@Trace

**类型：** Resource

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolModifier

```TypeScript
symbolModifier?: SymbolGlyphModifier
```

分段按钮选项HM Symbol类型图标属性样式修改器。默认值：undefined装饰器类型：@Trace

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

分段按钮选项文本。默认值：undefined装饰器类型：@Trace

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textModifier

```TypeScript
textModifier?: TextModifier
```

分段按钮选项文本属性样式修改器。默认值：undefined装饰器类型：@Trace

**类型：** TextModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
