# ContentItemV2

列表左侧显示的图标、图标大小以及中间元素文字内容。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class ContentItemV2--><!--Device-unnamed-export declare class ContentItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheckV2Options, ComposeListItemV2, IconTypeV2, OperateIconV2, OperateCheckV2, OperateItemV2, OperateItemV2Options, OperateIconV2Options, OperateButtonV2, OperateButtonV2Options, ContentItemV2, ContentItemV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ContentItemV2Options)
```

ContentItemV2的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)--><!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | 否 | 列表左侧属性配置。 |

## description

```TypeScript
public description?: ResourceStr
```

中间元素的描述内容。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public description?: ResourceStr--><!--Device-ContentItemV2-public description?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
public icon?: ResourceStr
```

左侧元素的图标资源。

默认不设置或设置为undefined，表示不显示icon图标资源。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public icon?: ResourceStr--><!--Device-ContentItemV2-public icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
public iconStyle?: IconTypeV2
```

左侧元素的图标样式。

默认不设置或设置为undefined，表示不显示icon图标资源。

**类型：** IconTypeV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public iconStyle?: IconTypeV2--><!--Device-ContentItemV2-public iconStyle?: IconTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
public primaryText?: ResourceStr
```

中间元素的标题内容。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public primaryText?: ResourceStr--><!--Device-ContentItemV2-public primaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
public secondaryText?: ResourceStr
```

中间元素的副标题内容。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public secondaryText?: ResourceStr--><!--Device-ContentItemV2-public secondaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

左侧元素的Symbol图标资源，优先级大于icon，同时设置了icon和Symbol图标，只显示Symbol图标。

默认不设置或设置为undefined，Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-ContentItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

