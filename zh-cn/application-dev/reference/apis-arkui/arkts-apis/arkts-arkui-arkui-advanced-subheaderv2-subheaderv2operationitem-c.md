# SubHeaderV2OperationItem

```TypeScript
export declare class SubHeaderV2OperationItem
```

操作区的设置项。

**起始版本：** 18

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class SubHeaderV2OperationItem--><!--Device-unnamed-export declare class SubHeaderV2OperationItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## action

```TypeScript
action?: SubHeaderV2OperationItemAction
```

操作文本或图标时的回调函数。

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-action?: SubHeaderV2OperationItemAction--><!--Device-SubHeaderV2OperationItem-action?: SubHeaderV2OperationItemAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: SubHeaderV2OperationItemOptions)
```

操作项SubHeaderV2OperationItem的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-constructor(options: SubHeaderV2OperationItemOptions)--><!--Device-SubHeaderV2OperationItem-constructor(options: SubHeaderV2OperationItemOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubHeaderV2OperationItemOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md) | 是 | 操作项配置信息。用于构建SubHeaderV2OperationItem对象。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

该文本或图标的无障碍描述。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-accessibilityDescription?: ResourceStr--><!--Device-SubHeaderV2OperationItem-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

该文本或图标的无障碍重要性级别。

**类型：** string

**默认值：** "auto"。取值如下：<br>"auto"：该值根据组件转换为"yes"或"no"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被<br>无障碍辅助服务所识别。

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-accessibilityLevel?: string--><!--Device-SubHeaderV2OperationItem-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

该文本或图标的无障碍文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-accessibilityText?: ResourceStr--><!--Device-SubHeaderV2OperationItem-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: SubHeaderV2OperationItemType
```

文本内容或图标地址。

**类型：** [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md)

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-content: SubHeaderV2OperationItemType--><!--Device-SubHeaderV2OperationItem-content: SubHeaderV2OperationItemType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

设置文本或图标的默认焦点状态。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-defaultFocus?: boolean--><!--Device-SubHeaderV2OperationItem-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

子标题尾部操作项id。需要为子标题尾部操作项设置id的时候设置此参数，缺省时不设置此参数。

默认值：undefined，表示不设置子标题尾部操作项id。

**类型：** string

**起始版本：** 24

**装饰器类型：** @Trace

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-SubHeaderV2OperationItem-id?: string--><!--Device-SubHeaderV2OperationItem-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
