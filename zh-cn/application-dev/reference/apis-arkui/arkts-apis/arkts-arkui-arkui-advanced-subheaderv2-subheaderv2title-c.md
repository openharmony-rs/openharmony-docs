# SubHeaderV2Title

标题设置项。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: SubHeaderV2TitleOptions)
```

标题内容信息SubHeaderV2Title构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubHeaderV2TitleOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2titleoptions-i.md) | 是 | 标题内容信息。 |

## id

```TypeScript
id?: string
```

标题id。需要为标题设置id的时候设置此参数，缺省时不设置此参数。默认值：undefined，表示不设置标题id。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

The first line text of content area.

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
primaryTitleModifier?: TextModifier
```

Text modifier for primary title.

**类型：** TextModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

The secondary line text of content area.

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
secondaryTitleModifier?: TextModifier
```

Text modifier for secondary title.

**类型：** TextModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleAccessibilityText

```TypeScript
titleAccessibilityText?: ResourceStr
```

设置标题自定义朗读内容。默认值：undefined值为undefined时，默认朗读组件显示的标题内容。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
