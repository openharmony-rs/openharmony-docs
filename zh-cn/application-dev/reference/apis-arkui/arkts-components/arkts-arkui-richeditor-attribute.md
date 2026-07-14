# RichEditor属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持[OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md)、
[StyledStringChangedListener](arkts-arkui-styledstringchangedlistener-i.md)、
[StyledStringChangeValue](arkts-arkui-styledstringchangevalue-i.md)和以下事件：

**继承/实现关系：** RichEditorAttribute extends [CommonMethod<RichEditorAttribute>](CommonMethod<RichEditorAttribute>)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDelete

```TypeScript
aboutToDelete(callback: Callback<RichEditorDeleteValue, boolean>)
```

输入法删除内容前，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorDeleteValue, boolean&gt; | 是 | [RichEditorDeleteValue](arkts-arkui-richeditordeletevalue-i.md)为准备删除的内容所在的文本或者图片Span信息。<br/>true:组件执行删除操作。<br/>false:组件不执行删除操作。<br/>输入法删除内容前的回调，英文预上屏点击候选词时会执行该回调。<br>**起始版本：** 12 |

## aboutToIMEInput

```TypeScript
aboutToIMEInput(callback: Callback<RichEditorInsertValue, boolean>)
```

输入法输入内容前触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorInsertValue, boolean&gt; | 是 | [RichEditorInsertValue](arkts-arkui-richeditorinsertvalue-i.md)为输入法将要输入内容信息。<br/>true:组件执行添加内容操作。<br/>false:组件不执行添加内容操作。<br/>输入法输入内容前的回调。<br>**起始版本：** 12 |

## barState

```TypeScript
barState(state: BarState)
```

设置RichEditor滚动条的显示模式。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | BarState | 是 | 输入框滚动条的显示模式。<br/>默认值：BarState.Auto |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: RichEditorSpanType, content: CustomBuilder, responseType: ResponseType | RichEditorResponseType,
    options?: SelectionMenuOptions)
```

设置自定义选择菜单。自定义菜单超长时，建议内部嵌套[Scroll](arkts-arkui-scroll.md)组件使用，避免键盘被遮挡。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | RichEditorSpanType | 是 | 菜单的类型。<br/>默认值：<br/>RichEditorSpanType.TEXT |
| content | CustomBuilder | 是 | 菜单的内容。 |
| responseType | ResponseType \| RichEditorResponseType | 是 | 菜单的响应类型。<br/> 默认值：<br/>ResponseType.LongPress<br>**起始版本：** 11 |
| options | SelectionMenuOptions | 否 | 菜单的选项。 |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

设置输入框光标、手柄颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor | 是 | 输入框光标、手柄颜色。<br/>默认值：'#007DFF' |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

设置是否开启行首标点符号压缩。

> **说明：**
>
> 行首标点符号默认不压缩。
>
> 支持压缩的标点符号，请参考[ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-paragraphstyle-i.md)的行首压缩的标点范围。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 是否开启行首标点符号压缩。<br/>true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## copyOptions

```TypeScript
copyOptions(value: CopyOptions)
```

设置组件是否支持文本内容可复制粘贴。

从API version 20开始，RichEditor组件在执行复制或剪切操作时，会将HTML格式的内容添加到剪贴板中。

- 仅支持TextSpan和ImageSpan向剪贴板中添加HTML内容，其他Span类型（如BuilderSpan、SymbolSpan、CustomSpan）则不能添加。
- 设置RichEditor组件的属性字符串时，请参考属性字符串[toHtml](arkts-arkui-styledstring-c.md#tohtml-1)接口文档，以了解支持转换为HTML的范围。

copyOptions不为CopyOptions.None时，长按组件内容，会弹出文本选择菜单。如果通过bindSelectionMenu等方式自定义文本选择菜单，则会弹出自定义的菜单。

设置copyOptions为CopyOptions.None时，禁用复制、剪切、翻译、分享、搜索、帮写功能，且不支持拖拽操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CopyOptions | 是 | 组件支持文本内容是否可复制粘贴。<br/>默认值：CopyOptions.LocalDevice |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined,
                 options?: KeyboardOptions | undefined)
```

设置自定义键盘。

当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。

自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认值。

自定义键盘无法获取焦点，但是会拦截手势事件。

默认在输入控件失去焦点时，关闭自定义键盘。

