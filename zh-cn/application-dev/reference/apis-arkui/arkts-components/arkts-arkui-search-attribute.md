# Search属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** SearchAttribute extends [CommonMethod<SearchAttribute>](CommonMethod<SearchAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class SearchAttribute extends CommonMethod<SearchAttribute>--><!--Device-unnamed-declare class SearchAttribute extends CommonMethod<SearchAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

设置自动大小写模式的文本模式，只提供接口能力，具体实现以输入法应用为主。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): SearchAttribute--><!--Device-SearchAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-text-common-autocapitalizationmode-e.md) | 是 | 自动大小写模式，默认状态无效。 |

## cancelButton

```TypeScript
cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions)
```

设置右侧清除按钮样式。示例请参考[示例2（设置搜索和删除图标）](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#示例2设置搜索和删除图标)和[示例11（设置symbol类型清除按钮）](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#示例11设置symbol类型清除按钮)。

Wearable设备上默认图标大小为18fp。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions): SearchAttribute--><!--Device-SearchAttribute-cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CancelButtonOptions \| CancelButtonSymbolOptions | 是 | 右侧清除按钮样式。<br>默认值：<br />{<br/>style:CancelButtonStyle.INPUT,<br/>icon: {<br/>size: '16vp',<br/>color: '#99ffffff',<br/>src: ' '<br/>}<br/>}<br/>当style为CancelButtonStyle.CONSTANT时，默认显示清除样式。<br>**起始版本：** 12 |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

设置光标样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-caretStyle(value: CaretStyle): SearchAttribute--><!--Device-SearchAttribute-caretStyle(value: CaretStyle): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-text-common-caretstyle-i.md) | 是 | 光标样式。<br />默认值：<br />{<br />width: '2.0vp',<br />color: '#007DFF'<br />} |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

设置是否开启行首标点符号压缩。

> **说明：**  
>  
> - 行首标点符号默认不压缩。  
>  
> - 支持压缩的标点符号，请参考[ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md)的行首压缩的标点范围。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否开启行首标点符号压缩。<br/>true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置输入的文本是否可复制。设置CopyOptions.None时，当前Search中的文字无法被复制、剪切、翻译、分享、搜索和帮写，支持粘贴和全选。

设置CopyOptions.None时，不允许拖拽。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-copyOption(value: CopyOptions): SearchAttribute--><!--Device-SearchAttribute-copyOption(value: CopyOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-enums-copyoptions-e.md) | 是 | 输入的文本是否可复制。<br />默认值：CopyOptions.LocalDevice，支持设备内复制。 |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

设置自定义键盘。

当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。

自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认值。

自定义键盘采用覆盖原始界面的方式呈现，当没有开启避让模式或者输入框不需要避让的场景不会对应用原始界面产生压缩或者上提。

自定义键盘无法获取焦点，但是会拦截手势事件。

