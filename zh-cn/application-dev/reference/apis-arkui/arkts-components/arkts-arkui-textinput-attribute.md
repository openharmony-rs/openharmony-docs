# TextInput属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** TextInputAttribute extends [CommonMethod<TextInputAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class TextInputAttribute extends CommonMethod<TextInputAttribute>--><!--Device-unnamed-declare class TextInputAttribute extends CommonMethod<TextInputAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

设置自动大小写模式的文本模式，只提供接口能力，具体实现以输入法应用为主。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextInputAttribute--><!--Device-TextInputAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | 是 | 自动大小写模式，默认状态无效。 |

## barState

```TypeScript
barState(value: BarState)
```

设置内联输入风格编辑态时滚动条的显示模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-barState(value: BarState): TextInputAttribute--><!--Device-TextInputAttribute-barState(value: BarState): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 内联输入风格编辑态时滚动条的显示模式。<br/>默认值：BarState.Auto |

## cancelButton

```TypeScript
cancelButton(options: CancelButtonOptions)
```

设置右侧清除按钮样式，仅支持图片类型的图标。不支持[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)。示例请参考[示例4（设置右侧清除按钮样式）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例4设置右侧清除按钮样式)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-cancelButton(options: CancelButtonOptions): TextInputAttribute--><!--Device-TextInputAttribute-cancelButton(options: CancelButtonOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) | 是 | 右侧清除按钮样式选项。<br />默认值：<br />{<br />style: CancelButtonStyle.INPUT<br />}<br/>Wearable设备上默认值为：28vp<br>**起始版本：** 18 |

## cancelButton

```TypeScript
cancelButton(symbolOptions: CancelButtonSymbolOptions)
```

设置右侧清除按钮样式，仅支持symbol图标。不支持[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)。示例请参考[示例15（设置symbol类型清除按钮）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例15设置symbol类型清除按钮)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-cancelButton(symbolOptions: CancelButtonSymbolOptions): TextInputAttribute--><!--Device-TextInputAttribute-cancelButton(symbolOptions: CancelButtonSymbolOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbolOptions | [CancelButtonSymbolOptions](arkts-arkui-cancelbuttonsymboloptions-i.md) | 是 | 右侧清除按钮样式。<br />默认值：<br />{<br />style: CancelButtonStyle.INPUT<br />} |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

设置输入框光标颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-caretColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-caretColor(value: ResourceColor): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入框光标颜色。<br/>默认值：'#007DFF' |

## caretPosition

```TypeScript
caretPosition(value: number)
```

设置光标位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-caretPosition(value: number): TextInputAttribute--><!--Device-TextInputAttribute-caretPosition(value: number): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 光标的位置。<br/>第一个字符前的位置是0。 |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

设置光标风格。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-caretStyle(value: CaretStyle): TextInputAttribute--><!--Device-TextInputAttribute-caretStyle(value: CaretStyle): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启行首标点符号压缩。<br/>true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## contentType

```TypeScript
contentType(value: ContentType)
```

设置自动填充类型。<!--RP7--><!--RP7End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-contentType(value: ContentType): TextInputAttribute--><!--Device-TextInputAttribute-contentType(value: ContentType): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ContentType](../../apis-audio-kit/arkts-apis/arkts-audio-audio-contenttype-e.md) | 是 | 自动填充类型。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置输入的文本是否可复制。设置CopyOptions.None时，只支持粘贴和全选。

设置CopyOptions.None时，不允许拖拽。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-copyOption(value: CopyOptions): TextInputAttribute--><!--Device-TextInputAttribute-copyOption(value: CopyOptions): TextInputAttribute-End-->

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

自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认值。

自定义键盘采用覆盖原始界面的方式呈现，当没有开启避让模式或者输入框不需要避让的场景不会对应用原始界面产生压缩或者上提。

自定义键盘无法获取焦点，但是会拦截手势事件。

