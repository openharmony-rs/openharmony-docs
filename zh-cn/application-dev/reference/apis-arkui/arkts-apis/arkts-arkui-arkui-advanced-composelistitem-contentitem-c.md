# ContentItem

列表左侧显示的图标、图标大小以及中间元素文字内容。

**起始版本：** 10

<!--Device-unnamed-export declare class ContentItem--><!--Device-unnamed-export declare class ContentItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheck, OperateIcon, ComposeListItem, OperateItem, IconType, ContentItem, OperateButton } from '@kit.ArkUI';
```

## description

```TypeScript
description?: ResourceStr
```

中间元素的描述内容。

默认不设置或设置为undefined，描述内容不显示。

**文字处理规则：** 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-description?: ResourceStr--><!--Device-ContentItem-description?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

左侧元素的图标资源。

默认不设置或设置为undefined，icon图标资源不显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-icon?: ResourceStr--><!--Device-ContentItem-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconType
```

左侧元素的图标样式。

默认不设置或设置为undefined，icon图标资源不显示。

**类型：** IconType

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-iconStyle?: IconType--><!--Device-ContentItem-iconStyle?: IconType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText?: ResourceStr
```

中间元素的标题内容。

默认不设置或设置为undefined，标题内容不显示。

**文字处理规则：** 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-primaryText?: ResourceStr--><!--Device-ContentItem-primaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

中间元素的副标题内容。

默认不设置或设置为undefined，副标题内容不显示。

**文字处理规则：** 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-secondaryText?: ResourceStr--><!--Device-ContentItem-secondaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

左侧元素的Symbol图标资源，优先级大于icon，同时设置了icon和Symbol图标，只显示Symbol图标。

默认不设置或设置为undefined，Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItem-symbolStyle?: SymbolGlyphModifier--><!--Device-ContentItem-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

