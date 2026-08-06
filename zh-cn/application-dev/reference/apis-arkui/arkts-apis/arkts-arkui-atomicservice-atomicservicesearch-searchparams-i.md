# SearchParams

AtomicServiceSearch中“搜索区”的可选属性。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-unnamed-export interface SearchParams--><!--Device-unnamed-export interface SearchParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelIcon

```TypeScript
cancelIcon?: IconOptions
```

右侧清除按钮样式。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 当style为CancelButtonStyle.CONSTANT时，默认显示清除样式。

**类型：** IconOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-cancelIcon?: IconOptions--><!--Device-SearchParams-cancelIcon?: IconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretStyle

```TypeScript
caretStyle?: CaretStyle
```

光标样式。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** CaretStyle

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-caretStyle?: CaretStyle--><!--Device-SearchParams-caretStyle?: CaretStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentBackgroundColor

```TypeScript
componentBackgroundColor?: ResourceColor
```

设置组件的背景色。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-componentBackgroundColor?: ResourceColor--><!--Device-SearchParams-componentBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## copyOptions

```TypeScript
copyOptions?: CopyOptions
```

输入的文本是否可复制。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，支持设备内复制。

**类型：** CopyOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-copyOptions?: CopyOptions--><!--Device-SearchParams-copyOptions?: CopyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: TextDecorationOptions
```

文本装饰线对象。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** TextDecorationOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-decoration?: TextDecorationOptions--><!--Device-SearchParams-decoration?: TextDecorationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editMenuOptions

```TypeScript
editMenuOptions?: EditMenuOptions
```

设置自定义菜单扩展项，允许用户设置扩展项的文本内容、图标、回调方法。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** EditMenuOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-editMenuOptions?: EditMenuOptions--><!--Device-SearchParams-editMenuOptions?: EditMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

是否开启触控反馈。true表示开启触控反馈。false表示不开启触控反馈。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-enableHapticFeedback?: boolean--><!--Device-SearchParams-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus?: boolean
```

Search获焦时，是否主动拉起软键盘。true表示Search获焦时主动拉起软键盘。false表示Search获焦时不主动拉起键盘。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-enableKeyboardOnFocus?: boolean--><!--Device-SearchParams-enableKeyboardOnFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewText

```TypeScript
enablePreviewText?: boolean
```

是否开启输入预上屏。true表示开启输入预上屏。false表示不开启输入预上屏。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 需要配合开启输入法的预上屏功能。预上屏内容定义为文字暂存态，目前不支持文字拦截功能，因此该值为true时不触发onWillInsert、onDidInsert回调。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-enablePreviewText?: boolean--><!--Device-SearchParams-enablePreviewText?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enterKeyType

```TypeScript
enterKeyType?: EnterKeyType
```

输入法回车键类型。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** EnterKeyType

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-enterKeyType?: EnterKeyType--><!--Device-SearchParams-enterKeyType?: EnterKeyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

输入文本的字体颜色。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-fontColor?: ResourceColor--><!--Device-SearchParams-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: ResourceStr
```

设置文字特性效果，比如数字等宽的特性。 格式为：normal | &lt;feature-tag-value&gt; &lt;feature-tag-value&gt;的格式为：\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ [ \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ | on | off ] &lt;feature-tag-value&gt;的个数可以有多个，中间用','隔开。 例如，使用等宽数字的输入格式为："ss01" on。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-fontFeature?: ResourceStr--><!--Device-SearchParams-fontFeature?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideSelectionMenu

```TypeScript
hideSelectionMenu?: boolean
```

是否不弹出系统文本选择菜单。 设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，不弹出系统文本选择菜单。设置为false时，弹出系统文本选择菜单。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-hideSelectionMenu?: boolean--><!--Device-SearchParams-hideSelectionMenu?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inputFilter

```TypeScript
inputFilter?: InputFilterParams
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。仅支持单个字符匹配，不支持字符串匹配。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 -value: 正则表达式。 -error: 正则匹配失败时，返回被过滤的内容。

**类型：** InputFilterParams

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-inputFilter?: InputFilterParams--><!--Device-SearchParams-inputFilter?: InputFilterParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string | Resource
```

设置文本字符间距。正数拉开字符距离，负数则拉近字符距离。浮点数默认值为0.0，单位为物理像素px。若输入类型非number且无法解析为数字，则使用默认值。

**类型：** number \| string \| Resource

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-letterSpacing?: number | string | Resource--><!--Device-SearchParams-letterSpacing?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | string | Resource
```

设置文本最大显示字号。需要配合minFontSize以及布局大小限制使用，单独设置不生效。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** number \| string \| Resource

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-maxFontSize?: number | string | Resource--><!--Device-SearchParams-maxFontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLength

```TypeScript
maxLength?: number
```

设置文本的最大输入字符数。默认不设置最大输入字符数限制。到达文本最大字符限制，将无法继续输入字符。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-maxLength?: number--><!--Device-SearchParams-maxLength?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | string | Resource
```

设置文本最小显示字号。需要配合maxFontSize以及布局大小限制使用，单独设置不生效。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** number \| string \| Resource

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-minFontSize?: number | string | Resource--><!--Device-SearchParams-minFontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: EditableTextOnChangeCallback
```

输入内容发生变化时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** EditableTextOnChangeCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onChange?: EditableTextOnChangeCallback--><!--Device-SearchParams-onChange?: EditableTextOnChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onContentScroll

