# TextArea属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** TextAreaAttribute extends [CommonMethod<TextAreaAttribute>](CommonMethod<TextAreaAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class TextAreaAttribute extends CommonMethod<TextAreaAttribute>--><!--Device-unnamed-declare class TextAreaAttribute extends CommonMethod<TextAreaAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

设置自动大小写模式的文本模式，只提供接口能力，具体实现以输入法应用为主。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextAreaAttribute--><!--Device-TextAreaAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | 是 | 自动大小写模式，默认状态无效。 |

## barState

```TypeScript
barState(value: BarState)
```

设置输入框滚动条的显示模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-barState(value: BarState): TextAreaAttribute--><!--Device-TextAreaAttribute-barState(value: BarState): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 输入框滚动条的显示模式。<br/>默认值：BarState.Auto |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

设置输入框光标颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-caretColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-caretColor(value: ResourceColor): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入框光标颜色。<br/>默认值：'#007DFF' |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

设置光标风格。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-caretStyle(value: CaretStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-caretStyle(value: CaretStyle): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | 是 | 光标的风格。 |

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

<!--Device-TextAreaAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启行首标点符号压缩。<br/>true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## contentType

```TypeScript
contentType(contentType: ContentType)
```

设置自动填充类型。<!--RP3--><!--RP3End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-contentType(contentType: ContentType): TextAreaAttribute--><!--Device-TextAreaAttribute-contentType(contentType: ContentType): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contentType | [ContentType](../../apis-audio-kit/arkts-apis/arkts-audio-audio-contenttype-e.md) | 是 | 自动填充类型。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置输入的文本是否可复制。设置CopyOptions.None时，只支持粘贴和全选。

设置CopyOptions.None时，不支持拖拽操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-copyOption(value: CopyOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-copyOption(value: CopyOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | 是 | 输入的文本是否可复制。<br/>默认值：CopyOptions.LocalDevice，支持设备内复制。 |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

设置自定义键盘。

当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。

自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度则使用系统默认值。

自定义键盘采用覆盖原始界面的方式呈现，当没有开启避让模式或者输入框不需要避让的场景，不会对应用原始界面产生压缩或者上提。

自定义键盘无法获取焦点，但是会拦截手势事件。

默认在输入控件失去焦点时，关闭自定义键盘，开发者也可以通过[TextAreaController](arkts-arkui-textareacontroller-c.md).[stopEditing](arkts-arkui-textareacontroller-c.md#stopediting)方法控制键盘关闭。

当设置自定义键盘时，可以通过绑定[onKeyPreIme](arkts-arkui-commonmethod-c.md#onkeypreime)事件规避物理键盘的输入。

从API version 23开始，自定义键盘可以通过[setCustomKeyboardContinueFeature](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#setcustomkeyboardcontinuefeature23)开启接续，在切换至其他自定义键盘时，会直接切换，不会触发键盘关闭和拉起动画。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| ComponentContent \| undefined | 是 | 自定义键盘。设定值为undefined时，关闭自定义键盘。<br>**起始版本：** 22 |
| options | [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | 否 | 设置自定义键盘是否支持避让功能。<br>**起始版本：** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

设置文本装饰线类型样式及其颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-decoration(value: TextDecorationOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-decoration(value: TextDecorationOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | 是 | 文本装饰线对象。<br />默认值：{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID,<br/> thicknessScale: 1.0<br/>} |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置自定义菜单扩展项，允许用户设置扩展项的文本内容、图标、回调方法。

调用[disableMenuItems](../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20)或[disableSystemServiceMenuItems](../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20)接口屏蔽文本选择菜单内的系统服务菜单项时，editMenuOptions接口内回调方法[onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu)的入参列表中不包含被屏蔽的菜单选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | 是 | 扩展菜单选项。 |

## ellipsisMode

```TypeScript
ellipsisMode(mode: Optional<EllipsisMode>)
```

设置省略位置。ellipsisMode属性需要配合[textOverflow](TextAreaAttribute#textOverflow)设置为TextOverflow.Ellipsis以及[maxLines](TextAreaAttribute#maxLines(value: number))使用，单独设置ellipsisMode属性不生效。

EllipsisMode.START和EllipsisMode.CENTER仅在[maxLines](TextAreaAttribute#maxLines(value: number))设置为1生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextAreaAttribute--><!--Device-TextAreaAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;EllipsisMode&gt; | 是 | 省略位置。 <br />默认值：EllipsisMode.END |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

设置是否启用自动填充。<!--RP2--><!--RP2End-->

<!--RP6--><!--RP6End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enableAutoFill(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableAutoFill(value: boolean): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用自动填充。<br/>true表示启用，false表示不启用。<br/>默认值：true |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启中文与西文的自动间距。<br/>true为开启自动间距，false为不开启。<br />默认值：false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

设置是否开启触控反馈。

开启触控反馈时，需要在工程的[module.json5](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段以开启振动权限，配置如下：

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enableHapticFeedback(isEnabled: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableHapticFeedback(isEnabled: boolean): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否开启触控反馈。<br/>true表示开启，false表示不开启。<br/>默认值：true |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

设置TextArea通过点击以外的方式获焦时，是否主动拉起软键盘。

从API version 10开始，获焦默认绑定输入法。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enableKeyboardOnFocus(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableKeyboardOnFocus(value: boolean): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 通过点击以外的方式获焦时，是否主动拉起软键盘。<br/>true表示主动拉起，false表示不主动拉起。<br/>默认值：true |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启输入预上屏。

预上屏内容定义为文字暂存态，目前不支持文字拦截功能。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enablePreviewText(enable: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enablePreviewText(enable: boolean): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否开启输入预上屏。<br/>true表示开启，false表示不开启。<br/>默认值：true |

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

<!--Device-TextAreaAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAreaAttribute-End-->

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
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-enterKeyType(value: EnterKeyType): TextAreaAttribute--><!--Device-TextAreaAttribute-enterKeyType(value: EnterKeyType): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-enterkeytype-e.md) | 是 | 输入法回车键类型。<br/>默认值：EnterKeyType.NEW_LINE |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。不通过该接口设置，默认行高不基于文字实际高度自适应。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 行高是否基于文字实际高度自适应。<br/>true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-fontColor(value: ResourceColor): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。 |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

设置字体列表。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontFamily(value: ResourceStr): TextAreaAttribute--><!--Device-TextAreaAttribute-fontFamily(value: ResourceStr): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 字体列表。默认字体'HarmonyOS Sans'。<br>使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。 |

## fontFeature

```TypeScript
fontFeature(value: string)
```

设置文字特性效果，比如数字等宽的特性。

格式为：normal \| \&lt;feature-tag-value\&gt;

\&lt;feature-tag-value\&gt;的格式为：\&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]

\&lt;feature-tag-value\&gt;的个数可以有多个，中间用','隔开。

例如，使用等宽数字的输入格式为："ss01" on。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontFeature(value: string): TextAreaAttribute--><!--Device-TextAreaAttribute-fontFeature(value: string): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 文字特性效果。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置字体大小。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontSize(value: Length): TextAreaAttribute--><!--Device-TextAreaAttribute-fontSize(value: Length): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。fontSize为number类型时，使用fp单位。字体默认大小16fp，Wearable设备上默认值为：18fp。不支持设置百分比字符串。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontStyle(value: FontStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-fontStyle(value: FontStyle): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FontStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontstyle-e.md) | 是 | 字体样式。<br/>默认值：FontStyle.Normal |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

设置文本的字体粗细，设置过大可能会在不同字体下有截断。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAreaAttribute--><!--Device-TextAreaAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| ResourceStr | 是 | 文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。<br/>默认值：FontWeight.Normal <br>从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

设置文本在行内垂直居中，将行间距平分至行的顶部与底部。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-halfLeading(halfLeading: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-halfLeading(halfLeading: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置文本是否垂直居中。<br/>true表示将行间距平分至行的顶部与底部，false则不平分。<br/>默认值：false |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

设置文本自适应高度的方式。

当设置为TextHeightAdaptivePolicy.MAX_LINES_FIRST时，优先使用[maxLines](TextAreaAttribute#maxLines(value: number))属性来调整文本高度。如果使用maxLines属性的布局大小超过了布局约束，则尝试在[minFontSize](TextAreaAttribute#minFontSize)和[maxFontSize](TextAreaAttribute#maxFontSize)的范围内缩小字体以显示更多文本。

组件设置为内联输入风格，编辑态与非编辑态存在字体大小不一致情况。

当设置为TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST时，优先使用minFontSize属性来调整文本高度。如果使用minFontSize属性可以将文本布局在一行中，则尝试在minFontSize和maxFontSize的范围内增大字体并使用最大可能的字体大小。

当设置为TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST时，优先使用布局约束来调整文本高度。如果布局大小超过布局约束，则尝试在minFontSize和maxFontSize的范围内缩小字体以满足布局约束。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute--><!--Device-TextAreaAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | 是 | 文本自适应高度的方式。<br/>默认值：TextHeightAdaptivePolicy.MAX_LINES_FIRST |

## horizontalScrolling

```TypeScript
horizontalScrolling(enabled: Optional<boolean>)
```

设置当文本宽度超过内容区宽度时是否启用水平滚动。未通过该接口设置时，禁用水平滚动。
> **说明：**  
>  
> 以下场景不支持水平滚动：设置[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)<!--Del-->；启用  
> [voiceButton](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea-sys.md#voicebutton23)<!--  
> DelEnd-->。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-horizontalScrolling(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-horizontalScrolling(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用水平滚动。<br/>true表示启用水平滚动；false表示禁用水平滚动，文本将自动换行。 |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-includeFontPadding(include: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-includeFontPadding(include: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否在首行和尾行增加间距以避免文字截断。<br/>true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: (value: string) => void)
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。

单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。

从API version 11开始，设置inputFilter且输入的字符不为空字符，会导致[type](TextAreaAttribute#type)接口附带的文本过滤效果失效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-inputFilter(value: ResourceStr, error?: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-inputFilter(value: ResourceStr, error?: (value: string) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 正则表达式。 |
| error | (value: string) =&gt; void | 否 | 正则匹配失败时，返回被过滤的内容。正则匹配成功时，无返回。 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置输入框拉起的键盘样式，需要输入法适配后生效。具体参考[输入法应用沉浸模式](../../../inputmethod/inputmethod-immersive-mode-guide.md)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextAreaAttribute--><!--Device-TextAreaAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-optional-t.md)&lt;KeyboardAppearance&gt; | 是 | 键盘样式。<br/>默认值：KeyboardAppearance.NONE_IMMERSIVE |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

设置文本字符间距。设置该值为百分比时，按默认值显示。当设置该值为0时，使用默认值。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

当取值为负值时，文字会发生压缩，负值过小时会将组件内容区大小压缩为0，导致无内容显示。

对每个字符生效，包括行尾字符。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-letterSpacing(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-letterSpacing(value: number | string | Resource): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本字符间距。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

设置折行规则。该属性在[wordBreak](TextAreaAttribute#wordBreak)不等于WordBreak.BREAK_ALL的时候生效，不支持连词符。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute--><!--Device-TextAreaAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | 是 | 文本的折行规则。 <br />默认值：LineBreakStrategy.GREEDY |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

设置文本的文本行高，设置值不大于0时，不限制文本行高，自适应字体大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-lineHeight(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-lineHeight(value: number | string | Resource): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本的文本行高。需要显式指定[像素单位](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，如'10px'，也可设置百分比字符串，如'100%'。<br>**说明**：不指定像素单位时，默认单位fp，如'10'，等同于10。 |

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics)
```

设置文本的行间距，设置值不大于0时，取默认值0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics): TextAreaAttribute--><!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 文本的行间距。默认值：0 |

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics, options?: LineSpacingOptions)
```

设置文本的行间距。当不配置LineSpacingOptions时，首行上方和尾行下方默认会有行间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 文本的行间距。设置值不大于0时，取默认值0。 |
| options | [LineSpacingOptions](../arkts-apis/arkts-arkui-linespacingoptions-i.md) | 否 | 设置行间距配置项。<br/>默认值：{ onlyBetweenLines: false } |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

设置文本最大的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-maxFontScale(scale: Optional<number|Resource>): TextAreaAttribute--><!--Device-TextAreaAttribute-maxFontScale(scale: Optional<number|Resource>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number\|Resource&gt; | 是 | 文本最大的字体缩放倍数，支持undefined类型。<br/>取值范围：[1, +∞)<br/>**说明：** <br/>设置的值小于1时，按值为1处理。异常值默认不生效。<br/>使用前需在工程中配置configuration.json文件和app.json5文件，具体详见[示例17（设置最小字体范围与最大字体范围）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#示例17设置最小字体范围与最大字体范围)。 |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

设置文本最大显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[minFontSize](TextAreaAttribute#minFontSize)以及[maxLines](TextAreaAttribute#maxLines(value: number))或布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

maxFontSize小于等于0或者maxFontSize小于minFontSize时，自适应字号不生效，此时按照[fontSize](TextAreaAttribute#fontSize)属性的值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-maxFontSize(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-maxFontSize(value: number | string | Resource): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最大显示字号。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## maxLength

```TypeScript
maxLength(value: number)
```

设置文本的最大输入字符数。默认不设置最大输入字符数限制。到达文本最大字符限制，将无法继续输入字符。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-maxLength(value: number): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLength(value: number): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 文本的最大输入字符数。</br> 当value<0时，按照默认值处理，不设限制。<br>默认值：uint32_max，即2的32次方-1。 |

## maxLines

```TypeScript
maxLines(value: number)
```

配置textOverflow一起使用时，maxLines为可显示行数，超出截断；未配置textOverflow时，内联模式获焦状态下内容超出maxLines时，文本可滚动显示，内联模式非获焦状态下不生效maxLines，非内联模式按行截断。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-maxLines(value: number): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLines(value: number): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内联输入风格编辑态时文本可显示的最大行数。<br/>默认值：3，非内联模式下，默认值为UINT32_MAX。 <br/>取值范围：(0, UINT32_MAX] |

## maxLines

```TypeScript
maxLines(lines: number, options: MaxLinesOptions)
```

配置[textOverflow](TextAreaAttribute#textOverflow)一起使用时，maxLines为可显示行数，超出可配置为截断或滚动。未配置textOverflow时，内联模式获焦状态下内容超出maxLines时，文本可滚动显示。内联模式非获焦状态下，maxLines不生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-maxLines(lines: number, options: MaxLinesOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLines(lines: number, options: MaxLinesOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lines | number | 是 | 内联输入风格编辑态时文本可显示的最大行数。<br/>默认值：3，非内联模式下，默认值为+∞，不限制最大行数。 <br/>取值范围：(0, +∞) |
| options | [MaxLinesOptions](../arkts-apis/arkts-arkui-maxlinesoptions-i.md) | 是 | 文本超长时显示效果。<br/>默认值：MaxLinesMode.CLIP |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

设置文本最小的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-minFontScale(scale: Optional<number|Resource>): TextAreaAttribute--><!--Device-TextAreaAttribute-minFontScale(scale: Optional<number|Resource>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number\|Resource&gt; | 是 | 文本最小的字体缩放倍数，支持undefined类型。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。异常值默认不生效。<br/>使用前需在工程中配置configuration.json文件和app.json5文件，具体详见[示例17（设置最小字体范围与最大字体范围）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#示例17设置最小字体范围与最大字体范围)。 |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

设置文本最小显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[maxFontSize](TextAreaAttribute#maxFontSize)以及[maxLines](TextAreaAttribute#maxLines(value: number))或布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

minFontSize小于或等于0时，自适应字号不生效，此时按照[fontSize](TextAreaAttribute#fontSize)属性的值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-minFontSize(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-minFontSize(value: number | string | Resource): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最小显示字号。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## minLines

```TypeScript
minLines(lines: Optional<number>)
```

设置最小行数。组件的高度将根据lines自动调整，确保显示高度不低于lines对应的高度。如果设置了[constraintSize](arkts-arkui-commonmethod-c.md#constraintsize)，那么组件最后显示高度会在[constraintSize](arkts-arkui-commonmethod-c.md#constraintsize)约束内。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-minLines(lines: Optional<number>): TextAreaAttribute--><!--Device-TextAreaAttribute-minLines(lines: Optional<number>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lines | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 最小行数。</br>默认值：1</br>取值范围：[1, INT32_MAX]</br>如果lines的值小于1，取默认值。 |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

输入内容发生变化时，触发该回调。

在本回调中，若执行了光标操作，需要开发者在预上屏场景下依据[EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md)的previewText参数调整光标逻辑，以适应预上屏场景。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onChange(callback: EditableTextOnChangeCallback): TextAreaAttribute--><!--Device-TextAreaAttribute-onChange(callback: EditableTextOnChangeCallback): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) | 是 | 当前输入文本内容变化时的回调。<br>**起始版本：** 12 |

## onContentScroll

```TypeScript
onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void)
```

文本内容滚动时，触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (totalOffsetX: number, totalOffsetY: number) =&gt; void | 是 | 监听事件的回调函数。 |

## onCopy

```TypeScript
onCopy(callback: (value: string) => void)
```

进行复制操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onCopy(callback: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onCopy(callback: (value: string) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string) =&gt; void | 是 | 监听事件的回调函数。 |

## onCut

```TypeScript
onCut(callback: (value: string) => void)
```

进行复制操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onCut(callback: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onCut(callback: (value: string) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string) =&gt; void | 是 | 监听事件的回调函数。 |

## onDidDelete

```TypeScript
onDidDelete(callback: Callback<DeleteValue>)
```

在删除完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onDidDelete(callback: Callback<DeleteValue>): TextAreaAttribute--><!--Device-TextAreaAttribute-onDidDelete(callback: Callback<DeleteValue>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;DeleteValue&gt; | 是 | 在删除完成时调用的回调。<br/>仅支持系统输入法输入的场景。 |

## onDidInsert

```TypeScript
onDidInsert(callback: Callback<InsertValue>)
```

在输入完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onDidInsert(callback: Callback<InsertValue>): TextAreaAttribute--><!--Device-TextAreaAttribute-onDidInsert(callback: Callback<InsertValue>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;InsertValue&gt; | 是 | 在输入完成时调用的回调。<br/>仅支持系统输入法输入的场景。 |

## onEditChange

```TypeScript
onEditChange(callback: (isEditing: boolean) => void)
```

输入状态变化时，触发该回调。有光标时为编辑态，无光标时为非编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onEditChange(callback: (isEditing: boolean) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onEditChange(callback: (isEditing: boolean) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isEditing: boolean) =&gt; void | 是 | 监听事件的回调函数。 |

## onPaste

```TypeScript
onPaste(callback: (value: string, event: PasteEvent) => void)
```

进行粘贴操作时，触发该回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onPaste(callback: (value: string, event: PasteEvent) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onPaste(callback: (value: string, event: PasteEvent) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string, event: PasteEvent) =&gt; void | 是 | 监听事件的回调函数。 |

## onSubmit

```TypeScript
onSubmit(callback: (enterKey: EnterKeyType) => void)
```

按下软键盘输入法回车键时，触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (enterKey: EnterKeyType) =&gt; void | 是 | 监听事件的回调函数。 |

## onSubmit

```TypeScript
onSubmit(callback: TextAreaSubmitCallback)
```

按下软键盘输入法回车键触发该回调事件，提交事件时提供保持TextArea编辑状态的方法。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute--><!--Device-TextAreaAttribute-onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextAreaSubmitCallback](arkts-arkui-textareasubmitcallback-t.md) | 是 | 按下软键盘输入法回车键时的回调事件。 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void)
```

文本选择的位置或编辑状态下光标位置发生变化时，触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (selectionStart: number, selectionEnd: number) =&gt; void | 是 | 监听事件的回调函数。 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient> | undefined)
```

在输入框将要绑定输入法前触发该回调。

<!--Del-->

在输入框将要绑定输入法前，可以通过`UIContext`的系统接口[setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig)设置键盘的样式。&lt;!--DelEnd-  
-&gt;

从API version 22开始，调用[IMEClient](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#imeclient20对象说明)的[setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig)方法可以设置输入法扩展信息。在绑定输入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。

IMEClient仅在onWillAttachIME执行期间有效，不可进行异步调用。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;IMEClient&gt; \| undefined | 是 | 在输入框将要绑定输入法前触发该回调。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

在文本内容将要发生变化时，触发该回调。

onWillChange的回调时序晚于onWillInsert、onWillDelete，早于onDidInsert、onDidDelete。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;EditableTextChangeValue, boolean&gt; | 是 | 在文本内容将要发生变化时的回调。<br/>返回true时，表示正常修改。返回false时，表示拦截此次触发。 |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

在进行复制操作前，触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillCopy(callback: Callback<string, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillCopy(callback: Callback<string, boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string, boolean&gt; | 是 | 复制操作前的回调。回调参数类型为string时，表示将要被复制的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被复制，true：允许文本被复制；false：不允许文本被复制。 |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

在进行剪切操作前，触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillCut(callback: Callback<string, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillCut(callback: Callback<string, boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string, boolean&gt; | 是 | 剪切操作前的回调。回调参数类型为string时，表示将要被剪切的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被剪切，true：允许文本被剪切；false：不允许文本被剪切。 |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

在将要删除时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;DeleteValue, boolean&gt; | 是 | 在将要删除时调用的回调。<br/>在返回true时，表示正常删除，返回false时，表示不删除。<br/>在预上屏删除操作时，该回调不触发。<br/>仅支持系统输入法输入的场景。 |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

在将要输入时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;InsertValue, boolean&gt; | 是 | 在将要输入时调用的回调。<br/>在返回true时，表示正常插入，返回false时，表示不插入。<br/>在预上屏和候选词操作时，该回调不触发。<br/>仅支持系统输入法输入的场景。 |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

设置文本排版时是否使能孤字优化。不通过该接口设置，默认不使能孤字优化。

孤字优化通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[wordBreak](TextAreaAttribute#wordBreak)为非BREAK_ALL并且待排版文本首个[TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)的[locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)为“zh-Hans”或“zh-Hant”时生效。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 段落最后一行是否使能孤字优化。<br/>true表示使能孤字优化，false表示不使能孤字优化。<br/>值为undefined或null时，不使能孤字优化。 |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

设置placeholder文本颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-placeholderColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-placeholderColor(value: ResourceColor): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | placeholder文本颜色。<br/>默认值：跟随主题。 |

## placeholderFont

```TypeScript
placeholderFont(value: Font)
```

设置placeholder文本样式，包括字体大小、字体粗细、字体族、字体风格。
> **说明：**  
>  
> 可以使用[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)注册自定义字体。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-placeholderFont(value: Font): TextAreaAttribute--><!--Device-TextAreaAttribute-placeholderFont(value: Font): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | placeholder文本样式。 |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

是否启用行尾标点溢出。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启，默认为false |

## scrollBarColor

```TypeScript
scrollBarColor(thumbColor: ColorMetrics | undefined)
```

设置滚动条的颜色。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-scrollBarColor(thumbColor: ColorMetrics | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-scrollBarColor(thumbColor: ColorMetrics | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| thumbColor | [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md) \| undefined | 是 | 滚动条的颜色。<br />默认值：'#66182431'，显示为灰色。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-selectedBackgroundColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-selectedBackgroundColor(value: ResourceColor): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本选中底板颜色。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置多行文本输入框内文本拖拽时的背板样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) \| undefined | 是 | 文本拖拽时的背板样式。<br/>设置为undefined时：背板颜色跟随主题，浅色模式显示白色，深色模式显示黑色。 |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

设置是否不弹出系统文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-selectionMenuHidden(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-selectionMenuHidden(value: boolean): TextAreaAttribute-End-->

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
> 当同时设置shaderStyle和[strokeWidth](TextAreaAttribute#strokeWidth)时，shaderStyle不生效。  
>  
> shaderStyle的优先级高于[fontColor](TextAreaAttribute#fontColor)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-shaderStyle(shader: ShaderStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-shaderStyle(shader: ShaderStyle | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) \| undefined | 是 | 文本着色器效果。<br/>值为undefined时，无渐变效果。 |

## showCounter

```TypeScript
showCounter(value: boolean, options?: InputCounterOptions)
```

设置当通过InputCounterOptions输入的字符数超过阈值时显示计数器。未调用showCounter接口时，默认不显示计数器。

参数value为true时，才能设置options，文本框开启计数器功能，需要配合maxLength（设置最大字符限制）一起使用。字符计数器显示的效果是当前输入字符数/最大可输入字符数。

当输入字符数大于最大字符数乘百分比值时，显示字符计数器。如果用户设置计数器时不设置InputCounterOptions，那么当前输入字符数达到最大字符数时，边框和计数器下标将变为红色。用户同时设置参数value为true和InputCounterOptions，当thresholdPercentage数值在有效区间内，且输入字符数超过最大字符数时，边框和计数器下标将变为红色，框体抖动。highlightBorder设置为false，则不显示红色边框，计数器默认显示红色边框。内联模式下字符计数器不显示。

[示例2（设置计数器）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#示例2设置计数器)展示了设置showCounter的效果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示计数器。<br/>true表示显示计数器，false表示不显示。 |
| options | [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | 否 | 计数器的配置项。<br>**起始版本：** 11 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键传递。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-stopBackPress(isStopped: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-stopBackPress(isStopped: Optional<boolean>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否阻止返回键。<br/>true表示阻止，false表示不阻止。<br/>默认值：true。异常值取默认值。 |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

设置文本描边的颜色。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-strokeColor(color: Optional<ResourceColor>): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeColor(color: Optional<ResourceColor>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 描边颜色。默认值为字体颜色，设置异常值时取默认值。 |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

设置文本描边拐角样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) \| undefined | 是 | 文本描边拐角样式。<br/>值为undefined时，按照StrokeJoinStyle.MITER_JOIN处理，请参考[StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md)，文本拐角处表现为锐角。 |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

设置文本描边的宽度。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 文本描边的宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。<br/>若设置值小于0，显示实心字；若大于0，显示空心字。<br/>默认值为0，不做描边处理。 |

## style

```TypeScript
style(value: TextContentStyle)
```

设置文本框多态样式，内联输入风格只支持TextAreaType.NORMAL类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-style(value: TextContentStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-style(value: TextContentStyle): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextContentStyle](../arkts-apis/arkts-arkui-textcontentstyle-e.md) | 是 | 文本框多态样式。<br/>默认值：TextContentStyle.DEFAULT |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

设置文本在输入框中的水平对齐方式。

支持TextAlign.Start、TextAlign.Center和TextAlign.End。从API version 11开始，新增TextAlign.JUSTIFY选项。

可通过[align](arkts-arkui-commonmethod-c.md#align)属性控制文本段落在垂直方向上的位置，此组件中不可通过align属性控制文本段落在水平方向上的位置。

- Alignment.TopStart、Alignment.Top、Alignment.TopEnd：内容顶部对齐。  
- Alignment.Start、Alignment.Center、Alignment.End：内容垂直居中。  
- Alignment.BottomStart、Alignment.Bottom、Alignment.BottomEnd：内容底部对齐。

当textAlign属性设置为TextAlign.JUSTIFY时，最后一行文本不参与两端对齐，为水平对齐首部效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-textAlign(value: TextAlign): TextAreaAttribute--><!--Device-TextAreaAttribute-textAlign(value: TextAlign): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextAlign](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textalign-e.md) | 是 | 文本在输入框中的水平对齐方式。<br/>默认值：TextAlign.Start |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

指定文本排版方向，未通过该接口设置时，默认文本排版方向遵循组件布局方向。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-textDirection(direction: TextDirection | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-textDirection(direction: TextDirection | undefined): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [TextDirection](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textdirection-e.md) \| undefined | 是 | 文本排版方向。<br/>设置为undefined时，按照TextDirection.DEFAULT处理，表现为文本排版方向遵循组件布局方向。 |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

设置首行文本缩进。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-textIndent(value: Dimension): TextAreaAttribute--><!--Device-TextAreaAttribute-textIndent(value: Dimension): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 首行文本缩进。<br/>默认值：0 <br/>单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) <br/>取值范围：大于等于0。设置负数时，按默认值处理。 |

## textOverflow

```TypeScript
textOverflow(value: TextOverflow)
```

设置文本超长时的显示方式。

内联模式，主动配置textOverflow才会生效按[maxLines](TextAreaAttribute#maxLines(value: number))截断效果，不配置时，默认不截断。

文本截断是按字截断。例如，英文以单词为最小单位进行截断，若需要以字母为单位进行截断，[wordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md)属性可设置为WordBreak.BREAK_ALL。

当textOverflow设置为TextOverflow.None、TextOverflow.Clip、TextOverflow.Ellipsis时，需配合[maxLines](TextAreaAttribute#maxLines(value: number))使用，单独设置不生效。设置TextOverflow.None与TextOverflow.Clip效果一样。
> **说明：**  
>  
> TextArea组件不支持设置TextOverflow.MARQUEE模式，当设置为TextOverflow.MARQUEE模式时，显示为TextOverflow.Clip。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-textOverflow(value: TextOverflow): TextAreaAttribute--><!--Device-TextAreaAttribute-textOverflow(value: TextOverflow): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md) | 是 | 文本超长时的显示方式。<br/>默认值：TextOverflow.Clip |

## type

```TypeScript
type(value: TextAreaType)
```

设置输入框类型。

不同的TextAreaType会拉起对应类型的键盘，同时限制输入。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-type(value: TextAreaType): TextAreaAttribute--><!--Device-TextAreaAttribute-type(value: TextAreaType): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextAreaType](arkts-arkui-textareatype-e.md) | 是 | 输入框类型。<br/>默认值：TextAreaType.NORMAL |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

设置文本断行规则。该属性对placeholder文本无效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaAttribute-wordBreak(value: WordBreak): TextAreaAttribute--><!--Device-TextAreaAttribute-wordBreak(value: WordBreak): TextAreaAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [WordBreak](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-wordbreak-e.md) | 是 | 文本断行规则。 <br />默认值：WordBreak.BREAK_WORD |

