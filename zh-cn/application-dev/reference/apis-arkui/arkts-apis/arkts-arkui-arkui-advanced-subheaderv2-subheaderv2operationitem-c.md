# SubHeaderV2OperationItem

操作区的设置项。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## action

```TypeScript
action?: SubHeaderV2OperationItemAction
```

callback function when operate the text or icon.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: SubHeaderV2OperationItemOptions)
```

操作项SubHeaderV2OperationItem的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubHeaderV2OperationItemOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md) | 是 | 操作项配置信息。用于构建SubHeaderV2OperationItem对象。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

The accessibilityDescription of this text or icon.

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

The accessibilityLevel of this text or icon.

**类型：** string

**默认值：** "auto".The options are as follows:
"auto":The value is converted to "yes" or "no" based on the component."yes": the current component is selectable for the accessibility service."no": The current component is not selectable for the accessibility service."no-hide-descendants":The current component and all its child components are not selectable
 for the accessibility service.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

The accessibilityText of this text or icon.

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: SubHeaderV2OperationItemType
```

The content of text or the address of icon.

**类型：** [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Sets the default focus state of the text or icon.

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

子标题右侧操作项id。需要为子标题右侧操作项设置id的时候设置此参数，缺省时不设置此参数。默认值：undefined，表示不设置子标题右侧操作项id。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
