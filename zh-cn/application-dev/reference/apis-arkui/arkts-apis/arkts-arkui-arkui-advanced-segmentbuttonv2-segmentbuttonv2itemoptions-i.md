# SegmentButtonV2ItemOptions

配置分段按钮选项参数。
> **说明**  
>  
> 1. 当配置`symbol`和`icon`时，`symbol`的显示优先级更高。  
>  
> 2. 当`symbol`和`symbolModifier`同时设置HM Symbol资源时，`symbolModifier`设置的资源具有更高的显示优先级。

**起始版本：** 18

<!--Device-unnamed-export interface SegmentButtonV2ItemOptions--><!--Device-unnamed-export interface SegmentButtonV2ItemOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OnSelectedIndexesChange, TabSegmentButtonV2, SegmentButtonV2Items, MultiCapsuleSegmentButtonV2, OnSelectedIndexChange, SegmentButtonV2ItemOptions, SegmentButtonV2Item, CapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

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

<!--Device-SegmentButtonV2ItemOptions-accessibilityDescription?: ResourceStr--><!--Device-SegmentButtonV2ItemOptions-accessibilityDescription?: ResourceStr-End-->

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

<!--Device-SegmentButtonV2ItemOptions-accessibilityLevel?: string--><!--Device-SegmentButtonV2ItemOptions-accessibilityLevel?: string-End-->

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

<!--Device-SegmentButtonV2ItemOptions-accessibilityText?: ResourceStr--><!--Device-SegmentButtonV2ItemOptions-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
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

<!--Device-SegmentButtonV2ItemOptions-enabled?: boolean--><!--Device-SegmentButtonV2ItemOptions-enabled?: boolean-End-->

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

<!--Device-SegmentButtonV2ItemOptions-icon?: ResourceStr--><!--Device-SegmentButtonV2ItemOptions-icon?: ResourceStr-End-->

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

<!--Device-SegmentButtonV2ItemOptions-iconModifier?: ImageModifier--><!--Device-SegmentButtonV2ItemOptions-iconModifier?: ImageModifier-End-->

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

<!--Device-SegmentButtonV2ItemOptions-symbol?: Resource--><!--Device-SegmentButtonV2ItemOptions-symbol?: Resource-End-->

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

<!--Device-SegmentButtonV2ItemOptions-symbolModifier?: SymbolGlyphModifier--><!--Device-SegmentButtonV2ItemOptions-symbolModifier?: SymbolGlyphModifier-End-->

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

<!--Device-SegmentButtonV2ItemOptions-text?: ResourceStr--><!--Device-SegmentButtonV2ItemOptions-text?: ResourceStr-End-->

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

<!--Device-SegmentButtonV2ItemOptions-textModifier?: TextModifier--><!--Device-SegmentButtonV2ItemOptions-textModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