自定义键盘支持接续功能，使用
[setCustomKeyboardContinueFeature](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#setcustomkeyboardcontinuefeature23)
接口，可以设置自定义键盘之间切换时是否接续。

> **说明：**
>
> 从API version 23开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder \| ComponentContent \| undefined | 是 | 自定义键盘。 <br/>传入undefined时默认使用系统键盘。<br>**起始版本：** 23 |
| options | KeyboardOptions \| undefined | 否 | 设置自定义键盘是否支持避让功能。 <br>传入undefined时默认不支持避让。<br>**起始版本：** 23 |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

设置文本特殊实体识别配置，可配置识别类型、实体显示样式，并可选择是否开启长按预览功能。

需配合[enableDataDetector](RichEditorAttribute.enableDataDetector)一起使用，设置enableDataDetector为true时，
dataDetectorConfig的配置才能生效。

当有两个实体A、B重叠时，按以下规则保留实体：

1.&nbsp;若A&nbsp;⊂&nbsp;B，则保留B，反之则保留A。

2.&nbsp;当A&nbsp;⊄&nbsp;B且B&nbsp;⊄&nbsp;A时，若A.start&nbsp;<&nbsp;B.start，则保留A，反之则保留B。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | TextDataDetectorConfig | 是 | 文本识别配置。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置系统默认菜单的扩展项，允许配置扩展项的文本内容、图标和回调方法。

调用[disableMenuItems](../../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20)或
[disableSystemServiceMenuItems](../../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20)
接口屏蔽文本选择菜单内的系统服务菜单项时，editMenuOptions接口内回调方法[onCreateMenu](arkts-arkui-editmenuoptions-i.md#oncreatemenu-1)的入参列表中不包含被
屏蔽的菜单选项。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | EditMenuOptions | 是 | 扩展菜单选项。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enable: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | 是否开启中文与西文的自动间距。<br/>true为开启自动间距，false为不开启。<br />默认值：false |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

设置是否进行文本特殊实体识别。

该接口依赖设备底层应具有文本识别能力，否则设置不会生效。

当enableDataDetector设置为true且未指定[dataDetectorConfig](RichEditorAttribute.dataDetectorConfig)属性时，系统将默认识别所有类型的实体，
并将这些实体的color和decoration更改为预设样式：

触摸点击或鼠标右键点击实体时，会根据实体类型弹出对应的实体操作菜单，鼠标左键点击实体会直接响应菜单的第一个选项。

对addBuilderSpan的节点文本，该功能不会生效。

当copyOptions设置为CopyOptions.None时，点击实体弹出的菜单没有选择文本和复制功能。

<!--RP1--><!--RP1End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 使能文本识别。<br/>true表示使能文本特殊实体识别，false表示不使能文本特殊实体识别。<br/>默认值： false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

设置RichEditor是否支持触感反馈。

> **说明：**
>
> 从API version 20开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 控制触感反馈的开关。<br/>默认值：true。true表示开启触感反馈，false表示关闭触感反馈。<br/>**说明：**<br/>触感反馈需应用具备ohos.permission.VIBRATE权限，用户已启用触感反馈，且系统硬件支持时才会生效。 |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(isEnabled: boolean)
```

设置RichEditor通过点击以外的方式获焦时，是否主动拉起软键盘。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 通过点击以外的方式获焦时，是否主动拉起软键盘。<br/>true表示主动拉起软键盘，false表示不主动拉起软键盘。<br/>默认值： true |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启预上屏功能。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 使能预上屏功能。<br/>true表示开启，false表示不开启。<br/>默认值： true |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

设置是否启用文本选择的AI菜单功能。启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。默认启用AI菜单功能。

AI菜单功能启用时，在组件中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)中的url（打开连接）、email（新建邮件）、
phoneNumber（呼叫）、address（导航前往）、dateTime（新建日程）。

AI菜单生效时，选中范围内需包括且仅包括一个完整的AI实体，才能展示对应的选项。该菜单项与[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)中的askAI菜单项不同时出现。

本功能仅在[copyOptions](RichEditorAttribute.copyOptions)为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时生效。

该接口依赖设备底层具有文本识别能力，否则设置不会生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否启用选择文本识别，true表示启用，false表示不启用。<br>传入undefined或null时属性重置为默认值。 |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

设置软键盘输入法回车键类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | EnterKeyType | 是 | 软键盘输入法回车键类型。<br/>默认为EnterKeyType.NEW_LINE。 |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。不通过该接口设置，默认行高不基于文字实际高度自适应。

该接口依赖[RichEditorTextStyle](arkts-arkui-richeditortextstyleresult-i.md)的lineHeight属性。当lineHeight设置值小于当前字号下文本渲染出的实际高度时，
fallbackLineSpacing属性将生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 行高是否基于文字实际高度自适应。<br/>true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 |

## horizontalScrolling

```TypeScript
horizontalScrolling(enabled: Optional<boolean>)
```

设置当文本宽度超过内容区宽度时是否启用水平滚动。不通过该接口设置，默认禁用水平滚动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 是否启用水平滚动。<br/>true表示启用水平滚动，false表示禁用水平滚动，文本将自动换行。设置为undefined或null时，不启用水平滚动。 |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | Optional&lt;boolean&gt; | 是 | 是否在首行和尾行增加间距以避免文字截断。<br/>true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置键盘外观。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | Optional&lt;KeyboardAppearance&gt; | 是 | 键盘外观。<br/>默认值：KeyboardAppearance.NONE_IMMERSIVE |

## maxLength

```TypeScript
maxLength(maxLength: Optional<number>)
```

设置组件内容的最大长度。当内容（包含文本、图片、Symbol和Builder）的总长度达到此值时，将无法继续添加内容。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxLength | Optional&lt;number&gt; | 是 | 文本的最大输入字符数。<br/>默认值：Infinity，可以无限输入，支持undefined类型。<br/>**说明：** <br/>当不设置该属性或设置异常值时，取默认值，设置小数时，取整数部分。 |

## maxLines

```TypeScript
maxLines(maxLines: Optional<number>)
```

设置富文本可显示的最大行数。maxLines为可显示行数，当设置maxLines时，超出内容可滚动显示。同时设置组件高度和最大行数，组件高度优先生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxLines | Optional&lt;number&gt; | 是 | 设置富文本可显示的最大行数。maxLines为可显示行数，当设置maxLines时，超出内容可滚动显示。同时设置组件高度和最大行数，组件高度优先生效。&lt;br/&gt;默认值：UINT32_MAX，可以无限输入，支持undefined类型。 <br/>取值范围：(0, UINT32_MAX] |

## onCopy

```TypeScript
onCopy(callback: Callback<CopyEvent>)
```

复制时触发回调。开发者可以通过该方法，覆盖系统默认行为，实现图文的复制。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件，默认支持图文的复制。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;CopyEvent&gt; | 是 | 定义用户复制事件。 |

## onCut

```TypeScript
onCut(callback: Callback<CutEvent>)
```

剪切时触发回调。开发者可以通过该方法，覆盖系统默认行为，实现图文的剪切。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件，默认支持图文的剪切。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;CutEvent&gt; | 是 | 定义用户剪切事件。 |

## onDeleteComplete

```TypeScript
onDeleteComplete(callback: Callback<void>)
```

输入法删除内容后，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | 订阅输入法完成删除内容的回调。<br>**起始版本：** 12 |

## onDidChange

```TypeScript
onDidChange(callback: OnDidChangeCallback) : RichEditorAttribute
```

在组件执行增删操作后，触发回调。如果文本实际未发生增删，则不触发该回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnDidChangeCallback | 是 | 在组件执行增删操作后，触发的回调. |

## onDidIMEInput

```TypeScript
onDidIMEInput(callback: Callback<TextRange>)
```

输入法输入完成后，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**
>
> 从API version 20开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;TextRange&gt; | 是 | TextRange为输入法本次输入内容的范围。<br/>输入法完成输入时的回调。 |

## onEditingChange

```TypeScript
onEditingChange(callback: Callback<boolean>)
```

组件内容的编辑状态发生变化时触发该回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | 是 | true表示编辑态，false表示非编辑态。 |

## onIMEInputComplete

```TypeScript
onIMEInputComplete(callback: Callback<RichEditorTextSpanResult>)
```

输入法输入完成后，触发回调。

该接口仅支持返回一个文本span的信息，当编辑操作涉及返回多个文本span信息时，建议使用[onDidIMEInput](RichEditorAttribute.onDidIMEInput)接口。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorTextSpanResult&gt; | 是 | [RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md)为输入法完成输入后的文本Span信息。<br/>输入法完成输入后的回调。<br>**起始版本：** 12 |

## onPaste

```TypeScript
onPaste(callback: PasteEventCallback)
```

粘贴时，触发回调。开发者可以通过该方法，覆盖系统默认行为，实现图文的粘贴。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | PasteEventCallback | 是 | 订阅粘贴时的回调。<br>**起始版本：** 12 |

## onReady

```TypeScript
onReady(callback: Callback<void>)
```

富文本组件初始化完成后触发回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | 订阅富文本组件初始化完成的回调。<br>**起始版本：** 12 |

## onSelect

```TypeScript
onSelect(callback: Callback<RichEditorSelection>)
```

鼠标左键双击选中内容触发回调；松开鼠标左键再次触发回调。

手指长按选中内容触发回调；松开手指再次触发回调。

通过手指或鼠标连续修改选中区、三击选段场景，不回调onSelect。

需要实时感知选中区变化的场景和使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件，请使用
onSelectionChange接口。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorSelection&gt; | 是 | [RichEditorSelection](arkts-arkui-richeditorselection-i.md)为选中的所有span信息。&lt;br/&gt;选择时触发的回调。<br>**起始版本：** 12 |

## onSelectionChange

```TypeScript
onSelectionChange(callback: Callback<RichEditorRange>)
```

内容选择区域或编辑状态下的光标位置发生变化时，将触发该回调。光标位置变化时，回调中选择区域的起始和终止位置相等。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorRange&gt; | 是 | [RichEditorRange](arkts-arkui-richeditorrange-i.md)为所有内容的选择区域起始和终止位置。<br/>订阅文本选择区域发生变化或编辑状态下光标位置发生变化时触发的回调。 |

## onSubmit

```TypeScript
onSubmit(callback: SubmitCallback)
```

按下软键盘输入法回车键时触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | SubmitCallback | 是 | 订阅事件的回调。 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient> | undefined)
```

在组件绑定输入法前，触发回调。

调用[IMEClient](arkts-arkui-imeclient-i.md)的[setExtraConfig](arkts-arkui-imeclient-i.md#setextraconfig-1)方法设置输入法扩展信息。
在绑定输入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;IMEClient&gt; \| undefined | 是 | 在组件绑定输入法前触发的回调。<br>值为undefined时清除已绑定的回调事件。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<RichEditorChangeValue, boolean>) : RichEditorAttribute
```

在组件执行增删操作前，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;RichEditorChangeValue, boolean&gt; | 是 | 在组件执行增删操作前，触发的回调 |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

设置文本排版时是否使能孤字优化。不通过该接口设置，默认不使能孤字优化。

孤字优化通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在
[RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md)的wordBreak属性为非BREAK_ALL并且待排版文本首个
[TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-textstyle-i.md)的
[locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-textstyle-i.md)为“zh-Hans”或“zh-Hant”时生效。

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 段落最后一行是否使能孤字优化。<br/>true表示使能孤字优化，false表示不使能孤字优化。设置为undefined或null时，不使能孤字优化。 |

## placeholder

```TypeScript
placeholder(value: ResourceStr, style?: PlaceholderStyle)
```

设置无输入时的提示文本。

> **说明：**
>
> 从API version 18开始，该接口支持在
> [attributeModifier](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceStr | 是 | 无输入时的提示文本。 |
| style | PlaceholderStyle | 否 | 提示文本的字体样式。<br/>缺省时默认跟随主题。 |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

设置是否启用行尾标点符号悬挂。不通过该接口设置，默认标点符号不悬挂。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 是否启用行尾标点符号悬挂。true表示启用行尾标点符号悬挂，false表示不启用行尾标点符号悬挂。设置为undefined或null时，不启用标点符号悬挂。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

设置组件滚动条颜色。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 设置组件滚动条颜色。<br />默认值：'#66182431'，显示为灰色。<br />**说明：** 设置异常值时按默认值处理。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中的底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor | 是 | 文本选中的底板颜色。<br/>默认为20%不透明度。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置拖动预览样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SelectedDragPreviewStyle \| undefined | 是 | 拖动预览样式。如果设置为undefined，样式将被重置。 |

## singleLine

```TypeScript
singleLine(isEnable: boolean | undefined)
```

设置是否启用单行模式。未通过该接口设置时，默认不启用单行模式。

> **说明：**
>
> 单行模式不显示滚动条。
>
> 单行模式下换行符会显示为空格。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean \| undefined | 是 | 是否启用单行模式。<br/>true表示启用单行模式；false表示不启用单行模式。<br/>设置为undefined或null时，按照false处理，不启用单行模式。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键传递。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | Optional&lt;boolean&gt; | 是 | 是否阻止返回键。<br/>true表示阻止，false表示不阻止。<br/>默认值：true。异常值取默认值。 |

## undoStyle

```TypeScript
undoStyle(style: Optional<UndoStyle>)
```

设置撤销还原时是否保留原内容的样式。

使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构建RichEditor组件时，撤销还原时默认保留原内容样式，不受该接口设置的属性影响。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;UndoStyle&gt; | 是 | 撤销还原是否保留原样式选项。默认值：UndoStyle.CLEAR_STYLE |

