# Search属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。除支持[通用事件](arkts-arkui-commonmethod-c.md)外，还支持以下事件。

**继承/实现关系：** SearchAttribute extends CommonMethod<SearchAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

设置自动大小写模式的文本模式，只提供接口能力，具体实现以输入法应用为主。未通过该接口设置时，默认不产生大小写转换效果，具体实现以输入法应用为主。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | 是 | 自动大小写模式，用于设置输入法的大小写转换规则，具体实现以输入法应用为主。 |

## cancelButton

```TypeScript
cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions)
```

设置右侧清除按钮样式。示例请参考 示例2（设置搜索和删除图标）和 示例11（设置symbol类型清除按钮）。未通 过该接口设置时，默认清除按钮样式为CancelButtonStyle.INPUT（输入样式），图标大小为16vp（Wearable设备上默认图标大小为18fp），颜色为'#99ffffff'（白色，不透明度约为60%）。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) \| [CancelButtonSymbolOptions](arkts-arkui-cancelbuttonsymboloptions-i.md) | 是 | 右侧清除按钮样式。当style为CancelButtonStyle.CONSTANT时，默认显示 清除样式。<br>**起始版本：** 12 |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

设置光标样式。未通过该接口设置时，默认光标宽度为2.0vp，颜色为'#007DFF'（蓝色）。

> **说明：**
> 
> 从API version 12开始，此接口支持设置文本手柄颜色，光标和文本手柄颜色保持一致。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | 是 | 光标样式。 |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

设置是否开启行首标点符号压缩。开启后，行首标点符号左侧的间距将被压缩，适用于追求排版美观的中文、日文等CJK文本场景。

