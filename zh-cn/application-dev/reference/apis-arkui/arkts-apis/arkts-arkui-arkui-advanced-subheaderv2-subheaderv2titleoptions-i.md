# SubHeaderV2TitleOptions

用于构建SubHeaderV2Title对象。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

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

标题内容。当[SubHeaderV2](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2-s.md)中同时使用primaryTitle、secondaryTitle、icon属性时，primaryTitle将不会显示。默认值：undefined

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
primaryTitleModifier?: TextModifier
```

设置标题文本属性，如设置主标题颜色、字体大小、字重等。默认值：undefined

**类型：** TextModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

副标题内容。默认值：undefined

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
secondaryTitleModifier?: TextModifier
```

设置副标题文本属性，如设置副标题颜色、字体大小、字重等。默认值：undefined

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
