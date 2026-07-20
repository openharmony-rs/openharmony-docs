# OperateCheck

列表右侧元素为Switch、CheckBox、Radio的类型。

**起始版本：** 10

<!--Device-unnamed-export declare class OperateCheck--><!--Device-unnamed-export declare class OperateCheck-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheck, OperateIcon, ComposeListItem, OperateItem, IconType, ContentItem, OperateButton } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

右侧Switch/CheckBox/Radio的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。

默认跟随基础组件Switch/CheckBox/Radio播报规则。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperateCheck-accessibilityDescription?: ResourceStr--><!--Device-OperateCheck-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

右侧Switch/CheckBox/Radio的无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。

支持的值为：

"auto"：当前组件会转换"no"。

"yes"：当前组件可被无障碍辅助服务所识别。

"no"：当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"

**类型：** string

**默认值：** "auto"

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperateCheck-accessibilityLevel?: string--><!--Device-OperateCheck-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

右侧Switch/CheckBox/Radio的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。

默认值：""

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperateCheck-accessibilityText?: ResourceStr--><!--Device-OperateCheck-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCheck

```TypeScript
isCheck?: boolean
```

右侧Switch/CheckBox/Radio选中状态。

isCheck默认值为false。

isCheck为true时，表示为选中。

isCheck为false时，表示为未选中。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateCheck-isCheck?: boolean--><!--Device-OperateCheck-isCheck?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: boolean) => void
```

右侧Switch/CheckBox/Radio选中状态改变时触发回调。

value为true时，表示从未选中变为选中。

value为false时，表示从选中变为未选中。

**类型：** (value: boolean) =&gt; void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateCheck-onChange?: (value: boolean) => void--><!--Device-OperateCheck-onChange?: (value: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