> **说明：**
> 
> - 行首标点符号默认不压缩。
> 
> - 支持压缩的标点符号，请参考[ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md)的行首压缩的标点范围。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启行首标点符号压缩。 true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置输入的文本是否可复制。未通过该接口设置时，默认支持设备内复制（CopyOptions.LocalDevice）。设置CopyOptions.None时，当前Search中的文字无法被复制、剪切、翻译、分享、搜索和帮写，支持粘贴和全选。设置CopyOptions.None时，不允许拖拽。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CopyOptions | 是 | 输入的文本是否可复制。    **说明：** 当copyOption不为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时， [enableSelectedDataDetector](#enableselecteddatadetector)功能不生效。 |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

设置自定义键盘。当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认值。自定义键盘采用覆盖原始界面的方式呈现。当未开启避让模式或输入框不需要避让时，不会对应用原始界面产生压缩或上提。自定义键盘无法获取焦点，但是会拦截手势事件。默认在输入控件失去焦点时，关闭自定义键盘，开发者也可以通过[stopEditing](arkts-arkui-searchcontroller-c.md#stopediting)方法控制键盘关闭。当设置自定义键盘时，可以通过绑定[onKeyPreIme](arkts-arkui-commonmethod-c.md#onkeypreime)事件规避物理键盘的输入。从API version 23开始，自定义键盘可以通过 [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature)开启接续，在切换至 其他自定义键盘时，会直接切换，不会触发键盘关闭和拉起动画。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| ComponentContent \| undefined | 是 | 自定义键盘。设定值为undefined时，关闭自定义键盘。<br>**起始版本：** 22 |
| options | [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | 否 | 设置自定义键盘是否支持避让功能。不传入时使用默认配置。<br>**起始版本：** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

设置文本装饰线类型样式及其颜色。未通过该接口设置时，默认装饰线类型为TextDecorationType.None（无装饰线），颜色为Color.Black（黑色），样式为TextDecorationStyle.SOLID（实线） ，粗细缩放为1.0。

> **说明：**
> 
> - 当文字的下边缘轮廓与装饰线位置相交时，会触发下划线避让规则，下划线将在这些字符处避让文字。常见”gjyqp”等英文字符。
> 
> - 当文本装饰线的颜色设置为Color.Transparent时，装饰线颜色设置为跟随每行第一个字的字体颜色。当文本装饰线的颜色设置为透明色16进制对应值”#00FFFFFF”时，装饰线颜色设置为透明色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | 是 | 文本装饰线对象。 |

## dividerColor

```TypeScript
dividerColor(color: Optional<ColorMetrics>)
```

设置输入框分割线颜色。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ColorMetrics&gt; | 是 | 设置分割线颜色。 默认使用系统的主题色：浅色模式下为0x33000000，表示黑色（20%不透明度），深色模式下为0x33FFFFFF，表示白色（20%不透明度）。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置自定义菜单扩展项，允许用户设置扩展项的文本内容、图标、回调方法。调用[disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems)或 [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems)接口屏蔽文本 选择菜单内的系统服务菜单项时，editMenuOptions接口内回调方法onCreateMenu的入参列表中不包含被屏蔽的菜单选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | 是 | 扩展菜单选项，用于设置自定义菜单扩展项的文本内容、图标和回调方法。当需要在文本选择菜单中添加自定义选项时使用此参数。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。未通过该接口设置时，默认不开启中文与西文的自动间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启中文与西文的自动间距。 true为开启自动间距，false为不开启。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

设置是否开启触控反馈。未通过该接口设置时，默认开启触控反馈。开启触控反馈时，需要在工程的[module.json5](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段以开启振动权限，配置如 下：

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否开启触控反馈。 true表示开启触控反馈，false表示不开启触控反馈。 |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

设置Search通过点击以外的方式获焦时，是否主动拉起软键盘。未通过该接口设置时，默认主动拉起软键盘。从API version 10开始，获焦默认绑定输入法。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | Search获焦时，是否主动拉起软键盘。 true表示主动拉起，false表示不主动拉起。 |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启输入预上屏。未通过该接口设置时，默认开启输入预上屏。预上屏内容定义为文字暂存态，目前不支持文字拦截功能。

> **说明：**
> 
> “预上屏”描述的是一种文字暂存状态。需要在输入法中开启预上屏功能，在输入文本过程中，未确认输入候选词时，文本框中显示标记文本。例如，通过拼音输入中文时，未确定候选词之前，在输入框中显示拼音字母，该状态称为文字预上屏。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否开启输入预上屏。 true表示开启输入预上屏，false表示不开启输入预上屏。 |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

设置是否对选中文本进行实体识别。该接口依赖设备底层应具有文本识别能力，否则设置不会生效。未通过该接口设置时，默认开启选中文本实体识别，并识别所有类型的实体，默认启用AI菜单功能。启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。AI菜单功能启用时，在组件中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括[TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md)中的url（打开链接）、email（新建邮件）、phoneNumber（ 呼叫）、address（导航前往）、dateTime（新建日程）。AI菜单生效时，选中范围内需包括且仅包括一个完整的AI实体，才能展示对应的选项。该菜单项与[TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md)中的askAI菜单项不同时出现。需要CopyOptions为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时，本功能生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 开启选中文本实体识别。 true：开启识别，false：关闭识别。 |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

设置输入法回车键类型。未通过该接口设置时，默认输入法回车键类型为EnterKeyType.Search。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | EnterKeyType | 是 | 输入法回车键类型。 |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。不通过该接口设置，默认行高不基于文字实际高度自适应。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 行高是否基于文字实际高度自适应。 此接口仅当行高小于文字实际高度时生效。 true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置输入文本的字体颜色。未通过该接口设置时，默认输入文本的字体颜色为'#FF182431'（深灰色），Wearable设备上默认为'#dbffffff'（白色，不透明度约为86%）。fontSize、fontStyle、 fontWeight和fontFamily在[textFont](#textfont)属性中设置。

> **说明：**
> 
> 当同时设置fontColor和[shaderStyle](#shaderstyle)时，fontColor不生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入文本的字体颜色。    **说明：** 当同时设置fontColor和[shaderStyle](#shaderstyle)时，fontColor设置不生效。 |

## fontFeature

```TypeScript
fontFeature(value: string)
```

设置文字特性效果，比如数字等宽的特性。格式为：normal \| \&lt;feature-tag-value\&gt;。\&lt;feature-tag-value\&gt;的格式为：\&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]。\&lt;feature-tag-value\&gt;的个数可以有多个，中间用','隔开。例如，使用等宽数字的输入格式为："ss01" on。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 文字特性效果，用于设置OpenType字体的高级排版能力，如连字、数字等宽等。 格式为："ss01" on。更多支持的属性详见fontFeature属性列表。 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

设置文本在行内垂直居中，将行间距平分至行的顶部与底部。适用于多行文本排版中需要精确控制文本垂直居中对齐的场景，如文本与图标混排、多语言混排等。未通过该接口设置时，默认不平分行间距。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置文本是否垂直居中。 true表示将行间距平分至行的顶部与底部，false则不平分。 |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否在首行和尾行增加间距以避免文字截断。 true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。适用于限制用户输入格式的场景，如仅允许输入字母、数字或特定字符等。单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。设置inputFilter且输入的字符不为空字符，会导致设置输入框类型(即type接口)附带的文本过滤效果失效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 输入过滤器的正则表达式。匹配该表达式的输入允许显示，不匹配的输入将被过滤。 |
| error | Callback &lt;string&gt; | 否 | 正则匹配失败时，返回被过滤的内容。不传入时不触发该回调。 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置输入框拉起的键盘样式，需要输入法适配后生效。未通过该接口设置时，默认键盘样式为KeyboardAppearance.NONE_IMMERSIVE（非沉浸模式）。具体参考 [输入法应用沉浸模式](../../../inputmethod/inputmethod-immersive-mode-guide.md)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-optional-t.md)&lt;[KeyboardAppearance](../arkts-apis/arkts-arkui-keyboardappearance-e.md)&gt; | 是 | 键盘样式。 |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

设置文本字符间距。设置该值为百分比时，按默认值显示。设置该值为0时，按默认值显示。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。当取值为负值时，文字会发生压缩，负值过小时会将组件内容区大小压缩为0，导致无内容显示。对每个字符生效，包括行尾字符。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本字符间距。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

设置文本的文本行高，设置值不大于0时，不限制文本行高，自适应字体大小，number类型时单位为fp。

> **说明：**
> 
> 特殊字符字体高度远超出同行的其他字符高度时，文本框出现截断、遮挡、内容相对位置发生变化等不符合预期的显示异常，需要开发者调整组件高度、行高等属性，修改对应的页面布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本的文本行高。 number类型时单位为fp，string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。 |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

设置文本最大的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 文本最大的字体缩放倍数，支持undefined类型。 取值范围：[1, +∞)    **说明：** 设置的值小于1时，按值为1处理。设置undefined时维持原值，异常值默认不生效。 设置maxFontScale属性后，search组件内容最多放大到2倍。 使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和 [app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见 示例19（设置最小字体范围与最大字体范围）。 |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

设置文本最大显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。需配合[minFontSize](#minfontsize)以及布局大小限制使用，单独设置不生效。自适应字号生效时，fontSize设置不生效。maxFontSize小于等于0或者maxFontSize小于minFontSize时，自适应字号不生效，此时按照[textFont](#textfont)属性里面size的取值生效，未设 置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最大显示字号。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) |

## maxLength

```TypeScript
maxLength(value: number)
```

设置文本的最大输入字符数。默认不设置最大输入字符数限制。到达文本最大字符限制，将无法继续输入字符。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 文本的最大输入字符数。取值范围：[0, +∞)。当value &lt;0时，按照默认值处理，不设限制。 |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

设置文本最小的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 文本最小的字体缩放倍数，支持undefined类型。 取值范围：[0, 1]    **说明：** 设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。设置undefined时维持原值，异常值默认不生效。 使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和 [app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见 示例19（设置最小字体范围与最大字体范围）。 |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

设置文本最小显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。需配合[maxFontSize](#maxfontsize)以及布局大小限制使用，单独设置不生效。自适应字号生效时，fontSize设置不生效。minFontSize小于或等于0时，自适应字号不生效，此时按照[textFont](#textfont)属性里面size的取值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最小显示字号。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

输入内容发生变化时，触发该回调。在本回调中，若执行了光标操作，需要开发者在预上屏场景下依据previewText参数调整光标逻辑，以适应预上屏场景。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnContentScrollCallback | 是 | 文本内容滚动回调，回调参数包括totalOffsetX（水平滚动偏移量）和totalOffsetY（垂直滚动偏移量）。<br>**起始版本：** 18 |

## onCopy

```TypeScript
onCopy(callback: Callback<string>)
```

进行复制操作时，触发该回调。

> **说明：**
> 
> onWillCopy先于onCopy触发。onWillCopy回调返回true时允许复制操作继续执行，返回false时拦截复制操作且不触发onCopy。两者可同时使用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string&gt; | 是 | 复制回调，其返回值为复制的文本内容。<br>**起始版本：** 18 |

## onCut

```TypeScript
onCut(callback: Callback<string>)
```

进行剪切操作时，触发该回调。

> **说明：**
> 
> onWillCut先于onCut触发。onWillCut回调返回true时允许剪切操作继续执行，返回false时拦截剪切操作且不触发onCut。两者可同时使用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string&gt; | 是 | 剪切回调，其返回值为剪切的文本内容。<br>**起始版本：** 18 |

## onDidDelete

```TypeScript
onDidDelete(callback: Callback<DeleteValue>)
```

在删除完成时，触发该回调。

> **说明：**
> 
> 点击清除按钮不触发onDidDelete回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md)&gt; | 是 | 在删除完成时调用的回调。 仅支持系统输入法输入的场景。 |

## onDidInsert

```TypeScript
onDidInsert(callback: Callback<InsertValue>)
```

在输入完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md)&gt; | 是 | 在输入完成时调用的回调。 仅支持系统输入法输入的场景。 |

## onEditChange

```TypeScript
onEditChange(callback: Callback<boolean>)
```

输入状态变化时，触发该回调。有光标时为编辑态，无光标时为非编辑态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;boolean&gt; | 是 | 编辑状态改变回调，其返回值为true表示正在输入，false表示无焦点，无法输入文字。 |

## onPaste

```TypeScript
onPaste(callback: OnPasteCallback)
```

进行粘贴操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnPasteCallback | 是 | Executed when a paste operation is performed.Callback used to return the pasted text content.<br>**起始版本：** 18 |

## onSubmit

```TypeScript
onSubmit(callback: Callback<string>)
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string&gt; | 是 | 搜索提交回调，其返回值为当前搜索框中输入的文本内容。<br>**起始版本：** 18 |

## onSubmit

```TypeScript
onSubmit(callback: SearchSubmitCallback)
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时触发该回调事件，提交事件时提供保持Search编辑状态的方法。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

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

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnTextSelectionChangeCallback | 是 | 文本选择变化回调或光标位置变化回调。<br>**起始版本：** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

在搜索框将要绑定输入法前触发该回调。<!--Del-->在搜索框将要绑定输入法前，可以通过`UIContext`的系统接口 setKeyboardAppearanceConfig设置键盘的样式。&lt;!--DelEnd- -&gt;从API version 22开始，调用[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)的[setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig)方法可以设置输入法扩展信息。在绑定输 入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。IMEClient仅在onWillAttachIME执行期间有效，不可进行异步调用。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; | 是 | 在搜索框将要绑定输入法前触发该回调。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

在文本内容将要发生变化时，触发该回调。onWillChange的回调时序晚于onWillInsert、onWillDelete，早于onDidInsert、onDidDelete。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[EditableTextChangeValue](../arkts-apis/arkts-arkui-editabletextchangevalue-i.md), boolean&gt; | 是 | 在文本内容将要发生变化时的回调。 返回true时，表示正常修改。返回false时，表示拦截此次触发。 |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

在进行复制操作前，触发该回调。

> **说明：**
> 
> onWillCopy先于onCopy触发。onWillCopy回调返回true时允许复制操作继续执行，返回false时拦截复制操作且不触发onCopy。两者可同时使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string, boolean&gt; | 是 | 复制操作前的回调。回调参数类型为string时，表示将要被复制的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被复 制，true：允许文本被复制；false：不允许文本被复制。 |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

在进行剪切操作前，触发该回调。

> **说明：**
> 
> onWillCut先于onCut触发。onWillCut回调返回true时允许剪切操作继续执行，返回false时拦截剪切操作且不触发onCut。两者可同时使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string, boolean&gt; | 是 | 剪切操作前的回调。回调参数类型为string时，表示将要被剪切的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被剪 切，true：允许文本被剪切；false：不允许文本被剪切。 |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

在将要删除时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md), boolean&gt; | 是 | 在将要删除时调用的回调。 在返回true时，表示正常删除，返回false时，表示不删除。 在预上屏删除操作时，该回调不触发。 仅支持系统输入法输入的场景。 |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

在将要输入时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md), boolean&gt; | 是 | 在将要输入时调用的回调。 在返回true时，表示正常插入，返回false时，表示不插入。 在预上屏和候选词操作时，该回调不触发。 仅支持系统输入法输入的场景。 |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

设置placeholder文本颜色。未通过该接口设置时，默认placeholder文本颜色为'#99182431'（深灰色，不透明度约为60%），Wearable设备上默认为'#99ffffff'（白色，不透明度约为60%）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | placeholder文本颜色。 |

## placeholderFont

```TypeScript
placeholderFont(value?: Font)
```

设置placeholder文本样式，包括字体大小、字体粗细、字体族、字体风格。Wearable设备上默认字体大小为18fp。

> **说明：**
> 
> 可以使用[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)注册自定义字体。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 否 | placeholder文本样式。不传入时使用系统默认字体样式。 |

## searchButton

```TypeScript
searchButton(value: ResourceStr, option?: SearchButtonOptions)
```

设置搜索框末尾搜索按钮。点击搜索按钮，同时触发onSubmit与onClick回调。Wearable设备上默认字体大小为18fp。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 搜索框末尾搜索按钮文本内容。 从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |
| option | [SearchButtonOptions](arkts-arkui-searchbuttonoptions-i.md) | 否 | 配置搜索框末尾搜索按钮样式。 默认值： {fontSize: '16fp', fontColor: '#ff3f97e9'}<br>**起始版本：** 10 |

## searchIcon

```TypeScript
searchIcon(value: IconOptions | SymbolGlyphModifier)
```

设置左侧搜索图标样式。如果与参数icon同时设置，本属性优先生效。Wearable设备上默认图标大小为16vp。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IconOptions](arkts-arkui-iconoptions-i.md) \| SymbolGlyphModifier | 是 | 左侧搜索图标样式。如果与参数icon同时设置，本属性优先生效。<!--RP1--> 浅色模式默认值： {size: '16vp', color: '#99182431', src: ' '} 深色模式默认值： {size: '16vp', color: '#99ffffff', src: ' '} <!--RP1End--><br>**起始版本：** 12 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置搜索框内文本拖拽时的背板样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) \| undefined | 是 | 文本拖拽时的背板样式。 设置为undefined时：背板颜色跟随主题，浅色模式显示白色，深色模式显示黑色。 |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

设置是否不弹出系统文本选择菜单。未通过该接口设置时，默认弹出系统文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否不弹出系统文本选择菜单。 设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，不弹出系统文本选择菜单。 设置为false时，弹出系统文本选择菜单。 |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

设置文本着色器效果，如线性渐变、径向渐变效果等。未通过该接口设置时，默认无渐变效果。

> **说明：**
> 
> - 当同时设置shaderStyle和[strokeWidth](#strokewidth)时，shaderStyle不生效。
> 
> - 当同时设置shaderStyle和[fontColor](#fontcolor)时，fontColor不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) \| undefined | 是 | 文本着色器效果。    **说明：** 当同时设置shaderStyle和[strokeWidth](#strokewidth)时，shaderStyle不生效。 当同时设置shaderStyle和[fontColor](#fontcolor)时，fontColor不生效。 值为undefined时，无渐变效果。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键事件向上传递。设置为true时，拦截返回键事件，不触发系统的默认返回行为；设置为false时，返回键事件正常向上传递。适用于需要自定义返回键行为的场景，如在搜索过程中阻止返回键直接退出以避免误操作，或需要弹出确认 提示后再退出等场景。未通过该接口设置时，默认阻止返回键。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否阻止返回键。 true表示阻止，false表示不阻止。 异常值取默认值。 |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

设置文本描边的颜色。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 描边颜色。未通过该接口设置时，默认描边颜色为字体颜色，设置异常值时取默认值。需配合 [strokeWidth](#strokewidth)设置描边宽度后生效。 |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

设置文本描边拐角样式，仅在使用strokeWidth设置文本描边时生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) \| undefined | 是 | 文本描边拐角样式。 值为undefined时，按照StrokeJoinStyle.MITER_JOIN处理，请参考[StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md)，文本拐角处表现为锐角。 |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

设置文本描边的宽度。未通过该接口设置时，默认值为0，不做描边处理。

> **说明：**
> 
> 当同时设置strokeWidth和[shaderStyle](#shaderstyle)时，shaderStyle不生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 文本描边的宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。 若设置值小于0，显示实心字；若大于0，显示空心字。    **说明：** 当同时设置strokeWidth和[shaderStyle](#shaderstyle)时，shaderStyle不生效。 [strokeJoinStyle](#strokejoinstyle)仅在使用strokeWidth设置文本描边时生效。 |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

设置文本在搜索框中的对齐方式。目前支持的对齐方式有：TextAlign.Start、TextAlign.Center、TextAlign.End、TextAlign.LEFT、TextAlign.RIGHT。 TextAlign.JUSTIFY的对齐方式按照TextAlign.Start处理。未通过该接口设置时，默认对齐方式为TextAlign.Start。

> **说明：**
> 
> textAlign只能调整文本整体的布局，不影响字符的显示顺序。若需要调整字符的显示顺序，请参考[镜像状态字符对齐](../../../ui/arkts-internationalization.md#镜像状态字符对齐)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | TextAlign | 是 | 文本在搜索框中的对齐方式。 |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

指定文本排版方向，未通过该接口设置时，默认文本排版方向遵循组件布局方向。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | TextDirection \| undefined | 是 | 文本排版方向。 设置为undefined时，按照TextDirection.DEFAULT处理，表现为文本排版方向遵循组件布局方向。 |

## textFont

```TypeScript
textFont(value?: Font)
```

设置搜索框内输入文本样式，包括字体大小、字体粗细、字体族、字体风格。Wearable设备上默认字体大小为18fp。

> **说明：**
> 
> 可以使用[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)注册自定义字体。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 否 | 搜索框内输入文本样式。不传入时使用系统默认字体样式。 |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

设置首行文本缩进。未通过该接口设置时，默认首行文本缩进为0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 首行文本缩进。 单位：[vp](../arkts-apis/arkts-arkui-length-t.md) 取值范围：大于等于0。设置负数时，按默认值处理。 |

## type

```TypeScript
type(value: SearchType)
```

设置输入框类型。未通过该接口设置时，默认输入框类型为SearchType.NORMAL（基本输入模式，无特殊限制）。不同的SearchType会拉起对应类型的键盘，同时限制输入。

> **说明：**
> 
> 如果同时设置了[inputFilter](#inputfilter)属性且输入的字符不为空字符，type接口附带的文本过滤效果将失效，以inputFilter的过滤规则为准。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SearchType](arkts-arkui-searchtype-e.md) | 是 | 输入框类型。 当同时设置了[inputFilter](#inputfilter)且输入的字符不为空字符时，type接口附带的文本过滤效果失效。 |