```TypeScript
onContentScroll?: OnContentScrollCallback
```

文本内容滚动时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** OnContentScrollCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onContentScroll?: OnContentScrollCallback--><!--Device-SearchParams-onContentScroll?: OnContentScrollCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCopy

```TypeScript
onCopy?: Callback<string>
```

进行复制操作时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;string&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onCopy?: Callback<string>--><!--Device-SearchParams-onCopy?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCut

```TypeScript
onCut?: Callback<string>
```

进行剪切操作时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;string&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onCut?: Callback<string>--><!--Device-SearchParams-onCut?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDelete

```TypeScript
onDidDelete?: Callback<DeleteValue>
```

在删除完成时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;DeleteValue&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onDidDelete?: Callback<DeleteValue>--><!--Device-SearchParams-onDidDelete?: Callback<DeleteValue>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidInsert

```TypeScript
onDidInsert?: Callback<InsertValue>
```

在输入完成时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;InsertValue&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onDidInsert?: Callback<InsertValue>--><!--Device-SearchParams-onDidInsert?: Callback<InsertValue>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEditChange

```TypeScript
onEditChange?: Callback<boolean>
```

输入状态变化时，触发该回调。有光标时为编辑态，无光标时为非编辑态。isEditing为true表示正在输入。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onEditChange?: Callback<boolean>--><!--Device-SearchParams-onEditChange?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPaste

```TypeScript
onPaste?: OnPasteCallback
```

进行粘贴操作时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** OnPasteCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onPaste?: OnPasteCallback--><!--Device-SearchParams-onPaste?: OnPasteCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSubmit

```TypeScript
onSubmit?: Callback<string> | SearchSubmitCallback
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;string&gt; \| SearchSubmitCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onSubmit?: Callback<string> | SearchSubmitCallback--><!--Device-SearchParams-onSubmit?: Callback<string> | SearchSubmitCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTextSelectionChange

```TypeScript
onTextSelectionChange?: OnTextSelectionChangeCallback
```

文本选择的位置发生变化或编辑状态下光标位置发生变化时，触发该回调。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** OnTextSelectionChangeCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onTextSelectionChange?: OnTextSelectionChangeCallback--><!--Device-SearchParams-onTextSelectionChange?: OnTextSelectionChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDelete

```TypeScript
onWillDelete?: Callback<DeleteValue, boolean>
```

在将要删除时，触发该回调。true表示正常删除，false表示不删除。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;DeleteValue, boolean&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onWillDelete?: Callback<DeleteValue, boolean>--><!--Device-SearchParams-onWillDelete?: Callback<DeleteValue, boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillInsert

```TypeScript
onWillInsert?: Callback<InsertValue, boolean>
```

在将要输入时，触发该回调。true表示将输入内容正常插入结果字符串，false表示不插入。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Callback&lt;InsertValue, boolean&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-onWillInsert?: Callback<InsertValue, boolean>--><!--Device-SearchParams-onWillInsert?: Callback<InsertValue, boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholderColor

```TypeScript
placeholderColor?: ResourceColor
```

placeholder文本颜色。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-placeholderColor?: ResourceColor--><!--Device-SearchParams-placeholderColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholderFont

```TypeScript
placeholderFont?: Font
```

设置placeholder文本样式，包括字体大小，字体粗细，字体族，字体风格。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Font

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-placeholderFont?: Font--><!--Device-SearchParams-placeholderFont?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressedBackgroundColor

```TypeScript
pressedBackgroundColor?: ResourceColor
```

设置组件按压态的背景色。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-pressedBackgroundColor?: ResourceColor--><!--Device-SearchParams-pressedBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## searchButton

```TypeScript
searchButton?: SearchButtonParams
```

设置搜索框末尾搜索按钮。点击搜索按钮，同时触发onSubmit与onClick回调。 -value：搜索框末尾搜索按钮文本内容。 -option: 配置搜索框文本样式。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** SearchButtonParams

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-searchButton?: SearchButtonParams--><!--Device-SearchParams-searchButton?: SearchButtonParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## searchIcon

```TypeScript
searchIcon?: IconOptions | SymbolGlyphModifier
```

左侧搜索图标样式。 浅色模式默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 深色模式默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。

**类型：** IconOptions \| SymbolGlyphModifier

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-searchIcon?: IconOptions | SymbolGlyphModifier--><!--Device-SearchParams-searchIcon?: IconOptions | SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## searchKey

```TypeScript
searchKey?: ResourceStr
```

用作找到一个唯一的search组件。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-searchKey?: ResourceStr--><!--Device-SearchParams-searchKey?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

文本选中底板颜色。默认为20%不透明度。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-selectedBackgroundColor?: ResourceColor--><!--Device-SearchParams-selectedBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

文本在搜索框中的对齐方式。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** TextAlign

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-textAlign?: TextAlign--><!--Device-SearchParams-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textFont

```TypeScript
textFont?: Font
```

设置搜索框内输入文本样式，包括字体大小，字体粗细，字体族，字体风格。目前仅支持默认字体族。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Font

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-textFont?: Font--><!--Device-SearchParams-textFont?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: Dimension
```

首行文本缩进。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** Dimension

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-textIndent?: Dimension--><!--Device-SearchParams-textIndent?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: SearchType
```

输入框类型。默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** SearchType

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchParams-type?: SearchType--><!--Device-SearchParams-type?: SearchType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

