# ComposeTitleBarV2MenuItem

菜单项类，用于定义标题栏左侧头像或右侧菜单项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ComposeTitleBarV2MenuItem--><!--Device-unnamed-export declare class ComposeTitleBarV2MenuItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(params?: ComposeTitleBarV2MenuItemParams)
```

ComposeTitleBarV2MenuItem的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-constructor(params?: ComposeTitleBarV2MenuItemParams)--><!--Device-ComposeTitleBarV2MenuItem-constructor(params?: ComposeTitleBarV2MenuItemParams)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [ComposeTitleBarV2MenuItemParams](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitemparams-i.md) | 否 | 菜单项参数对象。 |

## accessibilityDescription

```TypeScript
@Trace
  accessibilityDescription?: ResourceStr
```

标题栏右侧自定义按钮的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果 组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。 默认值："单指双击即可执行"。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityDescription?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
@Trace
  accessibilityLevel?: string
```

标题栏右侧自定义按钮无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。 支持的值为： "auto"：当前组件会根据情况转换成'yes'或'no'。 "yes"：当前组件可被无障碍辅助服务所识别。 "no"：当前组件不可被无障碍辅助服务所识别。 "no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。 默认值："auto"。

**类型：** string

**默认值：** auto .The options are as follows:<br/> "auto":The value is converted to "yes" or "no" based on the component. "yes": the current component is selectable for the accessibility service. "no": The current component is not selectable for the accessibility service. "no-hide-descendants":The current component and all its child components are not selectable<br/> for the accessibility service.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityLevel?: string--><!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
@Trace
  accessibilityText?: ResourceStr
```

标题栏右侧自定义按钮的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本 的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。 默认值：有label默认值为当前项label属性内容，没有设置label时，默认值为" "。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityText?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-@Trace  accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
@Trace
  action?: OnActionCallback
```

触发时的动作闭包，item属性不支持触发action事件。

**类型：** [OnActionCallback](../../apis-arkui/arkts-apis/arkts-arkui-onactioncallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  action?: OnActionCallback--><!--Device-ComposeTitleBarV2MenuItem-@Trace  action?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
@Trace
  isEnabled?: boolean
```

是否启用，默认启用。 isEnabled为true时，表示启用。 isEnabled为false时，表示禁用。 item属性不支持触发isEnabled属性。 默认值：true。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  isEnabled?: boolean--><!--Device-ComposeTitleBarV2MenuItem-@Trace  isEnabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
@Trace
  label?: ResourceStr
```

图标标签描述。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  label?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-@Trace  label?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源，优先级大于value，item左侧头像不支持设置该属性。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  symbolStyle?: SymbolGlyphModifier--><!--Device-ComposeTitleBarV2MenuItem-@Trace  symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
@Trace
  value: ResourceStr
```

图标资源。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2MenuItem-@Trace  value: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-@Trace  value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

