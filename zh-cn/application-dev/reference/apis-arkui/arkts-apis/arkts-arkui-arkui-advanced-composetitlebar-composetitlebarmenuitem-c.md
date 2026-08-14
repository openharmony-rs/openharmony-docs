# ComposeTitleBarMenuItem

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export declare class ComposeTitleBarMenuItem--><!--Device-unnamed-export declare class ComposeTitleBarMenuItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

标题栏右侧自定义按钮的无障碍描述，用于向用户详细解释组件功能和操作后果。组件被选中时，系统先播报文本属性，再播报无障碍描述内容。item属性不支持设置该属性。 默认值为“单指双击即可执行”。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-accessibilityDescription?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

标题栏右侧自定义按钮无障碍重要性，控制当前项是否可被无障碍辅助服务识别。仅适用于menuItems中的项，不适用于item参数。 支持的值为： "auto"：等同于"yes"。 "yes"：可被无障碍辅助服务识别。 "no"：不可被无障碍辅助服务识别。 "no-hide-descendants"：当前项及其子组件均不可被识别。 默认值："auto"。item参数不支持设置该属性。

**类型：** string

**默认值：** "auto".The options are as follows:<br/> "auto":The value is converted to "yes" or "no" based on the component. "yes": the current component is selectable for the accessibility service. "no": The current component is not selectable for the accessibility service. "no-hide-descendants":The current component and all its child components are not selectable<br/> for the accessibility service.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-accessibilityLevel?: string--><!--Device-ComposeTitleBarMenuItem-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

标题栏右侧自定义按钮的无障碍文本。当组件无文本属性时，屏幕朗读不会播报，设置此属性后屏幕朗读可播报该内容，帮助用户了解选中的组件。item属性不支持设置该属性。 默认值：有label时默认值为当前项label属性内容，未设置label时默认值为空字符串。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-accessibilityText?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

点击菜单项时触发的回调函数。item参数不支持触发action事件。

**类型：** () =&gt; void

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-action?: () => void--><!--Device-ComposeTitleBarMenuItem-action?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

是否启用。默认值：false。 true表示启用，false表示禁用。 item参数不支持触发isEnabled属性。

**类型：** boolean

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-isEnabled?: boolean--><!--Device-ComposeTitleBarMenuItem-isEnabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

图标标签描述，用于设置图标的辅助文本信息。当未设置accessibilityText时，label可作为无障碍文本的默认值。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-label?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-label?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源，优先级大于value，item左侧头像不支持设置该属性。不设置时使用value属性指定的图标资源。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-ComposeTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

图标资源。如果同时设置了symbolStyle属性，则symbolStyle优先级更高。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBarMenuItem-value: ResourceStr--><!--Device-ComposeTitleBarMenuItem-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

