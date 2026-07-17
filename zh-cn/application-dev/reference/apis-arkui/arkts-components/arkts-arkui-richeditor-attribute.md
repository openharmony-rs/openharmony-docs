# RichEditor属性/事件

除支持[通用属性](./common)外，还支持以下属性：

除支持[通用事件](./common)外，还支持[OnDidChangeCallback](../arkts-apis/arkts-arkui-ondidchangecallback-t.md)、[StyledStringChangedListener](../arkts-apis/arkts-arkui-text-common-styledstringchangedlistener-i.md)、[StyledStringChangeValue](../arkts-apis/arkts-arkui-text-common-styledstringchangevalue-i.md)和以下事件：

**继承/实现关系：** RichEditorAttribute extends [CommonMethod<RichEditorAttribute>](CommonMethod<RichEditorAttribute>)

**起始版本：** 10

<!--Device-unnamed-declare class RichEditorAttribute extends CommonMethod<RichEditorAttribute>--><!--Device-unnamed-declare class RichEditorAttribute extends CommonMethod<RichEditorAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDelete

```TypeScript
aboutToDelete(callback: Callback<RichEditorDeleteValue, boolean>)
```

输入法删除内容前，触发回调。

适用于需要拦截删除操作的场景，如阻止删除关键内容、删除前保存历史记录以支持撤销等。与[onDeleteComplete](RichEditorAttribute#onDeleteComplete)形成will/did时序模式：aboutToDelete在删除前触发，onDeleteComplete在删除完成后触发；aboutToDelete返回false时，组件不执行删除操作，onDeleteComplete不会触发。两者可同时使用。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-aboutToDelete(callback: Callback<RichEditorDeleteValue, boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-aboutToDelete(callback: Callback<RichEditorDeleteValue, boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorDeleteValue, boolean> | 是 | [RichEditorDeleteValue](arkts-arkui-rich-editor-richeditordeletevalue-i.md)为准备删除的内容所在的文本或者图片Span信息。<br>true表示组件执行删除操作，false表示组件不执行删除操作。<br>输入法删除内容前的回调，英文预上屏点击候选词时会执行该回调。<br>**起始版本：** 12 |

## aboutToIMEInput

```TypeScript
aboutToIMEInput(callback: Callback<RichEditorInsertValue, boolean>)
```

输入法输入内容前触发回调。

可用于需要拦截输入内容的场景，如过滤敏感词、限制输入格式、实时校验输入合法性等。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-aboutToIMEInput(callback: Callback<RichEditorInsertValue, boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-aboutToIMEInput(callback: Callback<RichEditorInsertValue, boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorInsertValue, boolean> | 是 | [RichEditorInsertValue](arkts-arkui-rich-editor-richeditorinsertvalue-i.md)为输入法将要输入内容信息。<br>true表示组件执行添加内容操作，false表示组件不执行添加内容操作。<br>输入法输入内容前的回调。<br>**起始版本：** 12 |

## barState

```TypeScript
barState(state: BarState)
```

RichEditor滚动条的显示模式。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-barState(state: BarState): RichEditorAttribute--><!--Device-RichEditorAttribute-barState(state: BarState): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [BarState](../arkts-apis/arkts-arkui-enums-barstate-e.md) | 是 | RichEditor滚动条的显示模式。<br>默认值：BarState.Auto |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: RichEditorSpanType, content: CustomBuilder, responseType: ResponseType | RichEditorResponseType,
    options?: SelectionMenuOptions)
```

设置自定义选择菜单。支持自定义菜单风格和触发条件，适合需要深度自定义菜单的场景。自定义菜单超长时，建议内部嵌套[Scroll](./scroll)组件使用，避免键盘被遮挡。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-bindSelectionMenu(spanType: RichEditorSpanType, content: CustomBuilder, responseType: ResponseType | RichEditorResponseType,
    options?: SelectionMenuOptions): RichEditorAttribute--><!--Device-RichEditorAttribute-bindSelectionMenu(spanType: RichEditorSpanType, content: CustomBuilder, responseType: ResponseType | RichEditorResponseType,
    options?: SelectionMenuOptions): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | [RichEditorSpanType](arkts-arkui-rich-editor-richeditorspantype-e.md) | 是 | 菜单的类型。<br>默认值：RichEditorSpanType.TEXT |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 菜单的内容。 |
| responseType | ResponseType \| RichEditorResponseType | 是 | 菜单的响应类型。<br> 默认值：<br>ResponseType.LongPress<br>**起始版本：** 11 |
| options | [SelectionMenuOptions](../arkts-apis/arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | 否 | 菜单的选项。<br>当需要自定义菜单弹出/关闭回调、指定菜单类型等信息时传入此参数；不传入时，使用默认选择菜单选项配置。 |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

设置输入框光标、手柄颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-caretColor(value: ResourceColor): RichEditorAttribute--><!--Device-RichEditorAttribute-caretColor(value: ResourceColor): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入框光标、手柄颜色。<br/>默认值：'#007DFF' |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

设置是否开启行首标点符号压缩。

适用于行首标点符号需要与正文内容对齐的场景。

> **说明：**  
>  
> 行首标点符号默认不压缩。  
>  
> 支持压缩的标点符号，请参考[ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md)的行首压缩的标点范围。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否开启行首标点符号压缩。<br>true表示开启行首标点符号压缩，false表示不开启行首标点符号压缩。<br>默认值：false。<br>设置为undefined或null时，取默认值。 |

## copyOptions

```TypeScript
copyOptions(value: CopyOptions)
```

设置组件是否支持复制和粘贴文本内容。

从API version 20开始，RichEditor组件在执行复制或剪切操作时，会将HTML格式的内容添加到剪贴板中。

- 仅支持[TextSpan](arkts-arkui-rich-editor-richeditortextspanoptions-i.md)和[ImageSpan](arkts-arkui-rich-editor-richeditorimagespanoptions-i.md)向剪贴板中添加HTML内容，其他Span类型（如[BuilderSpan](arkts-arkui-rich-editor-richeditorbuilderspanoptions-i.md)、[SymbolSpan](arkts-arkui-rich-editor-richeditorsymbolspanoptions-i.md)、[CustomSpan](../arkts-apis/arkts-arkui-styled-string-customspan-c.md)）则不能添加。  
- 设置RichEditor组件的属性字符串时，请参考属性字符串[toHtml](../arkts-apis/arkts-arkui-styled-string-styledstring-c.md#tohtml-1)接口文档，以了解支持转换为HTML的范围。

copyOptions不为CopyOptions.None时，长按组件内容，会弹出文本选择菜单。如果通过[bindSelectionMenu](RichEditorAttribute#bindSelectionMenu)等方式自定义文本选择菜单，则会弹出自定义的菜单。

设置copyOptions为CopyOptions.None时，禁用复制、剪切、翻译、分享、搜索、帮写功能，且不支持拖拽操作，同时[enableDataDetector](RichEditorAttribute#enableDataDetector)的实体识别菜单和[enableSelectedDataDetector](RichEditorAttribute#enableSelectedDataDetector)的AI菜单功能将受限。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-copyOptions(value: CopyOptions): RichEditorAttribute--><!--Device-RichEditorAttribute-copyOptions(value: CopyOptions): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-enums-copyoptions-e.md) | 是 | 文本内容是否支持复制和粘贴。<br>默认值：CopyOptions.LocalDevice |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined,
                 options?: KeyboardOptions | undefined)
```

设置自定义键盘。

当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。

自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认键盘宽度。

自定义键盘无法获取焦点，但是会拦截手势事件。

默认在输入控件失去焦点时，关闭自定义键盘。

自定义键盘支持接续功能，使用[setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature-1)接口，可以设置自定义键盘之间切换时是否接续。

> **说明：**  
>  
> 从API version 23开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined,
                 options?: KeyboardOptions | undefined): RichEditorAttribute--><!--Device-RichEditorAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined,
                 options?: KeyboardOptions | undefined): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder \| ComponentContent \| undefined | 是 | 自定义键盘。 <br/>传入undefined时默认使用系统键盘。<br>**起始版本：** 23 |
