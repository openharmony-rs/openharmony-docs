# EditableTitleBarMenuItemV2

菜单项配置类。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class EditableTitleBarMenuItemV2--><!--Device-unnamed-export declare class EditableTitleBarMenuItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: EditableTitleBarMenuItemV2Options)
```

EditableTitleBarMenuItemV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-constructor(options?: EditableTitleBarMenuItemV2Options)--><!--Device-EditableTitleBarMenuItemV2-constructor(options?: EditableTitleBarMenuItemV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 菜单项配置选项。 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

可访问性描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属 性，随后播报无障碍说明属性的内容。 默认值："单指双击即可执行"。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public accessibilityDescription?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel: string
```

可访问性级别，用于控制当前项是否可被无障碍辅助服务所识别。 支持的值为： "auto"：当前组件会转换为"yes"。 "yes"：当前组件可被无障碍辅助服务所识别。 "no"：当前组件不可被无障碍辅助服务所识别。 "no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。 默认值："auto"

**类型：** string

**默认值：** 'auto'

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public accessibilityLevel: string--><!--Device-EditableTitleBarMenuItemV2-public accessibilityLevel: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

屏幕阅读器的可访问性文本。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本的内容。 默认值：有label时默认值为当前项label属性内容，没有设置label时，默认值为" "。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public accessibilityText?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
public action?: OnActionCallback
```

点击菜单项的回调函数。

**类型：** OnActionCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public action?: OnActionCallback--><!--Device-EditableTitleBarMenuItemV2-public action?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
public defaultFocus: boolean
```

是否默认获取焦点。 true：获焦。 false：不获焦。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public defaultFocus: boolean--><!--Device-EditableTitleBarMenuItemV2-public defaultFocus: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
public isEnabled: boolean
```

是否启用。 默认值：true，表示启用。 isEnabled为false时，表示禁用。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public isEnabled: boolean--><!--Device-EditableTitleBarMenuItemV2-public isEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
public label?: ResourceStr
```

长按对话框的标签文本。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public label?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public label?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol图标样式修饰器，优先级大于value。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-EditableTitleBarMenuItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: ResourceStr
```

图标资源，支持Symbol或Image。 默认值：''。

**类型：** ResourceStr

**默认值：** ''

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarMenuItemV2-public value: ResourceStr--><!--Device-EditableTitleBarMenuItemV2-public value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

