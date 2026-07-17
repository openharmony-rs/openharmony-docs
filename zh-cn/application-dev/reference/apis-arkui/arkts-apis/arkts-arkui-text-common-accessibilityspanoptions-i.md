# AccessibilitySpanOptions

Span的无障碍朗读功能属性。

**起始版本：** 23

<!--Device-unnamed-declare interface AccessibilitySpanOptions--><!--Device-unnamed-declare interface AccessibilitySpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

无障碍说明属性。此描述用于向用户详细解释当前组件，开发人员应提供详尽的文本说明，以协助用户理解即将执行的操作及其后果，尤其当这些后果无法仅从组件的属性和无障碍文本中直接获取时。

默认值：''

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilitySpanOptions-accessibilityDescription?: ResourceStr--><!--Device-AccessibilitySpanOptions-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

无障碍重要性。用于设置组件是否可被无障碍辅助服务识别。

支持取值如下：

"auto"：当前组件由无障碍辅助服务和ArkUl进行综合判断组件是否可被无障碍辅助服务所识别。

"yes"：当前组件可被无障碍辅助服务识别。

"no"：当前组件不可被无障碍辅助服务识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"

值为undefined时，按默认值处理。

**说明：**

当accessibilityLevel设置成"auto"时，组件是否可被无障碍辅助服务所识别取决于以下多方面因素：

1. 组件是否可被识别由无障碍辅助服务内部判断，自行选择。2. 若组件的父组件accessibilityGroup属性中isGroup设置为true，无障碍服务将不再关注其子组件内容，组件不可被无障碍辅助服务所识别。3. 若组件的父组件accessibilityLevel属性设置为"no-hide-descendants"，组件不可被无障碍辅助服务所识别。

**类型：** string

**默认值：** "auto".

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilitySpanOptions-accessibilityLevel?: string--><!--Device-AccessibilitySpanOptions-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

无障碍文本属性。组件无文本属性时，屏幕朗读选中此组件不会播报。设置该属性后可为此类组件设置无障碍文本，屏幕朗读时将播报该文本，帮助使用者明确选中了什么组件。

默认值：''

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilitySpanOptions-accessibilityText?: ResourceStr--><!--Device-AccessibilitySpanOptions-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