默认在输入控件失去焦点时，关闭自定义键盘，开发者也可以通过[TextInputController](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#textinputcontroller8).[stopEditing](arkts-arkui-textinputcontroller-c.md#stopediting)方法控制键盘关闭。

当设置自定义键盘时，可以通过绑定[onKeyPreIme](arkts-arkui-commonmethod-c.md#onkeypreime)事件规避物理键盘的输入。

从API version 23开始，自定义键盘可以通过[setCustomKeyboardContinueFeature](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#setcustomkeyboardcontinuefeature23)开启接续，在切换至其他自定义键盘时，会直接切换，不会触发键盘关闭和拉起动画。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextInputAttribute--><!--Device-TextInputAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-decoration(value: TextDecorationOptions): TextInputAttribute--><!--Device-TextInputAttribute-decoration(value: TextDecorationOptions): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute--><!--Device-TextInputAttribute-editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | 是 | 扩展菜单选项。 |

## ellipsisMode

```TypeScript
ellipsisMode(mode: Optional<EllipsisMode>)
```

设置省略位置。ellipsisMode属性仅在[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)下生效，需要配合overflow设置为TextOverflow.Ellipsis使用，单独设置ellipsisMode属性不生效。

非编辑态时正常生效，编辑态时EllipsisMode.START和EllipsisMode.CENTER仅在maxLines设置为1时生效，EllipsisMode.END、EllipsisMode.MULTILINE_START和EllipsisMode.MULTILINE_CENTER正常生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextInputAttribute--><!--Device-TextInputAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;EllipsisMode&gt; | 是 | 省略位置。 <br />默认值：EllipsisMode.END |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

设置是否启用自动填充。<!--RP6--><!--RP6End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enableAutoFill(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoFill(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用自动填充。<br/>true表示启用，false表示不启用。<br/>默认值：true |

## enableAutoFillAnimation

```TypeScript
enableAutoFillAnimation(enabled: Optional<boolean>)
```

设置是否启用自动填充动效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enableAutoFillAnimation(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoFillAnimation(enabled: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用自动填充动效。<br/>true表示启用，false表示不启用。<br/>默认值：true <br/>**说明：**<br/>启用之后，仅输入模式[InputType](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#inputtype枚举说明)设置为Password、NEW_PASSWORD或NUMBER_PASSWORD的输入框在进行自动填充时动效可生效。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-enableHapticFeedback(isEnabled: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableHapticFeedback(isEnabled: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否开启触控反馈。<br/>true表示开启触控反馈，false表示不开启触控反馈。<br/>默认值：true |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

设置TextInput通过点击以外的方式获焦时，是否主动拉起软键盘。

从API version 10开始，获焦默认绑定输入法。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enableKeyboardOnFocus(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableKeyboardOnFocus(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 通过点击以外的方式获焦时，是否主动拉起软键盘。<br/>true表示主动拉起软键盘，false表示不主动拉起。<br/>默认值：TV设备为false，其他设备为true。 |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启输入预上屏。

预上屏内容定义为文字暂存态，目前不支持文字拦截功能。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enablePreviewText(enable: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enablePreviewText(enable: boolean): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextInputAttribute--><!--Device-TextInputAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextInputAttribute-End-->

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

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-enterKeyType(value: EnterKeyType): TextInputAttribute--><!--Device-TextInputAttribute-enterKeyType(value: EnterKeyType): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-enterkeytype-e.md) | 是 | 输入法回车键类型。<br/>默认值：EnterKeyType.Done |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。不通过该接口设置，默认行高不基于文字实际高度自适应。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-fontColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-fontColor(value: ResourceColor): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。<br/>Wearable设备上默认值为：'#dbffffff' |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

设置字体列表。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-fontFamily(value: ResourceStr): TextInputAttribute--><!--Device-TextInputAttribute-fontFamily(value: ResourceStr): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 字体列表。默认字体'HarmonyOS Sans'。<br>使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。<br>应用当前支持'HarmonyOS Sans'字体和自定义字体。<br>卡片当前仅支持'HarmonyOS Sans'字体。 |

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

<!--Device-TextInputAttribute-fontFeature(value: string): TextInputAttribute--><!--Device-TextInputAttribute-fontFeature(value: string): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-fontSize(value: Length): TextInputAttribute--><!--Device-TextInputAttribute-fontSize(value: Length): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。fontSize为number类型时，使用fp单位。字体默认大小16fp。不支持设置百分比字符串。<br/>Wearable设备上默认值为：18fp |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-fontStyle(value: FontStyle): TextInputAttribute--><!--Device-TextInputAttribute-fontStyle(value: FontStyle): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextInputAttribute--><!--Device-TextInputAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-halfLeading(halfLeading: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-halfLeading(halfLeading: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置文本是否垂直居中。<br/>true表示将行间距平分至行的顶部与底部，false则不平分。<br/>默认值：false |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

组件设置为内联输入风格时，设置文本自适应高度的方式。

当设置为TextHeightAdaptivePolicy.MAX_LINES_FIRST时，优先使用[maxLines](TextInputAttribute#maxLines)属性来调整文本高度。如果使用maxLines属性的布局大小超过了布局约束，则尝试在[minFontSize](TextInputAttribute#minFontSize)和[maxFontSize](TextInputAttribute#maxFontSize)的范围内缩小字体以显示更多文本。

当设置为TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST时，优先使用minFontSize属性来调整文本高度。如果使用minFontSize属性可以将文本布局在一行中，则尝试在minFontSize和maxFontSize的范围内增大字体并使用最大限度的字体大小。

当设置为TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST时，与TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST效果一样。

组件设置为非内联输入风格时，设置文本自适应高度(TextHeightAdaptivePolicy)的三种方式效果一样，即在minFontSize和maxFontSize的范围内缩小字体以显示更多文本。
> **说明：**  
>  
> 组件设置为内联输入风格，编辑态与非编辑态存在字体大小不一致情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute--><!--Device-TextInputAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | 是 | 文本自适应高度的方式。<br/>默认值：TextHeightAdaptivePolicy.MAX_LINES_FIRST |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-includeFontPadding(include: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-includeFontPadding(include: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否在首行和尾行增加间距以避免文字截断。<br/>true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。

单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。

从API version 11开始，设置inputFilter且输入的字符不为空字符，会导致[type](TextInputAttribute#type)接口附带的文本过滤效果失效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 正则表达式。 |
| error | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 正则匹配失败时，返回被过滤的内容。<br>**起始版本：** 18 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置输入框拉起的键盘样式，需要输入法适配后生效。具体参考[输入法应用沉浸模式](../../../inputmethod/inputmethod-immersive-mode-guide.md)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextInputAttribute--><!--Device-TextInputAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-optional-t.md)&lt;KeyboardAppearance&gt; | 是 | 键盘样式。<br/>默认值：KeyboardAppearance.NONE_IMMERSIVE |

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

<!--Device-TextInputAttribute-letterSpacing(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-letterSpacing(value: number | string | Resource): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本字符间距。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

设置折行规则。该属性在wordBreak不等于breakAll的时候生效，不支持连词符。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute--><!--Device-TextInputAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | 是 | 文本的折行规则。 <br />默认值：LineBreakStrategy.GREEDY <br/>**说明：**<br/>仅设置[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)时该属性生效。 |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

设置文本的行高。

设置值不大于0时，不限制文本行高，自适应字体大小，number类型时单位为fp。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。
> **说明：**  
>  
> - 特殊字符字体高度远超出同行的其他字符高度时，文本框出现截断、遮挡、内容相对位置发生变化等不符合预期的显示异常，需要开发者调整组件高度、行高等属性，修改对应的页面布局。  
>  
> - 设置[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)时，通过该接口设置行高  
> [lineHeight](TextInputAttribute#lineHeight)不生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-lineHeight(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-lineHeight(value: number | string | Resource): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-maxFontScale(scale: Optional<number|Resource>): TextInputAttribute--><!--Device-TextInputAttribute-maxFontScale(scale: Optional<number|Resource>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number\|Resource&gt; | 是 | 文本最大的字体缩放倍数，支持undefined类型。<br/>取值范围：[1, +∞)<br/>**说明：** <br/>设置的值小于1时，按值为1处理。异常值默认不生效。<br/>当设置maxFontScale属性后，showError最多放大到2倍。<br/>使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和[app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见[示例18（设置最小字体范围与最大字体范围）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例18设置最小字体范围与最大字体范围)。 |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

设置文本最大显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[minFontSize](TextInputAttribute#minFontSize)以及[maxLines](TextInputAttribute#maxLines)(组件设置为内联输入风格且编辑态时使用)或布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

maxFontSize小于等于0或者maxFontSize小于minFontSize时，自适应字号不生效，此时按照[fontSize](TextInputAttribute#fontSize)属性的值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-maxFontSize(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-maxFontSize(value: number | string | Resource): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最大显示字号。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## maxLength

```TypeScript
maxLength(value: number)
```

设置文本的最大输入字符数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-maxLength(value: number): TextInputAttribute--><!--Device-TextInputAttribute-maxLength(value: number): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 文本的最大输入字符数。<br/>默认值：Infinity，可以无限输入。<br/>**说明：** <br/>当不设置该属性或设置异常值时，取默认值，设置小数时，取整数部分，设置值超过2^31-1时，可能导致异常行为。 |

## maxLines

```TypeScript
maxLines(value: number)
```

设置内联输入风格编辑态时文本可显示的最大行数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-maxLines(value: number): TextInputAttribute--><!--Device-TextInputAttribute-maxLines(value: number): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内联输入风格编辑态时文本可显示的最大行数。<br/>默认值：3 <br/>取值范围：(0, UINT32_MAX] |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

设置文本最小的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-minFontScale(scale: Optional<number|Resource>): TextInputAttribute--><!--Device-TextInputAttribute-minFontScale(scale: Optional<number|Resource>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number\|Resource&gt; | 是 | 文本最小的字体缩放倍数，支持undefined类型。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。异常值默认不生效。<br/>使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和[app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见[示例18（设置最小字体范围与最大字体范围）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例18设置最小字体范围与最大字体范围)。 |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

设置文本最小显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

需配合[maxFontSize](TextInputAttribute#maxFontSize)以及[maxLines](TextInputAttribute#maxLines)(组件设置为内联输入风格且编辑态时使用)或布局大小限制使用，单独设置不生效。

自适应字号生效时，fontSize设置不生效。

minFontSize小于或等于0时，自适应字号不生效，此时按照[fontSize](TextInputAttribute#fontSize)属性的值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-minFontSize(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-minFontSize(value: number | string | Resource): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最小显示字号。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

输入内容发生变化时，触发该回调。

在本回调中，若执行了光标操作，需要开发者在预上屏场景下依据previewText参数调整光标逻辑，以适应预上屏场景。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onChange(callback: EditableTextOnChangeCallback): TextInputAttribute--><!--Device-TextInputAttribute-onChange(callback: EditableTextOnChangeCallback): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onContentScroll(callback: OnContentScrollCallback): TextInputAttribute--><!--Device-TextInputAttribute-onContentScroll(callback: OnContentScrollCallback): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onCopy(callback: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-onCopy(callback: Callback<string>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 复制回调，其返回值为复制的文本内容。<br>**起始版本：** 18 |

## onCut

```TypeScript
onCut(callback: Callback<string>)
```

进行剪切操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onCut(callback: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-onCut(callback: Callback<string>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 剪切回调，其返回值为剪切的文本内容。<br>**起始版本：** 18 |

## onDidDelete

```TypeScript
onDidDelete(callback: Callback<DeleteValue>)
```

在删除完成时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onDidDelete(callback: Callback<DeleteValue>): TextInputAttribute--><!--Device-TextInputAttribute-onDidDelete(callback: Callback<DeleteValue>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onDidInsert(callback: Callback<InsertValue>): TextInputAttribute--><!--Device-TextInputAttribute-onDidInsert(callback: Callback<InsertValue>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;InsertValue&gt; | 是 | 在输入完成时调用的回调。<br/>仅支持系统输入法输入的场景。 |

## onEditChange

```TypeScript
onEditChange(callback: Callback<boolean>)
```

输入状态变化时，触发该回调。有光标时为编辑态，无光标时为非编辑态。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onEditChange(callback: Callback<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onEditChange(callback: Callback<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 输入状态变化回调，返回值为true表示输入框处于编辑态，返回值为false表示输入框处于非编辑态。<br>**起始版本：** 18 |

## onEditChanged

```TypeScript
onEditChanged(callback: (isEditing: boolean) => void)
```

输入状态变化时，触发该回调。
> **说明：**  
>  
> 从API version 7开始支持，从API version 8开始废弃，建议使用[onEditChange](TextInputAttribute#onEditChange)替代。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** onEditChange

<!--Device-TextInputAttribute-onEditChanged(callback: (isEditing: boolean) => void): TextInputAttribute--><!--Device-TextInputAttribute-onEditChanged(callback: (isEditing: boolean) => void): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isEditing: boolean) =&gt; void | 是 | 监听事件的回调函数。 |

## onPaste

```TypeScript
onPaste(callback: OnPasteCallback)
```

进行粘贴操作时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onPaste(callback: OnPasteCallback): TextInputAttribute--><!--Device-TextInputAttribute-onPaste(callback: OnPasteCallback): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 是 | Executed when a paste operation is performed.<br>**起始版本：** 18 |

## onSecurityStateChange

```TypeScript
onSecurityStateChange(callback: Callback<boolean>)
```

密码显隐状态切换时，触发该回调。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onSecurityStateChange(callback: Callback<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onSecurityStateChange(callback: Callback<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。<br/>true表示状态切换；false表示状态未切换。 |

## onSubmit

```TypeScript
onSubmit(callback: OnSubmitCallback)
```

按下输入法回车键触发该回调。

非TV设备按下回车键时输入框默认会失焦且收起键盘，可在OnSubmitCallback回调中配置是否收起键盘，参考[示例2（设置下划线）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例2设置下划线)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onSubmit(callback: OnSubmitCallback): TextInputAttribute--><!--Device-TextInputAttribute-onSubmit(callback: OnSubmitCallback): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSubmitCallback](arkts-arkui-onsubmitcallback-t.md) | 是 | 提交回调。<br>**起始版本：** 18 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: OnTextSelectionChangeCallback)
```

文本选择的位置或编辑状态下光标位置发生变化时，触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): TextInputAttribute--><!--Device-TextInputAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 是 | 文本选择变化回调或光标位置变化回调。<br>**起始版本：** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

在输入框将要绑定输入法前触发该回调。

<!--Del-->

在输入框将要绑定输入法前，可以通过`UIContext`的系统接口[setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig)设置键盘的样式。&lt;!--DelEnd-  
-&gt;

从API version 22开始，调用[IMEClient](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#imeclient20对象说明)的[setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig)方法可以设置输入法扩展信息。在绑定输入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。

IMEClient仅在onWillAttachIME执行期间有效，不可进行异步调用。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onWillAttachIME(callback: Callback<IMEClient>): TextInputAttribute--><!--Device-TextInputAttribute-onWillAttachIME(callback: Callback<IMEClient>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;IMEClient&gt; | 是 | 在输入框将要绑定输入法前触发该回调。 |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

在文本内容将要发生变化时，触发该回调。

onWillChange的回调时序晚于onWillInsert、onWillDelete，早于onDidInsert、onDidDelete。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onWillCopy(callback: Callback<string, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillCopy(callback: Callback<string, boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onWillCut(callback: Callback<string, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillCut(callback: Callback<string, boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextInputAttribute-End-->

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

孤字优化通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[wordBreak](TextInputAttribute#wordBreak)为非BREAK_ALL并且待排版文本首个[TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)的[locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)为“zh-Hans”或“zh-Hant”时生效。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 段落最后一行是否使能孤字优化。<br/>true表示使能孤字优化，false表示不使能孤字优化。<br/>值为undefined或null时，不使能孤字优化。 |

## passwordIcon

```TypeScript
passwordIcon(value: PasswordIcon)
```

设置当密码输入模式时，输入框末尾的图标。

支持jpg、png、bmp、heic和webp类型的图片格式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-passwordIcon(value: PasswordIcon): TextInputAttribute--><!--Device-TextInputAttribute-passwordIcon(value: PasswordIcon): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PasswordIcon](arkts-arkui-passwordicon-i.md) | 是 | 密码输入模式时，输入框末尾的图标。<br/>默认为系统提供的密码图标。<br/>该图标的固定尺寸为24vp，Wearable设备上默认值为28vp，若引用的图标过大或过小，均显示为固定尺寸。 |

## passwordRules

```TypeScript
passwordRules(value: string)
```

定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。<!--RP1--><!--RP1End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-passwordRules(value: string): TextInputAttribute--><!--Device-TextInputAttribute-passwordRules(value: string): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 定义生成密码的规则。 |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

设置placeholder文本颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-placeholderColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-placeholderColor(value: ResourceColor): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | placeholder文本颜色。<br/>默认值：跟随主题。<br/>Wearable设备上默认值为：'#99ffffff' |

## placeholderFont

```TypeScript
placeholderFont(value?: Font)
```

设置placeholder文本样式，包括字体大小、字体粗细、字体族、字体风格。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-placeholderFont(value?: Font): TextInputAttribute--><!--Device-TextInputAttribute-placeholderFont(value?: Font): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 否 | placeholder文本样式。<br/>Wearable设备上默认值为：18fp |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

是否启用行尾标点溢出。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-punctuationOverflow(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-punctuationOverflow(enabled: Optional<boolean>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启，默认为false |

## selectAll

```TypeScript
selectAll(value: boolean)
```

设置初始状态时，是否全选文本。不支持[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-selectAll(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-selectAll(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全选文本。<br/>true表示会全选文本，false表示不会全选文本。<br />默认值：false |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-selectedBackgroundColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-selectedBackgroundColor(value: ResourceColor): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本选中底板颜色。 |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

设置文本输入框内文本拖拽时的背板样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) \| undefined | 是 | 文本拖拽时的背板样式。<br/>设置为undefined时：背板颜色跟随主题，浅色模式显示白色，深色模式显示黑色。 |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

设置是否隐藏系统文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-selectionMenuHidden(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-selectionMenuHidden(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏系统文本选择菜单。<br />设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。<br />设置为false时，显示系统文本选择菜单。<br />默认值：false |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

设置文本着色器效果，如线性渐变、径向渐变效果等。
> **说明：**  
>  
> 当同时设置shaderStyle和[strokeWidth](TextInputAttribute#strokeWidth)时，shaderStyle不生效。  
>  
> shaderStyle的优先级高于[fontColor](TextInputAttribute#fontColor)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-shaderStyle(shader: ShaderStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-shaderStyle(shader: ShaderStyle | undefined): TextInputAttribute-End-->

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

参数value为true时，才能设置options，文本框开启计数下标功能，需要配合[maxLength](TextInputAttribute#maxLength)（设置最大字符限制）一起使用。字符计数器显示的效果是当前输入字符数/最大可输入字符数。

当输入字符数大于最大字符数乘百分比值时，显示字符计数器。如果用户设置计数器时不设置InputCounterOptions，那么当前输入字符数超过最大字符数时，边框和计数器下标将变为红色。用户同时设置参数value为true和[InputCounterOptions](arkts-arkui-inputcounteroptions-i.md)，当thresholdPercentage数值在有效区间内，且输入字符数超过最大字符数时，边框和计数器下标将变为红色，框体抖动。highlightBorder设置为false，则不显示红色边框，计数器默认显示红色，框体抖动。

[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)、[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)下字符计数器不显示。

[示例5（设置计数器）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例5设置计数器)展示了设置showCounter的效果。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextInputAttribute--><!--Device-TextInputAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示计数器。<br/>true表示显示计数器，false表示不显示。 |
| options | [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | 否 | 计数器的配置项。 |

## showError

```TypeScript
showError(value?: ResourceStr | undefined)
```

设置错误状态下提示的错误文本或者不显示错误状态。

当参数类型为ResourceStr并且输入内容不符合定义规范时，提示错误文本，当提示错误单行文本超长时，末尾以省略号显示。当参数类型为undefined时，不显示错误状态。请参考[示例2](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例2设置下划线)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showError(value?: ResourceStr | undefined): TextInputAttribute--><!--Device-TextInputAttribute-showError(value?: ResourceStr | undefined): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined | 否 | 错误状态下提示的错误文本或者不显示错误状态。<br/>默认不显示错误状态。<br/>Wearable设备上字体大小为：13fp，对齐方式为：居中对齐<br/>**说明：** <br/>从API version 12开始，value支持Resource类型。<br>**起始版本：** 12 |

## showPassword

```TypeScript
showPassword(visible: boolean)
```

设置密码的显隐状态。

当[InputType](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#inputtype枚举说明)设置为Password、NEW_PASSWORD和NUMBER_PASSWORD模式时，密码保护功能才能生效。非密码输入模式则不会触发该功能。

[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)时，由于输入框后端的状态和前端应用侧的状态管理变量会不一致，可能导致末尾图标的状态异常。建议在[onSecurityStateChange](TextInputAttribute#onSecurityStateChange)上增加状态同步。参考[示例1（设置与获取光标位置）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#示例1设置与获取光标位置)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showPassword(visible: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showPassword(visible: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 是否显示密码。<br/>true表示会显示密码，false表示不会显示密码。<br/>默认值：false |

## showPasswordIcon

```TypeScript
showPasswordIcon(value: boolean)
```

设置当密码输入模式时，输入框末尾的图标是否显示。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showPasswordIcon(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showPasswordIcon(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 密码输入模式时，输入框末尾的图标是否显示。<br/>true表示显示，false表示不显示。<br/>默认值：TV设备为false，其他设备为true。 |

## showUnderline

```TypeScript
showUnderline(value: boolean)
```

设置是否开启下划线。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showUnderline(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showUnderline(value: boolean): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启下划线。<br/>true表示开启，false表示不开启。<br/>默认值：false<br/>下划线默认颜色为'#33182431'，默认粗细为1px，文本框尺寸48vp，下划线只支持InputType.Normal类型。 |

## showUnit

```TypeScript
showUnit(value: CustomBuilder)
```

设置控件作为文本框单位。需搭配[showUnderline](TextInputAttribute#showUnderline)使用，当showUnderline为true时生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-showUnit(value: CustomBuilder): TextInputAttribute--><!--Device-TextInputAttribute-showUnit(value: CustomBuilder): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 文本输入时，文本框的显示单位。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键传递。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-stopBackPress(isStopped: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-stopBackPress(isStopped: Optional<boolean>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-strokeColor(color: Optional<ResourceColor>): TextInputAttribute--><!--Device-TextInputAttribute-strokeColor(color: Optional<ResourceColor>): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-strokeWidth(width: Optional<LengthMetrics>): TextInputAttribute--><!--Device-TextInputAttribute-strokeWidth(width: Optional<LengthMetrics>): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 文本描边的宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。<br/>若设置值小于0，显示实心字；若大于0，显示空心字。<br/>默认值为0，不做描边处理。 |

## style

```TypeScript
style(value: TextInputStyle | TextContentStyle)
```

设置输入框为默认风格或内联输入风格，内联输入风格只支持InputType.Normal类型。

输入框类型介绍请参考[type](TextInputAttribute#type)接口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-style(value: TextInputStyle | TextContentStyle): TextInputAttribute--><!--Device-TextInputAttribute-style(value: TextInputStyle | TextContentStyle): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextInputStyle](arkts-arkui-textinputstyle-e.md) \| TextContentStyle | 是 | 输入框为默认风格或内联输入风格。<br/>默认值：TextInputStyle.Default |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

设置文本在输入框中的水平对齐方式。

支持TextAlign.Start、TextAlign.Center和TextAlign.End。TextAlign.JUSTIFY的对齐方式按照TextAlign.Start处理。

可通过[align](arkts-arkui-commonmethod-c.md#align)属性控制文本段落在垂直方向上的位置。此组件中不可使用align属性控制文本段落在水平方向上的位置。

- Alignment.TopStart、Alignment.Top、Alignment.TopEnd：内容顶部对齐。  
- Alignment.Start、Alignment.Center、Alignment.End：内容垂直居中。  
- Alignment.BottomStart、Alignment.Bottom、Alignment.BottomEnd：内容底部对齐。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-textAlign(value: TextAlign): TextInputAttribute--><!--Device-TextInputAttribute-textAlign(value: TextAlign): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-textDirection(direction: TextDirection | undefined): TextInputAttribute--><!--Device-TextInputAttribute-textDirection(direction: TextDirection | undefined): TextInputAttribute-End-->

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

<!--Device-TextInputAttribute-textIndent(value: Dimension): TextInputAttribute--><!--Device-TextInputAttribute-textIndent(value: Dimension): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 首行文本缩进。<br/>默认值：0 <br/>单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) <br/>取值范围：大于等于0。设置负数时，按默认值处理。 |

## textOverflow

```TypeScript
textOverflow(value: TextOverflow)
```

设置文本超长时的显示方式。仅在[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)的编辑态、非编辑态下支持。

文本截断是按字进行。例如，英文以单词为最小单位进行截断，若需要以字母为单位进行截断，可将wordBreak属性设置为WordBreak.BREAK_ALL。

当overflow设置为TextOverflow.None时，效果与TextOverflow.Clip相同。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-textOverflow(value: TextOverflow): TextInputAttribute--><!--Device-TextInputAttribute-textOverflow(value: TextOverflow): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md) | 是 | 文本超长时的显示方式。<br/>[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)非编辑态下默认值：TextOverflow.Ellipsis <br/>内联模式编辑态下默认值：TextOverflow.Clip |

## type

```TypeScript
type(value: InputType)
```

设置输入框类型。

不同的InputType会拉起对应类型的键盘，同时限制输入。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-type(value: InputType): TextInputAttribute--><!--Device-TextInputAttribute-type(value: InputType): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [InputType](arkts-arkui-inputtype-e.md) | 是 | 输入框类型。<br/>默认值：InputType.Normal |

## underlineColor

```TypeScript
underlineColor(value: ResourceColor | UnderlineColor | undefined)
```

设置下划线颜色。

开启输入框下划线[showUnderline](TextInputAttribute#showUnderline)时，支持配置下划线颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-underlineColor(value: ResourceColor | UnderlineColor | undefined): TextInputAttribute--><!--Device-TextInputAttribute-underlineColor(value: ResourceColor | UnderlineColor | undefined): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| UnderlineColor \| undefined | 是 | 设置下划线颜色。<br/>当设置下划线颜色模式时，修改下划线颜色。当只设定非特殊状态下的颜色，可以直接输入ResourceColor。设定值为undefined、null、无效值时，所有下划线恢复为默认值。<br/>默认值：主题配置的下划线颜色。主题配置的默认下划线颜色为'#33182431'。 |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

设置文本断行规则。该属性在组件设置[内联模式](../../../ui/arkts-common-components-text-input.md#内联模式)时样式生效，但对placeholder文本无效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputAttribute-wordBreak(value: WordBreak): TextInputAttribute--><!--Device-TextInputAttribute-wordBreak(value: WordBreak): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [WordBreak](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-wordbreak-e.md) | 是 | 内联输入风格编辑态时断行规则。 <br />默认值：WordBreak.BREAK_WORD |

