# ContentItem

列表左侧显示的图标、图标大小以及中间元素文字内容。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## description

```TypeScript
description?: ResourceStr
```

中间元素的描述内容。默认不设置或设置为undefined，描述内容不显示。  
**文字处理规则：** 文本超长后无限换行显示。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

左侧元素的图标资源。需同时设置iconStyle才显示图标；与symbolStyle同时设置时，优先显示Symbol图标。默认不设置或设置为undefined，icon图标资源不显示。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconType
```

左侧元素的图标样式。需同时设置icon或symbolStyle才显示图标。默认不设置或设置为undefined，icon图标资源不显示。

**类型：** [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText?: ResourceStr
```

中间元素的标题内容。默认不设置或设置为undefined，标题内容不显示。  
**文字处理规则：** 文本超长后无限换行显示。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

中间元素的副标题内容。默认不设置或设置为undefined，副标题内容不显示。  
**文字处理规则：** 文本超长后无限换行显示。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

左侧元素的Symbol图标样式。需同时设置iconStyle才显示图标；与icon同时设置时，优先显示Symbol图标。默认不设置或设置为undefined，Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