默认在输入控件失去焦点时，关闭自定义键盘，开发者也可以通过[stopEditing](arkts-arkui-search-searchcontroller-c.md#stopediting-1)方法控制键盘关闭。

当设置自定义键盘时，可以通过绑定[onKeyPreIme](arkts-arkui-common-commonmethod-c.md#onkeypreime-1)事件规避物理键盘的输入。

从API version 23开始，自定义键盘可以通过[setCustomKeyboardContinueFeature](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#setcustomkeyboardcontinuefeature23)开启接续，在切换至其他自定义键盘时，会直接切换，不会触发键盘关闭和拉起动画。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): SearchAttribute--><!--Device-SearchAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder \| ComponentContent \| undefined | 是 | 自定义键盘。设定值为undefined时，关闭自定义键盘。<br>**起始版本：** 22 |
| options | [KeyboardOptions](arkts-arkui-rich-editor-keyboardoptions-i.md) | 否 | 设置自定义键盘是否支持避让功能。<br>**起始版本：** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

设置文本装饰线类型样式及其颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-decoration(value: TextDecorationOptions): SearchAttribute--><!--Device-SearchAttribute-decoration(value: TextDecorationOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-common-textdecorationoptions-i.md) | 是 | 文本装饰线对象。<br />默认值：{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID,<br/> thicknessScale: 1.0<br/>} |

## dividerColor

```TypeScript
dividerColor(color: Optional<ColorMetrics>)
```

设置输入框分割线颜色。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-dividerColor(color: Optional<ColorMetrics>): SearchAttribute--><!--Device-SearchAttribute-dividerColor(color: Optional<ColorMetrics>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)<ColorMetrics> | 是 | 设置分割线颜色。<br/>默认使用系统的主题色：浅色模式下为0x33000000，显示为浅黑色，深色模式下为0x33FFFFFF，显示为浅白色。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置自定义菜单扩展项，允许用户设置扩展项的文本内容、图标、回调方法。

调用[disableMenuItems](../../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20)或[disableSystemServiceMenuItems](../../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20)接口屏蔽文本选择菜单内的系统服务菜单项时，editMenuOptions接口内回调方法[onCreateMenu](../arkts-apis/arkts-arkui-text-common-editmenuoptions-i.md#oncreatemenu-1)的入参列表中不包含被屏蔽的菜单选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-editMenuOptions(editMenu: EditMenuOptions): SearchAttribute--><!--Device-SearchAttribute-editMenuOptions(editMenu: EditMenuOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-text-common-editmenuoptions-i.md) | 是 | 扩展菜单选项。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enableAutoSpacing(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-enableAutoSpacing(enabled: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否开启中文与西文的自动间距。<br/>true为开启自动间距，false为不开启。<br />默认值：false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

设置是否开启触控反馈。

开启触控反馈时，需要在工程的[module.json5](../../../../quick-start/module-configuration-file.md)中配置requestPermissions字段以开启振动权限，配置如下：

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enableHapticFeedback(isEnabled: boolean): SearchAttribute--><!--Device-SearchAttribute-enableHapticFeedback(isEnabled: boolean): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否开启触控反馈。<br/>true表示开启触控反馈，false表示不开启触控反馈。<br/>默认值：true |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

设置Search通过点击以外的方式获焦时，是否主动拉起软键盘。

从API version 10开始，获焦默认绑定输入法。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enableKeyboardOnFocus(value: boolean): SearchAttribute--><!--Device-SearchAttribute-enableKeyboardOnFocus(value: boolean): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | Search获焦时，是否主动拉起软键盘。<br/>true表示主动拉起，false表示不主动拉起。<br/>默认值：true |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启输入预上屏。

预上屏内容定义为文字暂存态，目前不支持文字拦截功能。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enablePreviewText(enable: boolean): SearchAttribute--><!--Device-SearchAttribute-enablePreviewText(enable: boolean): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否开启输入预上屏。<br/>true表示开启输入预上屏，false表示不开启输入预上屏。<br/>默认值：true |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

设置是否对选中文本进行实体识别。该接口依赖设备底层应具有文本识别能力，否则设置不会生效。

当enableSelectedDataDetector设置为true时，默认识别所有类型的实体。

需要[CopyOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-copyoptions-i.md)为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时，本功能生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enableSelectedDataDetector(enable: boolean | undefined): SearchAttribute--><!--Device-SearchAttribute-enableSelectedDataDetector(enable: boolean | undefined): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 开启选中词文本识别。<br/>true：开启识别，false：关闭识别。默认值为：true。 |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

设置输入法回车键类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-enterKeyType(value: EnterKeyType): SearchAttribute--><!--Device-SearchAttribute-enterKeyType(value: EnterKeyType): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-text-input-enterkeytype-e.md) | 是 | 输入法回车键类型。<br/>默认值：EnterKeyType.Search |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。不通过该接口设置，默认行高不基于文字实际高度自适应。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-fallbackLineSpacing(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-fallbackLineSpacing(enabled: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 行高是否基于文字实际高度自适应。<br/>true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置输入文本的字体颜色。fontSize、fontStyle、fontWeight和fontFamily在[textFont](SearchAttribute#textFont)属性中设置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-fontColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-fontColor(value: ResourceColor): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入文本的字体颜色。<br/>默认值：'#FF182431'<br/>Wearable设备上默认值为：'#dbffffff' |

## fontFeature

```TypeScript
fontFeature(value: string)
```

设置文字特性效果，比如数字等宽的特性。

格式为：normal \| \<feature-tag-value\>

\<feature-tag-value\>的格式为：\<string\> \[ \<integer\> \| on \| off ]

\<feature-tag-value\>的个数可以有多个，中间用','隔开。

例如，使用等宽数字的输入格式为："ss01" on。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-fontFeature(value: string): SearchAttribute--><!--Device-SearchAttribute-fontFeature(value: string): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 文字特性效果。 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

设置文本在行内垂直居中，将行间距平分至行的顶部与底部。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-halfLeading(halfLeading: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-halfLeading(halfLeading: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 设置文本是否垂直居中。<br/>true表示将行间距平分至行的顶部与底部，false则不平分。<br/>默认值：false |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-includeFontPadding(include: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-includeFontPadding(include: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否在首行和尾行增加间距以避免文字截断。<br/>true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。

单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。

设置inputFilter且输入的字符不为空字符，会导致设置输入框类型(即type接口)附带的文本过滤效果失效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 正则表达式。 |
| error | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string> | 否 | 正则匹配失败时，返回被过滤的内容。 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置输入框拉起的键盘样式，需要输入法适配后生效。具体参考[输入法应用沉浸模式](../../../../inputmethod/inputmethod-immersive-mode-guide.md)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): SearchAttribute--><!--Device-SearchAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-optional-t.md)<KeyboardAppearance> | 是 | 键盘样式。<br/>默认值：KeyboardAppearance.NONE_IMMERSIVE |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

设置文本字符间距。设置该值为百分比时，按默认值显示。设置该值为0时，按默认值显示。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

当取值为负值时，文字会发生压缩，负值过小时会将组件内容区大小压缩为0，导致无内容显示。

对每个字符生效，包括行尾字符。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-letterSpacing(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-letterSpacing(value: number | string | Resource): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本字符间距。<br/>单位：[fp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

设置文本的文本行高，设置值不大于0时，不限制文本行高，自适应字体大小，number类型时单位为fp。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-lineHeight(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-lineHeight(value: number | string | Resource): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本的文本行高。 |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

设置文本最大的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-maxFontScale(scale: Optional<number|Resource>): SearchAttribute--><!--Device-SearchAttribute-maxFontScale(scale: Optional<number|Resource>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)<number\|Resource> | 是 | 文本最大的字体缩放倍数，支持undefined类型。<br/>取值范围：[1, +∞)<br/>**说明：** <br/>设置的值小于1时，按值为1处理。异常值默认不生效。<br/>设置maxFontScale属性后，search组件内容最多放大到2倍。<br/>使用前需在工程中配置[configuration.json](../../../../quick-start/app-configuration-file.md#configuration标签)文件和[app.json5](../../../../quick-start/app-configuration-file.md)文件，具体详见[示例19（设置最小字体范围与最大字体范围）](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#示例19设置最小字体范围与最大字体范围)。 |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

设置文本最大显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[minFontSize](SearchAttribute#minFontSize)以及布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

maxFontSize小于等于0或者maxFontSize小于minFontSize时，自适应字号不生效，此时按照[textFont](SearchAttribute#textFont)属性里面size的取值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-maxFontSize(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-maxFontSize(value: number | string | Resource): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最大显示字号。<br/>单位：[fp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## maxLength

```TypeScript
maxLength(value: number)
```

设置文本的最大输入字符数。默认不设置最大输入字符数限制。到达文本最大字符限制，将无法继续输入字符。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-maxLength(value: number): SearchAttribute--><!--Device-SearchAttribute-maxLength(value: number): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 文本的最大输入字符数。 &lt;/br&gt; 当value&lt;0时，按照默认值处理，不设限制。 |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

设置文本最小的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-minFontScale(scale: Optional<number|Resource>): SearchAttribute--><!--Device-SearchAttribute-minFontScale(scale: Optional<number|Resource>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)<number\|Resource> | 是 | 文本最小的字体缩放倍数，支持undefined类型。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。异常值默认不生效。<br/>使用前需在工程中配置[configuration.json](../../../../quick-start/app-configuration-file.md#configuration标签)文件和[app.json5](../../../../quick-start/app-configuration-file.md)文件，具体详见[示例19（设置最小字体范围与最大字体范围）](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#示例19设置最小字体范围与最大字体范围)。 |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

设置文本最小显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[maxFontSize](SearchAttribute#maxFontSize)以及布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

minFontSize小于或等于0时，自适应字号不生效，此时按照[textFont](SearchAttribute#textFont)属性里面size的取值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-minFontSize(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-minFontSize(value: number | string | Resource): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最小显示字号。<br/>单位：[fp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

输入内容发生变化时，触发该回调。

在本回调中，若执行了光标操作，需要开发者在预上屏场景下依据previewText参数调整光标逻辑，以适应预上屏场景。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onChange(callback: EditableTextOnChangeCallback): SearchAttribute--><!--Device-SearchAttribute-onChange(callback: EditableTextOnChangeCallback): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) | 是 | 当前输入文本内容变化时的回调。<br>**起始版本：** 12 |

## onContentScroll

```TypeScript
onContentScroll(callback: OnContentScrollCallback)
```

文本内容滚动时，触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onContentScroll(callback: OnContentScrollCallback): SearchAttribute--><!--Device-SearchAttribute-onContentScroll(callback: OnContentScrollCallback): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | 是 | 文本内容滚动回调。<br>**起始版本：** 18 |

## onCopy

```TypeScript
onCopy(callback: Callback<string>)
```

进行复制操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onCopy(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onCopy(callback: Callback<string>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string> | 是 | 复制回调，其返回值为复制的文本内容。<br>**起始版本：** 18 |

## onCut

```TypeScript
onCut(callback: Callback<string>)
```

进行剪切操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onCut(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onCut(callback: Callback<string>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string> | 是 | 剪切回调，其返回值为剪切的文本内容。<br>**起始版本：** 18 |

## onDidDelete

```TypeScript
onDidDelete(callback: Callback<DeleteValue>)
```

在删除完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onDidDelete(callback: Callback<DeleteValue>): SearchAttribute--><!--Device-SearchAttribute-onDidDelete(callback: Callback<DeleteValue>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<DeleteValue> | 是 | 在删除完成时调用的回调。<br/>仅支持系统输入法输入的场景。 |

## onDidInsert

```TypeScript
onDidInsert(callback: Callback<InsertValue>)
```

在输入完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onDidInsert(callback: Callback<InsertValue>): SearchAttribute--><!--Device-SearchAttribute-onDidInsert(callback: Callback<InsertValue>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<InsertValue> | 是 | 在输入完成时调用的回调。<br/>仅支持系统输入法输入的场景。 |

## onEditChange

```TypeScript
onEditChange(callback: Callback<boolean>)
```

输入状态变化时，触发该回调。有光标时为编辑态，无光标时为非编辑态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onEditChange(callback: Callback<boolean>): SearchAttribute--><!--Device-SearchAttribute-onEditChange(callback: Callback<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 是 | 编辑状态改变回调，其返回值为true表示正在输入，false表示无焦点，无法输入文字。 |

## onPaste

```TypeScript
onPaste(callback: OnPasteCallback)
```

进行粘贴操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onPaste(callback: OnPasteCallback): SearchAttribute--><!--Device-SearchAttribute-onPaste(callback: OnPasteCallback): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 是 | Executed when a paste operation is performed.Callback used to return the pasted text content.<br>**起始版本：** 18 |

## onSubmit

```TypeScript
onSubmit(callback: Callback<string>)
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onSubmit(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onSubmit(callback: Callback<string>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string> | 是 | 搜索提交回调，其返回值为当前搜索框中输入的文本内容。<br>**起始版本：** 18 |

## onSubmit

```TypeScript
onSubmit(callback: SearchSubmitCallback)
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时触发该回调事件，提交事件时提供保持Search编辑状态的方法。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onSubmit(callback: SearchSubmitCallback): SearchAttribute--><!--Device-SearchAttribute-onSubmit(callback: SearchSubmitCallback): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SearchSubmitCallback](arkts-arkui-searchsubmitcallback-t.md) | 是 | 点击搜索图标、搜索按钮或者按下软键盘搜索按钮时的回调事件。 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: OnTextSelectionChangeCallback)
```

文本选择的位置或编辑状态下光标位置发生变化时，触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): SearchAttribute--><!--Device-SearchAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 是 | 文本选择变化回调或光标位置变化回调。<br>**起始版本：** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

在搜索框将要绑定输入法前触发该回调。

<!--Del-->

在搜索框将要绑定输入法前，可以通过`UIContext`的系统接口[setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig-1)设置键盘的样式。<!--DelEnd-  
->

从API version 22开始，调用[IMEClient](../../../../reference/apis-arkui/arkui-ts/ts-text-common.md#imeclient20对象说明)的[setExtraConfig](../arkts-apis/arkts-arkui-text-common-imeclient-i.md#setextraconfig-1)方法可以设置输入法扩展信息。在绑定输入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。

IMEClient仅在onWillAttachIME执行期间有效，不可进行异步调用。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillAttachIME(callback: Callback<IMEClient>): SearchAttribute--><!--Device-SearchAttribute-onWillAttachIME(callback: Callback<IMEClient>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<IMEClient> | 是 | 在搜索框将要绑定输入法前触发该回调。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

在文本内容将要发生变化时，触发该回调。

onWillChange的回调时序晚于onWillInsert、onWillDelete，早于onDidInsert、onDidDelete。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<EditableTextChangeValue, boolean> | 是 | 在文本内容将要发生变化时的回调。<br/>返回true时，表示正常修改。返回false时，表示拦截此次触发。 |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

在进行复制操作前，触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillCopy(callback: Callback<string, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillCopy(callback: Callback<string, boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string, boolean> | 是 | 复制操作前的回调。回调参数类型为string时，表示将要被复制的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被复制，true：允许文本被复制；false：不允许文本被复制。 |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

在进行剪切操作前，触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillCut(callback: Callback<string, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillCut(callback: Callback<string, boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<string, boolean> | 是 | 剪切操作前的回调。回调参数类型为string时，表示将要被剪切的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被剪切，true：允许文本被剪切；false：不允许文本被剪切。 |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

在将要删除时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<DeleteValue, boolean> | 是 | 在将要删除时调用的回调。<br/>在返回true时，表示正常删除，返回false时，表示不删除。<br/>在预上屏删除操作时，该回调不触发。<br/>仅支持系统输入法输入的场景。 |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

在将要输入时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<InsertValue, boolean> | 是 | 在将要输入时调用的回调。<br/>在返回true时，表示正常插入，返回false时，表示不插入。<br/>在预上屏和候选词操作时，该回调不触发。<br/>仅支持系统输入法输入的场景。 |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

设置placeholder文本颜色，Wearable设备上默认值为'#99ffffff'。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-placeholderColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-placeholderColor(value: ResourceColor): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | placeholder文本颜色。<br />默认值：'#99182431'。 |

## placeholderFont

```TypeScript
placeholderFont(value?: Font)
```

设置placeholder文本样式，包括字体大小、字体粗细、字体族、字体风格。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-placeholderFont(value?: Font): SearchAttribute--><!--Device-SearchAttribute-placeholderFont(value?: Font): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 否 | placeholder文本样式。 |

## searchButton

```TypeScript
searchButton(value: ResourceStr, option?: SearchButtonOptions)
```

设置搜索框末尾搜索按钮。

点击搜索按钮，同时触发onSubmit与onClick回调。

Wearable设备上默认字体大小为18fp。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-searchButton(value: ResourceStr, option?: SearchButtonOptions): SearchAttribute--><!--Device-SearchAttribute-searchButton(value: ResourceStr, option?: SearchButtonOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 搜索框末尾搜索按钮文本内容。 <br>从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |
| option | [SearchButtonOptions](arkts-arkui-search-searchbuttonoptions-i.md) | 否 | 配置搜索框末尾搜索按钮文本样式。<br />默认值：<br />{<br />fontSize: '16fp',<br />fontColor: '#ff3f97e9'<br />}<br>**起始版本：** 10 |

## searchIcon

```TypeScript
searchIcon(value: IconOptions | SymbolGlyphModifier)
```

设置左侧搜索图标样式。

Wearable设备上默认图标大小为16vp。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-searchIcon(value: IconOptions | SymbolGlyphModifier): SearchAttribute--><!--Device-SearchAttribute-searchIcon(value: IconOptions | SymbolGlyphModifier): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | IconOptions \| SymbolGlyphModifier | 是 | 左侧搜索图标样式。&lt;!--RP1--&gt;<br />浅色模式默认值：<br />{<br />size: '16vp',<br/>color: '#99182431',<br />src: ' '<br />}<br />深色模式默认值：<br />{<br />size: '16vp',<br />color: '#99ffffff',<br/>src: ' '<br />} &lt;!--RP1End--&gt;<br>**起始版本：** 12 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-selectedBackgroundColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-selectedBackgroundColor(value: ResourceColor): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本选中底板颜色。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置搜索框内文本拖拽时的背板样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SelectedDragPreviewStyle \| undefined | 是 | 文本拖拽时的背板样式。<br/>设置为undefined时：背板颜色跟随主题，浅色模式显示白色，深色模式显示黑色。 |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

设置是否不弹出系统文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-selectionMenuHidden(value: boolean): SearchAttribute--><!--Device-SearchAttribute-selectionMenuHidden(value: boolean): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否不弹出系统文本选择菜单。<br />设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，不弹出系统文本选择菜单。<br />设置为false时，弹出系统文本选择菜单。<br />默认值：false |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

设置文本着色器效果，如线性渐变、径向渐变效果等。

> **说明：**  
>  
> 当同时设置shaderStyle和[strokeWidth](SearchAttribute#strokeWidth)时，shaderStyle不生效。  
>  
> shaderStyle的优先级高于[fontColor](SearchAttribute#fontColor)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-shaderStyle(shader: ShaderStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-shaderStyle(shader: ShaderStyle | undefined): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | ShaderStyle \| undefined | 是 | 文本着色器效果。<br/>值为undefined时，无渐变效果。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键传递。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-stopBackPress(isStopped: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-stopBackPress(isStopped: Optional<boolean>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否阻止返回键。<br/>true表示阻止，false表示不阻止。<br/>默认值：true。异常值取默认值。 |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

设置文本描边的颜色。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-strokeColor(color: Optional<ResourceColor>): SearchAttribute--><!--Device-SearchAttribute-strokeColor(color: Optional<ResourceColor>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)<ResourceColor> | 是 | 描边颜色。默认值为字体颜色，设置异常值时取默认值。 |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

设置文本描边拐角样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strokeJoinStyle | StrokeJoinStyle \| undefined | 是 | 文本描边拐角样式。<br/>值为undefined时，按照StrokeJoinStyle.MITER_JOIN处理，请参考[StrokeJoinStyle](../arkts-apis/arkts-arkui-text-common-strokejoinstyle-e.md)，文本拐角处表现为锐角。 |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

设置文本描边的宽度。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-strokeWidth(width: Optional<LengthMetrics>): SearchAttribute--><!--Device-SearchAttribute-strokeWidth(width: Optional<LengthMetrics>): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)<LengthMetrics> | 是 | 文本描边的宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。<br/>若设置值小于0，显示实心字；若大于0，显示空心字。<br/>默认值为0，不做描边处理。 |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

设置文本在搜索框中的对齐方式。目前支持的对齐方式有：TextAlign.Start、TextAlign.Center、TextAlign.End、TextAlign.LEFT、TextAlign.RIGHT。TextAlign.JUSTIFY的对齐方式按照TextAlign.Start处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-textAlign(value: TextAlign): SearchAttribute--><!--Device-SearchAttribute-textAlign(value: TextAlign): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextAlign](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textalign-e.md) | 是 | 文本在搜索框中的对齐方式。<br/>默认值：TextAlign.Start |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

指定文本排版方向，未通过该接口设置时，默认文本排版方向遵循组件布局方向。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-textDirection(direction: TextDirection | undefined): SearchAttribute--><!--Device-SearchAttribute-textDirection(direction: TextDirection | undefined): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | TextDirection \| undefined | 是 | 文本排版方向。<br/>设置为undefined时，按照TextDirection.DEFAULT处理，表现为文本排版方向遵循组件布局方向。 |

## textFont

```TypeScript
textFont(value?: Font)
```

设置搜索框内输入文本样式，包括字体大小、字体粗细、字体族、字体风格。

Wearable设备上默认字体大小为18fp。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-textFont(value?: Font): SearchAttribute--><!--Device-SearchAttribute-textFont(value?: Font): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 否 | 搜索框内输入文本样式。 |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

设置首行文本缩进。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-textIndent(value: Dimension): SearchAttribute--><!--Device-SearchAttribute-textIndent(value: Dimension): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 首行文本缩进。<br/>默认值：0 <br/>单位：[vp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) <br/>取值范围：大于等于0。设置负数时，按默认值处理。 |

## type

```TypeScript
type(value: SearchType)
```

设置输入框类型。

不同的SearchType会拉起对应类型的键盘，同时限制输入。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchAttribute-type(value: SearchType): SearchAttribute--><!--Device-SearchAttribute-type(value: SearchType): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SearchType](arkts-arkui-search-searchtype-e.md) | 是 | 输入框类型。<br/>默认值：SearchType.NORMAL |

