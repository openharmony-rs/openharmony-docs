# SubHeaderV2OperationItemOptions

用于构建SubHeaderV2OperationItem对象。

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

选项操作事件回调，点击操作项时触发，用于执行自定义操作。默认值：() =&gt; void。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

子标题右侧操作项无障碍说明，用于为用户进一步说明当前组件。默认值：“单指双击即可执行”。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

子标题右侧操作项无障碍重要性。支持的值为："auto"：当前子标题右侧操作项由无障碍分组服务和ArkUI进行综合判断是否可被无障碍辅助服务所识别。"yes"：当前子标题右侧操作项可被无障碍辅助服务所识别。"no"：当前子标题右侧操作项不可被无障碍辅助服务所识别。"no-hide-descendants"：当前子标题右侧操作项及其所有子组件不可被无障碍辅助服务所识别。默认值：“yes”。

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

子标题右侧操作项无障碍描述。默认值：undefined

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: SubHeaderV2OperationItemType
```

操作项显示的内容。

**类型：** [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

子标题右侧操作项是否为默认焦点。true：子标题右侧操作项是默认焦点。false：子标题右侧操作项不是默认焦点。默认值：false

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