| options | KeyboardOptions \| undefined | 否 | 设置自定义键盘是否支持避让功能。<br>传入undefined或省略时默认不支持避让。<br>**起始版本：** 23 |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

设置文本特殊实体识别配置，可配置识别类型、实体显示样式，并可选择是否开启长按预览功能。

需配合[enableDataDetector](RichEditorAttribute#enableDataDetector)一起使用，设置enableDataDetector为true时，dataDetectorConfig的配置才能生效。

当有两个实体A、B重叠时，按以下规则保留实体：

1.&nbsp;若A&nbsp;⊂&nbsp;B，则保留B，反之则保留A。

2.&nbsp;当A&nbsp;⊄&nbsp;B且B&nbsp;⊄&nbsp;A时，若A.start&nbsp;<&nbsp;B.start，则保留A，反之则保留B。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-dataDetectorConfig(config: TextDataDetectorConfig): RichEditorAttribute--><!--Device-RichEditorAttribute-dataDetectorConfig(config: TextDataDetectorConfig): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [TextDataDetectorConfig](../arkts-apis/arkts-arkui-text-common-textdatadetectorconfig-i.md) | 是 | 文本识别配置。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置系统默认菜单的扩展项，允许配置扩展项的文本内容、图标和回调方法。

与[bindSelectionMenu](RichEditorAttribute#bindSelectionMenu)的区别：editMenuOptions在系统默认菜单风格基础上添加扩展项，触发条件不变，适合仅需扩展菜单项的场景；bindSelectionMenu完全自定义菜单风格和触发条件，适合需要深度自定义菜单的场景。

调用[disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems-1)或[disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems-1)接口屏蔽文本选择菜单内的系统服务菜单项时，editMenuOptions接口内回调方法[onCreateMenu](../arkts-apis/arkts-arkui-text-common-editmenuoptions-i.md#oncreatemenu-1)的入参列表中不包含被屏蔽的菜单选项。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-editMenuOptions(editMenu: EditMenuOptions): RichEditorAttribute--><!--Device-RichEditorAttribute-editMenuOptions(editMenu: EditMenuOptions): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-text-common-editmenuoptions-i.md) | 是 | 扩展菜单选项。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enable: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。适用于混排中英文内容（如新闻文章、技术文档）等需要改善中西文之间阅读体验的场景。开启后，中文字符与西文字符之间将自动插入间距；关闭后不自动插入间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enableAutoSpacing(enable: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-enableAutoSpacing(enable: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否开启中文与西文的自动间距。<br>true表示开启自动间距，false表示不开启自动间距。<br>默认值：false |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

设置是否进行文本特殊实体识别，识别的类型包括电话号码、邮箱地址、网址链接、日期、地址等。具体识别类型可通过[dataDetectorConfig](RichEditorAttribute#dataDetectorConfig)属性配置。

该接口依赖设备系统具备文本实体识别能力，否则设置不会生效。

当enableDataDetector设置为true且未指定[dataDetectorConfig](RichEditorAttribute#dataDetectorConfig)属性时，系统将默认识别所有类型的实体，并将这些实体的color和decoration更改为预设样式：

触摸点击或鼠标右键点击实体时，会根据实体类型弹出对应的实体操作菜单，鼠标左键点击实体会直接响应菜单的第一个选项。

对[addBuilderSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addbuilderspan-1)的节点文本，该功能不会生效。

当copyOptions设置为CopyOptions.None时，点击实体弹出的菜单没有选择文本和复制功能。

<!--RP1--><!--RP1End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enableDataDetector(enable: boolean): RichEditorAttribute--><!--Device-RichEditorAttribute-enableDataDetector(enable: boolean): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用文本识别。<br>true表示启用文本特殊实体识别，false表示不启用文本特殊实体识别。<br>默认值： false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

设置RichEditor是否支持触感反馈。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enableHapticFeedback(isEnabled: boolean): RichEditorAttribute--><!--Device-RichEditorAttribute-enableHapticFeedback(isEnabled: boolean): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 控制触感反馈的开关。<br>默认值：true。true表示开启触感反馈，false表示关闭触感反馈。<br>**说明：**<br>触感反馈需应用具备ohos.permission.VIBRATE权限，用户已启用触感反馈，且系统硬件支持时才会生效。<br>不同设备品类对振动硬件的支持情况存在差异，无振动硬件的设备品类上触感反馈功能不可用。 |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(isEnabled: boolean)
```

设置RichEditor通过点击以外的方式获焦时，是否主动拉起软键盘。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enableKeyboardOnFocus(isEnabled: boolean): RichEditorAttribute--><!--Device-RichEditorAttribute-enableKeyboardOnFocus(isEnabled: boolean): RichEditorAttribute-End-->

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

开启后，组件内显示输入法输入过程中的拼音、笔画字符。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enablePreviewText(enable: boolean): RichEditorAttribute--><!--Device-RichEditorAttribute-enablePreviewText(enable: boolean): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用预上屏功能。<br>true表示启用，false表示不启用。<br>默认值： true |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

设置是否启用文本选择的AI菜单功能。启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。默认启用AI菜单功能。

AI菜单功能启用时，在组件中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括[TextMenuItemId](../arkts-apis/arkts-arkui-text-common-textmenuitemid-c.md)中的url（打开链接）、email（新建邮件）、phoneNumber（呼叫）、address（导航前往）、dateTime（新建日程）。

AI菜单生效时，选中范围内需包括且仅包括一个完整的AI实体，才能展示对应的选项。该菜单项与[TextMenuItemId](../arkts-apis/arkts-arkui-text-common-textmenuitemid-c.md)中的askAI菜单项不同时出现。

本功能仅在[copyOptions](RichEditorAttribute#copyOptions)为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时生效。

该接口依赖设备底层具有文本识别能力，否则设置不会生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enableSelectedDataDetector(enable: boolean | undefined): RichEditorAttribute--><!--Device-RichEditorAttribute-enableSelectedDataDetector(enable: boolean | undefined): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否启用选择文本识别，true表示启用，false表示不启用。<br>默认值：true。<br>设置为undefined或null时，取默认值。 |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

设置软键盘输入法回车键类型。

设置后，软键盘回车键的图标和触发行为将根据指定类型变化，不同EnterKeyType对应不同的回车键样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-enterKeyType(value: EnterKeyType): RichEditorAttribute--><!--Device-RichEditorAttribute-enterKeyType(value: EnterKeyType): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-text-input-enterkeytype-e.md) | 是 | 软键盘输入法回车键类型。<br>默认为EnterKeyType.NEW_LINE。<br>各枚举值适用场景请参考EnterKeyType枚举说明。 |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

在多行文字叠加场景下，设置行高是否基于文字实际高度自适应。

适用于混排不同字号文字、聊天消息气泡等需要避免文字重叠的场景。不通过该接口设置，默认行高不基于文字实际高度自适应。

该接口依赖[RichEditorTextStyle](arkts-arkui-rich-editor-richeditortextstyle-i.md)的lineHeight属性。当lineHeight设置值小于当前字号下文本渲染出的实际高度时，fallbackLineSpacing属性将生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-fallbackLineSpacing(enabled: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-fallbackLineSpacing(enabled: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 行高是否基于文字实际高度自适应。<br>true表示行高基于文字实际高度自适应，false表示行高不基于文字实际高度自适应。<br>默认值：false。<br>设置为undefined或null时，取默认值。 |

## horizontalScrolling

```TypeScript
horizontalScrolling(enabled: Optional<boolean>)
```

设置当文本宽度超过内容区宽度时是否启用水平滚动。适用于需要显示长文本内容（如代码片段、长URL等）而不希望自动换行的场景。不通过该接口设置，默认禁用水平滚动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-horizontalScrolling(enabled: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-horizontalScrolling(enabled: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否启用水平滚动。<br>true表示启用水平滚动，false表示禁用水平滚动，文本将自动换行。<br>默认值：false。设置为undefined或null时，不启用水平滚动。 |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。适用于自定义字体行高较小导致文字被裁剪、紧凑排版等场景。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-includeFontPadding(include: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-includeFontPadding(include: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否在首行和尾行增加间距以避免文字截断。<br>true表示在首行和尾行增加间距，false表示在首行和尾行不增加间距。<br>默认值：false。<br>设置为undefined或null时，取默认值。 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置键盘外观。

适用于需要根据应用主题或沉浸式场景调整键盘视觉风格的场景，如深色模式下使用DARK外观。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): RichEditorAttribute--><!--Device-RichEditorAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-optional-t.md)<KeyboardAppearance> | 是 | 键盘外观。<br>默认值：KeyboardAppearance.NONE_IMMERSIVE。<br>各枚举值适用场景请参考KeyboardAppearance枚举说明。<br>设置为undefined或null时，取默认值。 |

## maxLength

```TypeScript
maxLength(maxLength: Optional<number>)
```

设置组件内容的最大长度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-maxLength(maxLength: Optional<number>): RichEditorAttribute--><!--Device-RichEditorAttribute-maxLength(maxLength: Optional<number>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxLength | [Optional](arkts-arkui-optional-t.md)<number> | 是 | 内容的最大输入长度。当内容（包含文本、图片、Symbol和Builder）的总长度达到此值时，将无法继续添加内容。<br>默认值：Infinity，可以无限输入。<br>**说明：**<br>取值范围：[0, +∞)。当不设置该属性或设置为undefined或负数时，取默认值Infinity；设置为0时，无法输入内容；设置小数时，取整数部分。 |

## maxLines

```TypeScript
maxLines(maxLines: Optional<number>)
```

设置组件可显示的最大行数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-maxLines(maxLines: Optional<number>): RichEditorAttribute--><!--Device-RichEditorAttribute-maxLines(maxLines: Optional<number>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxLines | [Optional](arkts-arkui-optional-t.md)<number> | 是 | 设置富文本可显示的最大行数。maxLines为可显示行数，当设置maxLines时，超出内容可滚动显示。同时设置组件高度和最大行数，组件高度优先生效。<br>取值范围：(0, UINT32_MAX]。<br>默认值：UINT32_MAX，可以无限输入。<br>设置为0、负数、undefined或null时，取默认值。 |

## onCopy

```TypeScript
onCopy(callback: Callback<CopyEvent>)
```

复制时触发回调。开发者可以通过该方法，覆盖系统默认行为，实现图文的复制。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件，默认支持图文的复制。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onCopy(callback: Callback<CopyEvent>): RichEditorAttribute--><!--Device-RichEditorAttribute-onCopy(callback: Callback<CopyEvent>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<CopyEvent> | 是 | 定义用户复制事件。 |

## onCut

```TypeScript
onCut(callback: Callback<CutEvent>)
```

剪切时触发回调。开发者可以通过该方法，覆盖系统默认行为，实现图文的剪切。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件，默认支持图文的剪切。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onCut(callback: Callback<CutEvent>): RichEditorAttribute--><!--Device-RichEditorAttribute-onCut(callback: Callback<CutEvent>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<CutEvent> | 是 | 定义用户剪切事件。 |

## onDeleteComplete

```TypeScript
onDeleteComplete(callback: Callback<void>)
```

输入法删除内容后，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onDeleteComplete(callback: Callback<void>): RichEditorAttribute--><!--Device-RichEditorAttribute-onDeleteComplete(callback: Callback<void>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 订阅输入法完成删除内容的回调。<br>**起始版本：** 12 |

## onDidChange

```TypeScript
onDidChange(callback: OnDidChangeCallback) : RichEditorAttribute
```

在组件执行增删操作后，触发回调。如果文本实际未发生增删，则不触发该回调。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onDidChange(callback: OnDidChangeCallback) : RichEditorAttribute--><!--Device-RichEditorAttribute-onDidChange(callback: OnDidChangeCallback) : RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnDidChangeCallback](../arkts-apis/arkts-arkui-ondidchangecallback-t.md) | 是 | The triggered function after content changed. |

## onDidIMEInput

```TypeScript
onDidIMEInput(callback: Callback<TextRange>)
```

输入法输入完成后，触发回调。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onDidIMEInput(callback: Callback<TextRange>): RichEditorAttribute--><!--Device-RichEditorAttribute-onDidIMEInput(callback: Callback<TextRange>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<TextRange> | 是 | TextRange为输入法本次输入内容的范围。<br/>输入法完成输入时的回调。 |

## onEditingChange

```TypeScript
onEditingChange(callback: Callback<boolean>)
```

组件内容的编辑状态发生变化时触发该回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onEditingChange(callback: Callback<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-onEditingChange(callback: Callback<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 是 | 编辑状态变化时触发的回调。<br>true表示编辑态，false表示非编辑态。 |

## onIMEInputComplete

```TypeScript
onIMEInputComplete(callback: Callback<RichEditorTextSpanResult>)
```

输入法输入完成后，触发回调。

该接口仅支持返回一个文本span的信息，当编辑操作涉及返回多个文本span信息时，建议使用[onDidIMEInput](RichEditorAttribute#onDidIMEInput)接口。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onIMEInputComplete(callback: Callback<RichEditorTextSpanResult>): RichEditorAttribute--><!--Device-RichEditorAttribute-onIMEInputComplete(callback: Callback<RichEditorTextSpanResult>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorTextSpanResult> | 是 | [RichEditorTextSpanResult](arkts-arkui-rich-editor-richeditortextspanresult-i.md)为输入法完成输入后的文本Span信息。<br/>输入法完成输入后的回调。<br>**起始版本：** 12 |

## onPaste

```TypeScript
onPaste(callback: PasteEventCallback)
```

粘贴完成前，触发回调。

开发者可以通过该方法，覆盖系统默认行为，实现图文的粘贴。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onPaste(callback: PasteEventCallback): RichEditorAttribute--><!--Device-RichEditorAttribute-onPaste(callback: PasteEventCallback): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PasteEventCallback](arkts-arkui-pasteeventcallback-t.md) | 是 | 订阅粘贴时的回调。<br>**起始版本：** 12 |

## onReady

```TypeScript
onReady(callback: Callback<void>)
```

富文本组件初始化完成后触发回调。初始化完成后组件可正常响应输入和交互。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onReady(callback: Callback<void>): RichEditorAttribute--><!--Device-RichEditorAttribute-onReady(callback: Callback<void>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 订阅富文本组件初始化完成的回调。<br>**起始版本：** 12 |

## onSelect

```TypeScript
onSelect(callback: Callback<RichEditorSelection>)
```

鼠标左键双击选中内容触发回调；松开鼠标左键再次触发回调。

手指长按选中内容触发回调；松开手指再次触发回调。

通过手指或鼠标连续修改选中区、三击选段场景，不回调onSelect。

需要实时感知选中区变化的场景和使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件，请使用onSelectionChange接口。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onSelect(callback: Callback<RichEditorSelection>): RichEditorAttribute--><!--Device-RichEditorAttribute-onSelect(callback: Callback<RichEditorSelection>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorSelection> | 是 | [RichEditorSelection](arkts-arkui-rich-editor-richeditorselection-i.md)为选中的所有span信息。<br/>选择时触发的回调。<br>**起始版本：** 12 |

## onSelectionChange

```TypeScript
onSelectionChange(callback: Callback<RichEditorRange>)
```

内容选择区域或编辑状态下的光标位置发生变化时，将触发该回调。光标位置变化时，回调中选择区域的起始和终止位置相等。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onSelectionChange(callback: Callback<RichEditorRange>): RichEditorAttribute--><!--Device-RichEditorAttribute-onSelectionChange(callback: Callback<RichEditorRange>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorRange> | 是 | [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md)为所有内容的选择区域起始和终止位置。<br/>订阅文本选择区域发生变化或编辑状态下光标位置发生变化时触发的回调。 |

## onSubmit

```TypeScript
onSubmit(callback: SubmitCallback)
```

按下软键盘输入法回车键时触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onSubmit(callback: SubmitCallback): RichEditorAttribute--><!--Device-RichEditorAttribute-onSubmit(callback: SubmitCallback): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SubmitCallback](arkts-arkui-submitcallback-t.md) | 是 | 按下软键盘回车键时的回调，用于接收回车键类型和提交事件信息。 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient> | undefined)
```

在组件绑定输入法前，触发回调。

适用于需要定制输入法行为的场景，如设置输入法扩展配置以实现特定输入模式、自定义输入法功能等。

调用[IMEClient](../arkts-apis/arkts-arkui-text-common-imeclient-i.md)的[setExtraConfig](../arkts-apis/arkts-arkui-text-common-imeclient-i.md#setextraconfig-1)方法设置输入法扩展信息。在绑定输入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。

<!--Del-->

从API版本26.0.0开始，在输入框将要绑定输入法前，可以通过`UIContext`的系统接口[setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig-1)设置键盘的样式。<!--DelEnd-  
->

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): RichEditorAttribute--><!--Device-RichEditorAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<IMEClient> \| undefined | 是 | 在组件绑定输入法前触发的回调。<br>值为undefined时清除已绑定的回调事件。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<RichEditorChangeValue, boolean>) : RichEditorAttribute
```

在组件执行增删操作前，触发回调。与[onDidChange](RichEditorAttribute#onDidChange)形成will/did时序模式：onWillChange在增删操作前触发，onDidChange在增删操作后触发；onWillChange返回false时，组件不执行增删操作，onDidChange不会触发。两者可同时使用。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建的RichEditor组件不支持该回调。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-onWillChange(callback: Callback<RichEditorChangeValue, boolean>) : RichEditorAttribute--><!--Device-RichEditorAttribute-onWillChange(callback: Callback<RichEditorChangeValue, boolean>) : RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<RichEditorChangeValue, boolean> | 是 | The triggered function before text content is about to change. |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

设置文本排版时是否启用孤字优化。

适用于长文排版、电子书阅读等需要避免段落末行仅剩一个字影响阅读体验的场景。不通过该接口设置，默认不启用孤字优化。

孤字优化通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。启用后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[RichEditorParagraphStyle](arkts-arkui-rich-editor-richeditorparagraphstyle-i.md)的wordBreak属性为非BREAK_ALL并且待排版文本首个[TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)的[locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)为“zh-Hans”或“zh-Hant”时生效。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-orphanCharOptimization(enabled: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-orphanCharOptimization(enabled: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 段落最后一行是否启用孤字优化。<br>true表示启用孤字优化，false表示不启用孤字优化。<br>默认值：false。设置为undefined或null时，不启用孤字优化。 |

## placeholder

```TypeScript
placeholder(value: ResourceStr, style?: PlaceholderStyle)
```

设置无输入时的提示文本。

设置后，组件无内容时显示提示文本，用户开始输入内容后提示文本自动消失。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-placeholder(value: ResourceStr, style?: PlaceholderStyle): RichEditorAttribute--><!--Device-RichEditorAttribute-placeholder(value: ResourceStr, style?: PlaceholderStyle): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 无输入时的提示文本。 |
| style | [PlaceholderStyle](arkts-arkui-rich-editor-placeholderstyle-i.md) | 否 | 提示文本的字体样式。<br>当需要自定义placeholder的颜色、字体大小等样式时传入此参数；缺省时，默认跟随主题样式。 |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

设置是否启用行尾标点符号悬挂。

启用后，允许行尾单个标点符号超出排版宽度而不换行，适用于需要避免行尾标点符号换行至下一行行首以提升排版美观度的场景。不通过该接口设置，默认标点符号不悬挂。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-punctuationOverflow(enabled: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-punctuationOverflow(enabled: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否启用行尾标点符号悬挂。<br>true表示启用行尾标点符号悬挂，false表示不启用行尾标点符号悬挂。<br>默认值：false。设置为undefined或null时，不启用标点符号悬挂。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

设置组件滚动条颜色。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-scrollBarColor(color: Optional<ColorMetrics>): RichEditorAttribute--><!--Device-RichEditorAttribute-scrollBarColor(color: Optional<ColorMetrics>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)<ColorMetrics> | 是 | 设置组件滚动条颜色。<br />默认值：'#66182431'，显示为灰色。<br />**说明：** 设置异常值时按默认值处理。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中的底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-selectedBackgroundColor(value: ResourceColor): RichEditorAttribute--><!--Device-RichEditorAttribute-selectedBackgroundColor(value: ResourceColor): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本选中的底板颜色。<br/>默认为20%不透明度。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置拖动预览样式。适用于需要自定义拖拽内容外观的场景，如匹配应用主题风格的拖拽预览效果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): RichEditorAttribute--><!--Device-RichEditorAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): RichEditorAttribute-End-->

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
> 单行模式下换行符会显示为空格。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-singleLine(isEnable: boolean | undefined): RichEditorAttribute--><!--Device-RichEditorAttribute-singleLine(isEnable: boolean | undefined): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean \| undefined | 是 | 是否启用单行模式。<br>true表示启用单行模式，false表示不启用单行模式。<br>设置为undefined或null时，按照false处理，不启用单行模式。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键传递。适用于编辑内容未保存时阻止返回避免数据丢失、弹窗编辑等需要防止用户误操作退出编辑的场景。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-stopBackPress(isStopped: Optional<boolean>): RichEditorAttribute--><!--Device-RichEditorAttribute-stopBackPress(isStopped: Optional<boolean>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否阻止返回键。<br/>true表示阻止，false表示不阻止。<br/>默认值：true。异常值取默认值。 |

## undoStyle

```TypeScript
undoStyle(style: Optional<UndoStyle>)
```

设置撤销还原时是否保留原内容的样式。

使用[RichEditorStyledStringOptions](arkts-arkui-rich-editor-richeditorstyledstringoptions-i.md)构建RichEditor组件时，撤销还原时默认保留原内容样式，不受该接口设置的属性影响。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorAttribute-undoStyle(style: Optional<UndoStyle>): RichEditorAttribute--><!--Device-RichEditorAttribute-undoStyle(style: Optional<UndoStyle>): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<UndoStyle> | 是 | 撤销还原是否保留原样式选项。<br>默认值：UndoStyle.CLEAR_STYLE。<br>设置为undefined或null时，取默认值。 |

