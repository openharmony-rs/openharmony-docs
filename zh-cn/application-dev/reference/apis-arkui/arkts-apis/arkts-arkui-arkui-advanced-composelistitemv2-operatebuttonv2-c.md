# OperateButtonV2

列表项右侧按钮元素的类型。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class OperateButtonV2--><!--Device-unnamed-export declare class OperateButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheckV2Options, ComposeListItemV2, IconTypeV2, OperateIconV2, OperateCheckV2, OperateItemV2, OperateItemV2Options, OperateIconV2Options, OperateButtonV2, OperateButtonV2Options, ContentItemV2, ContentItemV2Options } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options?: OperateButtonV2Options)
```

OperateButtonV2的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateButtonV2-constructor(options?: OperateButtonV2Options)--><!--Device-OperateButtonV2-constructor(options?: OperateButtonV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OperateButtonV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2options-i.md) | 否 | 列表项右侧按钮属性配置。 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

列表项右侧按钮的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。

默认值:"单指双击即可执行"。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateButtonV2-public accessibilityDescription?: ResourceStr--><!--Device-OperateButtonV2-public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

列表项右侧按钮的无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。

支持的值为:

"auto":当前组件会转换"no"。

"yes":当前组件可被无障碍辅助服务所识别。

"no":当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants":当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值:"auto"

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateButtonV2-public accessibilityLevel?: string--><!--Device-OperateButtonV2-public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

列表项右侧按钮的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。

默认值:""

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateButtonV2-public accessibilityText?: ResourceStr--><!--Device-OperateButtonV2-public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
public text?: ResourceStr
```

列表项右侧按钮文字。

默认值:""

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateButtonV2-public text?: ResourceStr--><!--Device-OperateButtonV2-public text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

