# TextInput属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。除支持[通用事件](arkts-arkui-commonmethod-c.md)外，还支持以下事件。

**继承/实现关系：** TextInputAttribute extends CommonMethod\<TextInputAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

设置自动大小写模式的文本模式，只提供接口能力，具体实现以输入法应用为主。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | 是 | 自动大小写模式。不设置时，默认不启用自动大小写功能。具体实现以输入法应用为主。 |

## barState

```TypeScript
barState(value: BarState)
```

设置内联输入风格编辑态时滚动条的显示模式。未通过该接口设置时，默认为BarState.Auto。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 内联输入风格编辑态时滚动条的显示模式。仅设置内联模式时该属性生效。 |

## cancelButton

```TypeScript
cancelButton(options: CancelButtonOptions)
```

设置右侧清除按钮样式，仅支持图片类型的图标。不支持[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式。示例请参考 示例4（设置右侧清除按钮样式）。未通过该接口设置 时，默认为{ style: CancelButtonStyle.INPUT }，Wearable设备上图标默认尺寸为28vp。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) | 是 | 右侧清除按钮样式选项。<br>**起始版本：** 18 |

## cancelButton

```TypeScript
cancelButton(symbolOptions: CancelButtonSymbolOptions)
```

设置右侧清除按钮样式，仅支持symbol图标。不支持[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式。示例请参考 示例15（设置symbol类型清除按钮）。 未通过该接口设置时，默认为{ style: CancelButtonStyle.INPUT }。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbolOptions | [CancelButtonSymbolOptions](arkts-arkui-cancelbuttonsymboloptions-i.md) | 是 | 右侧清除按钮样式。 |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

设置输入框光标颜色。未通过该接口设置时，默认为'#007DFF'（蓝色），Wearable设备上默认值为'#5EA1FF'（蓝色，比'#007DFF'颜色稍浅）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 输入框光标颜色。 |

## caretPosition

```TypeScript
caretPosition(value: number)
```

设置光标位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 光标的位置。 第一个字符前的位置是0。 当取值小于0时，取0；大于文本长度时，显示在文本末尾。 |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

设置光标风格。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | 是 | 光标的风格，用于自定义光标的显示样式。配置项包括width（光标宽度）和color（光标颜色）等。不设置时使用系统默认光标样式。 |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

设置是否开启行首标点符号压缩。未通过该接口设置时，默认不开启行首标点符号压缩。

> **说明：**
> 
> - 支持压缩的标点符号，请参考[ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md)的行首压缩的标点范围。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启行首标点符号压缩。 true表示开启行首标点符号压缩；false表示不开启行首标点符号压缩。 |

## contentType

```TypeScript
contentType(value: ContentType)
```

设置自动填充类型。<!--RP7--><!--RP7End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ContentType](arkts-arkui-contenttype-e.md) | 是 | 自动填充类型。取值范围：详见ContentType枚举说明。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置输入的文本是否可复制。设置CopyOptions.None时，只支持粘贴和全选。设置CopyOptions.None时，不允许拖拽。未通过该接口设置时，默认为CopyOptions.LocalDevice，支持设备内复制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CopyOptions | 是 | 输入的文本是否可复制。 |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

设置自定义键盘。当设置自定义键盘时，输入框激活后不会打开系统输入法，而是加载指定的自定义组件。自定义键盘的高度可以通过自定义组件根节点的height属性设置，宽度不可设置，使用系统默认值。自定义键盘采用覆盖原始界面的方式呈现，当没有开启避让模式或者输入框不需要避让的场景不会对应用原始界面产生压缩或者上提。自定义键盘无法获取焦点，但是会拦截手势事件。默认在输入控件失去焦点时，关闭自定义键盘，开发者也可以通过[TextInputController](arkts-arkui-textinputcontroller-c.md). [stopEditing](arkts-arkui-textinputcontroller-c.md#stopediting)方法控制键盘关闭。当设置自定义键盘时，可以通过绑定[onKeyPreIme](arkts-arkui-commonmethod-c.md#onkeypreime)事件规避物理键盘的输入。从API version 23开始，自定义键盘可以通过 [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature)开启接续，在切换至 其他自定义键盘时，会直接切换，不会触发键盘关闭和拉起动画。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| ComponentContent \| undefined | 是 | 自定义键盘。设定值为undefined时，关闭自定义键盘。<br>**起始版本：** 22 |
| options | [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | 否 | 设置自定义键盘是否支持避让功能。 不设置该参数时，自定义键盘默认不支持避让功能。<br>**起始版本：** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

设置文本装饰线类型样式及其颜色。未通过该接口设置时，默认为{&nbsp;type:&nbsp;TextDecorationType.None,&nbsp;color:&nbsp;Color.Black,&nbsp;style:&nbsp;TextDecorationStyle.SOLID,&nbsp;thicknessScale:&nbsp;1.0}。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | 是 | 文本装饰线对象。 |

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
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | 是 | 扩展菜单选项。 |

## ellipsisMode

```TypeScript
ellipsisMode(mode: Optional<EllipsisMode>)
```

设置省略位置。ellipsisMode属性仅在[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式下生效，需要配合 [textOverflow](#textoverflow)设置为TextOverflow.Ellipsis使用，单独设置ellipsisMode属性不生效。未通过该接口设置时，默认为 EllipsisMode.END。非编辑态时正常生效，编辑态时EllipsisMode.START和EllipsisMode.CENTER仅在maxLines设置为1时生效，EllipsisMode.END、EllipsisMode.MULTILINE_START 和EllipsisMode.MULTILINE_CENTER正常生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;EllipsisMode&gt; | 是 | 省略位置。 |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

设置是否启用自动填充。未通过该接口设置时，默认启用自动填充。<!--RP6--><!--RP6End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用自动填充。 true表示启用，false表示不启用。 |

## enableAutoFillAnimation

```TypeScript
enableAutoFillAnimation(enabled: Optional<boolean>)
```

设置是否启用自动填充动效。未通过该接口设置时，默认为true。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用自动填充动效。 true表示启用，false表示不启用。    **说明：** 需先设置[enableAutoFill](#enableautofill)启用自动填充功能。启用之后，仅输入模式 [InputType](arkts-arkui-inputtype-e.md)设置为Password、NEW_PASSWORD或NUMBER_PASSWORD的输入框在进行自动填充时动效可生效。 |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

设置是否开启中文与西文的自动间距。未通过该接口设置时，默认为false。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否开启触控反馈。 true表示开启触控反馈，false表示不开启触控反馈。 |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

设置TextInput通过点击以外的方式获焦时，是否主动拉起软键盘。未通过该接口设置时，默认TV设备为false，其他设备为true。从API version 10开始，获焦默认绑定输入法。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 通过点击以外的方式获焦时，是否主动拉起软键盘。 true表示主动拉起软键盘，false表示不主动拉起。 |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

设置是否开启输入预上屏。未通过该接口设置时，默认开启输入预上屏。预上屏内容定义为文字暂存态，目前不支持文字拦截功能。

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

设置是否对选中文本进行实体识别。该接口依赖设备底层应具有文本识别能力，否则设置不会生效。未通过该接口设置时，默认开启选中文本实体识别，并识别所有类型的实体，同时启用AI菜单功能。当enableSelectedDataDetector设置为true时，默认识别所有类型的实体。启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。AI菜单功能启用时，在组件中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括[TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md)中的url（打开链接）、email（新建邮件）、phoneNumber（ 呼叫）、address（导航前往）、dateTime（新建日程）。AI菜单生效时，选中范围内需包括且仅包括一个完整的AI实体，才能展示对应的选项。该菜单项与[TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md)中的askAI菜单项不同时出现。需要CopyOptions为CopyOptions.LocalDevice或CopyOptions.CROSS_DEVICE时，本功能生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否开启选中文本实体识别。 true：开启识别，false：关闭识别。 值为undefined时，按默认值处理。 |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

设置输入法回车键类型。未通过该接口设置时，默认为EnterKeyType.Done。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-enterkeytype-e.md) | 是 | 输入法回车键类型。 |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。不通过该接口设置，默认行高不基于文字实际高度自适应。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 行高是否基于文字实际高度自适应。 true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 此接口仅当行高小于文字实际高度时生效。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。未通过该接口设置时，默认颜色跟随主题，Wearable设备上默认值为'#dbffffff'（白色，不透明度为86%）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。 |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

设置字体列表。未通过该接口设置时，默认字体为'HarmonyOS Sans'。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 字体列表。使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。 应用当前支持'HarmonyOS Sans'字体和自定义字体。 卡片当前仅支持'HarmonyOS Sans'字体。 Wearable设备支持'HarmonyOS Sans'字体和自定义字体。 |

## fontFeature

```TypeScript
fontFeature(value: string)
```

设置文字特性效果，比如数字等宽的特性。格式为：normal \| \&lt;feature-tag-value\&gt;\&lt;feature-tag-value\&gt;的格式为：\&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]\&lt;feature-tag-value\&gt;的个数可以有多个，中间用','隔开。例如，使用等宽数字的输入格式为："ss01" on。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 文字特性效果，用于设置OpenType字体高级排版能力（如等宽数字、连字等）。格式为normal或 &lt;feature-tag-value&gt;，例如"ss01" on。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置字体大小。未通过该接口设置时，默认字体大小为16fp，Wearable设备上默认值为18fp。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。fontSize为number类型时，使用fp单位。不支持设置百分比字符串。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。未通过该接口设置时，默认为FontStyle.Normal。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FontStyle | 是 | 字体样式。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

设置文本的字体粗细，设置过大可能会在不同字体下有截断。未通过该接口设置时，默认为FontWeight.Normal。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本的字体粗细，number类型取值[100,900]，取值间隔为100，取值越大，字体越粗。string类型仅支持 number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular”、“medium”，分别对应FontWeight中相应的枚举值。 从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

设置文本在行内垂直居中，将行间距平分至行的顶部与底部。未通过该接口设置时，默认为false。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置文本是否垂直居中。 true表示将行间距平分至行的顶部与底部，false则不平分。 |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

组件设置为内联输入风格时，设置文本自适应高度的方式。未通过该接口设置时，默认为TextHeightAdaptivePolicy.MAX_LINES_FIRST。当设置为TextHeightAdaptivePolicy.MAX_LINES_FIRST时，优先使用[maxLines](#maxlines)属性来调整文本高度。如果使用 maxLines属性的布局大小超过了布局约束，则尝试在[minFontSize](#minfontsize)和 [maxFontSize](#maxfontsize)的范围内缩小字体以显示更多文本。当设置为TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST时，优先使用minFontSize属性来调整文本高度。如果使用minFontSize属性可以将文本布局在一行中，则尝试在 minFontSize和maxFontSize的范围内增大字体并使用最大限度的字体大小。当设置为TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST时，与TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST效果一样。组件设置为非内联输入风格时，设置文本自适应高度(TextHeightAdaptivePolicy)的三种方式效果一样，即在minFontSize和maxFontSize的范围内缩小字体以显示更多文本。

> **说明：**
> 
> 组件设置为内联输入风格，编辑态与非编辑态存在字体大小不一致情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | 是 | 文本自适应高度的方式。仅设置内联输入风格时该属性生效。 |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

设置是否在首行和尾行增加间距以避免文字截断。不通过该接口设置，默认不增加间距。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否在首行和尾行增加间距以避免文字截断。 true表示在首行和尾行增加间距；false表示在首行和尾行不增加间距。 |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。未通过该接口设置时，默认无输入过滤规则，所有输入都允许显示。从API version 11开始，设置inputFilter且输入的字符不为空字符，会导致[type](#type)接口附带的文本过滤效果失效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 正则表达式。 |
| error | Callback &lt;string&gt; | 否 | 正则匹配失败时，返回被过滤的内容。<br>**起始版本：** 18 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

设置输入框拉起的键盘样式，需要输入法适配后生效。具体参考[输入法应用沉浸模式](../../../inputmethod/inputmethod-immersive-mode-guide.md)。未通过该接口设置时，默认为 KeyboardAppearance.NONE_IMMERSIVE。

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

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

设置折行规则。该属性在wordBreak不等于BREAK_ALL的时候生效，不支持连词符。未通过该接口设置时，默认为LineBreakStrategy.GREEDY。适用于需要优化文本换行效果的场景：LineBreakStrategy.GREEDY适用于优先填充每行的快速换行；LineBreakStrategy.HIGH_QUALITY适用于追求更优视觉效果的排版； LineBreakStrategy.BALANCED适用于需要均匀分配各行内容的布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | 是 | 文本的折行规则。 LineBreakStrategy.GREEDY表示贪婪折行，优先填充每行；LineBreakStrategy.HIGH_QUALITY表示高质量折行，平衡行长；LineBreakStrategy.BALANCED 表示均衡折行，优化排版美观。    **说明：** 仅设置[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式时该属性生效。 |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

设置文本的行高。设置值不大于0时，不限制文本行高，自适应字体大小，number类型时单位为fp。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

> **说明：**
> 
> - 特殊字符字体高度远超出同行的其他字符高度时，文本框出现截断、遮挡、内容相对位置发生变化等不符合预期的显示异常，需要开发者调整组件高度、行高等属性，修改对应的页面布局。
> 
> - 设置[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)时，通过该接口设置行高
> [lineHeight](#lineheight)不生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本行高。 number类型时单位为fp。 |

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
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 文本最大的字体缩放倍数，支持undefined类型。 取值范围：[1, +∞)    **说明：** 设置的值小于1时，按值为1处理。异常值默认不生效。 当设置maxFontScale属性后，showError最多放大到2倍。 使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和 [app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见 示例18（设置最小字体范围与最大字体范围）。 |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

设置文本最大显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。需配合[minFontSize](#minfontsize)以及[maxLines](#maxlines)(组件设置为内联输入风格且编 辑态时使用)或布局大小限制使用，单独设置不生效。自适应字号生效时，fontSize设置不生效。maxFontSize小于等于0或者maxFontSize小于minFontSize时，自适应字号不生效，此时按照[fontSize](#fontsize)属性的值生效，未设置时按照 其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最大显示字号。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) 需大于0且大于minFontSize，否则自适应字号不生效，按fontSize属性值生效。 需配合minFontSize使用，单独设置不生效。 |

## maxLength

```TypeScript
maxLength(value: number)
```

设置文本的最大输入字符数。未通过该接口设置时，默认可以无限输入。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 文本的最大输入字符数。 取值范围：[0, 2^31-1]    **说明：** 当不设置该属性或设置异常值时，取默认值。设置小数时，取整数部分。设置值超过取值范围上限时，可能导致组件显示或功能异常，请勿超过上限值。 |

## maxLines

```TypeScript
maxLines(value: number)
```

设置内联输入风格编辑态时文本可显示的最大行数。未通过该接口设置时，默认为3。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内联输入风格编辑态时文本可显示的最大行数。仅设置内联模式且处于编辑态时该属性生效。 取值范围：(0, UINT32_MAX]。传入0或负数时，按默认值3处理；超出UINT32_MAX时，自动修正为UINT32_MAX。 |

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
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 文本最小的字体缩放倍数，支持undefined类型。 取值范围：[0, 1]    **说明：** 设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。异常值默认不生效。 使用前需在工程中配置[configuration.json](../../../quick-start/app-configuration-file.md#configuration标签)文件和 [app.json5](../../../quick-start/app-configuration-file.md)文件，具体详见 示例18（设置最小字体范围与最大字体范围）。 |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

设置文本最小显示字号。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。需配合[maxFontSize](#maxfontsize)以及[maxLines](#maxlines)(组件设置为内联输入风格且编 辑态时使用)或布局大小限制使用，单独设置不生效。自适应字号生效时，fontSize设置不生效。minFontSize小于或等于0时，自适应字号不生效，此时按照[fontSize](#fontsize)属性的值生效，未设置时按照其默认值生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 文本最小显示字号。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) 需大于0，小于或等于0时自适应字号不生效，按fontSize属性值生效。 需配合maxFontSize使用，单独设置不生效。 |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

输入内容发生变化时，触发该回调。在本回调中，若执行了光标操作，需要开发者在预上屏场景下依据previewText参数调整光标逻辑，以适应预上屏场景。

**起始版本：** 7

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

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;boolean&gt; | 是 | 输入状态变化回调，返回值为true表示输入框处于编辑态（有光标显示，可以接收用户输入）；返回值为false表示输入框处于非编辑态（无光标显示，不能接收 用户输入）。<br>**起始版本：** 18 |

## onEditChanged

```TypeScript
onEditChanged(callback: (isEditing: boolean) => void)
```

输入状态变化时，触发该回调。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [onEditChange](#oneditchange)

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
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;boolean&gt; | 是 | 回调函数。 true表示密码显示；false表示密码隐藏。 |

## onSubmit

```TypeScript
onSubmit(callback: OnSubmitCallback)
```

按下输入法回车键触发该回调。非TV设备按下回车键时输入框默认会失焦且收起键盘，可在OnSubmitCallback回调中配置是否收起键盘，参考 示例2（设置下划线）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 是 | 文本选择变化回调或光标位置变化回调。<br>**起始版本：** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

在输入框将要绑定输入法前触发该回调。<!--Del-->在输入框将要绑定输入法前，可以通过`UIContext`的系统接口 setKeyboardAppearanceConfig设置键盘的样式。&lt;!--DelEnd- -&gt;从API version 22开始，调用[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)的[setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig)方法可以设置输入法扩展信息。在绑定输 入法成功后，输入法会收到扩展信息，输入法可以依据此信息实现自定义功能。IMEClient仅在onWillAttachIME执行期间有效，不可进行异步调用。

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
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; | 是 | 在输入框将要绑定输入法前触发该回调。 |

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
| callback | Callback&lt;[EditableTextChangeValue](../arkts-apis/arkts-arkui-editabletextchangevalue-i.md), boolean&gt; | 是 | 在文本内容将要发生变化时的回调。 回调参数类型为EditableTextChangeValue时，包含文本变化的相关信息。回调参数类型为boolean时，表示是否允许此次文本变化，返回true：允许文本正常修改，变化会生效；返回false：拦截此次 文本变化操作，文本内容不会发生改变。开发者可通过此回调实现对文本变化的拦截和控制。 |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

在进行复制操作前，触发该回调。

> **说明：**
> 
> onWillCopy和onCopy形成will/did时序模式：
> 
> - onWillCopy在复制操作前触发，可通过返回false拦截复制操作；返回true则允许复制，随后触发onCopy。
> 
> - onCopy在复制操作完成后触发，无法拦截。
> 
> - 两者可以同时使用，onWillCopy用于拦截控制，onCopy用于获取复制结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string, boolean&gt; | 是 | 复制操作前的回调。回调参数类型为string时，表示将要被复制的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被复 制，true：允许文本被复制，执行正常的复制操作；false：不允许文本被复制，拦截此次复制操作，文本不会被复制到剪贴板。 |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

在进行剪切操作前，触发该回调。

> **说明：**
> 
> onWillCut和onCut形成will/did时序模式：
> 
> - onWillCut在剪切操作前触发，可通过返回false拦截剪切操作；返回true则允许剪切，随后触发onCut。
> 
> - onCut在剪切操作完成后触发，无法拦截。
> 
> - 两者可以同时使用，onWillCut用于拦截控制，onCut用于获取剪切结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;string, boolean&gt; | 是 | 剪切操作前的回调。回调参数类型为string时，表示将要被剪切的文本内容。回调参数类型为boolean时，表示当前选中文本是否允许被剪 切，true：允许文本被剪切，执行正常的剪切操作；false：不允许文本被剪切，拦截此次剪切操作，文本不会被剪切到剪贴板也不会从输入框中删除。 |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

在将要删除时，触发该回调。

> **说明：**
> 
> onWillDelete和onDidDelete形成will/did时序模式：
> 
> - onWillDelete在删除操作前触发，可通过返回false拦截删除操作；返回true则允许删除，随后触发onDidDelete
> 
> - onDidDelete在删除完成后触发，无法拦截
> 
> - 两者可以同时使用，onWillDelete用于拦截控制，onDidDelete用于获取删除结果

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md), boolean&gt; | 是 | 在将要删除时调用的回调。 回调参数类型为DeleteValue时，包含将要删除的文本内容等信息。回调参数类型为boolean时，表示是否允许此次删除，返回true：允许文本正常删除；返回false：拦截此次删除操作，文本不会被删除。开发者可 通过此回调实现对删除操作的拦截和控制。 在预上屏删除操作时，该回调不触发。 仅支持系统输入法输入的场景。 |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

在将要输入时，触发该回调。

> **说明：**
> 
> onWillInsert和onDidInsert形成will/did时序模式：
> 
> - onWillInsert在输入操作前触发，可通过返回false拦截输入操作；返回true则允许输入，随后触发onDidInsert
> 
> - onDidInsert在输入完成后触发，无法拦截
> 
> - 两者可以同时使用，onWillInsert用于拦截控制，onDidInsert用于获取输入结果

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md), boolean&gt; | 是 | 在将要输入时调用的回调。 回调参数类型为InsertValue时，包含将要插入的文本内容等信息。回调参数类型为boolean时，表示是否允许此次插入，返回true：允许文本正常插入到输入框中；返回false：拦截此次插入操作，文本不会被插 入。开发者可通过此回调实现对输入内容的过滤和拦截。 在预上屏和候选词操作时，该回调不触发。 仅支持系统输入法输入的场景。 |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

设置文本排版时是否使能孤字优化。不通过该接口设置，默认不使能孤字优化。使能后，会调整换行点以尽可能避免孤立字符（段落尾行首字符），改善文本布局。该特性需在wordBreak为非BREAK_ALL且待排版文本首个 [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)的[locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md)为"zh-Hans"或"zh-Hant"时生效。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 段落最后一行是否使能孤字优化。 true表示使能孤字优化，false表示不使能孤字优化。 值为undefined或null时，不使能孤字优化。 孤字优化需在wordBreak为非BREAK_ALL并且待排版文本首个TextStyle的locale为"zh-Hans"或"zh-Hant"时生效。 |

## passwordIcon

```TypeScript
passwordIcon(value: PasswordIcon)
```

设置在密码模式下，输入框末尾的图标。未通过该接口设置时，默认使用系统提供的密码图标。支持jpg、png、bmp、heic和webp类型的图片格式。该图标的固定尺寸为24vp，Wearable设备上默认尺寸为28vp，若引用的图标过 大或过小，均显示为固定尺寸。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PasswordIcon](arkts-arkui-passwordicon-i.md) | 是 | 密码输入模式时，输入框末尾的图标。 |

## passwordRules

```TypeScript
passwordRules(value: string)
```

定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。<!--RP1--><!--RP1End-->

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 定义生成密码的规则。    **说明：** 需先设置[enableAutoFill](#enableautofill)启用自动填充功能，并设置 [contentType](#contenttype)为NEW_PASSWORD类型，该属性在触发自动填充时生效。 |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

设置placeholder文本颜色。未通过该接口设置时，默认颜色跟随主题，Wearable设备上默认值为'#99ffffff'（白色，不透明度为60%）。

**起始版本：** 7

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

设置placeholder文本样式，包括字体大小、字体粗细、字体族、字体风格。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 否 | placeholder文本样式。 省略该参数时使用系统默认字体样式。 Wearable设备上字体大小默认值为18fp |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

设置是否启用行尾标点符号悬挂。不通过该接口设置，默认标点符号不悬挂。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用行尾标点符号悬挂。 true表示启用行尾标点符号悬挂，false表示不启用行尾标点符号悬挂。设置为undefined或null时，不启用标点符号悬挂。 |

## selectAll

```TypeScript
selectAll(value: boolean)
```

设置初始状态时，是否全选文本。不支持[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式。未通过该接口设置时，默认不会全选文本。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全选文本。 true表示会全选文本，false表示不会全选文本。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置文本选中底板颜色。如果未设置不透明度，默认为20%不透明度。未通过该接口设置时，默认为'#FF007DFF'（蓝色），Wearable设备上默认值为'#FF1F71FF'（蓝色，比'#FF007DFF'颜色稍深）。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) \| undefined | 是 | 文本拖拽时的背板样式。 设置为undefined时：背板颜色跟随主题，浅色模式显示白色，深色模式显示黑色。 |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

设置是否隐藏系统文本选择菜单。未通过该接口设置时，默认显示系统文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏系统文本选择菜单。 设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。 设置为false时，显示系统文本选择菜单。 |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

设置文本着色器效果，如线性渐变、径向渐变效果等。

> **说明：**
> 
> 当同时设置shaderStyle和[strokeWidth](#strokewidth)时，shaderStyle不生效。
> 
> shaderStyle的优先级高于[fontColor](#fontcolor)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) \| undefined | 是 | 文本着色器效果，用于设置文本的渐变或特殊颜色效果。支持线性渐变、径向渐变、纯色等类型。 当同时设置shaderStyle和strokeWidth时，shaderStyle不生效。 值为undefined时，无渐变效果。 |

## showCounter

```TypeScript
showCounter(value: boolean, options?: InputCounterOptions)
```

设置当通过InputCounterOptions输入的字符数超过阈值时显示计数器。未调用showCounter接口时，默认不显示计数器。参数value为true时，才能设置options，文本框开启计数下标功能，需要配合[maxLength](#maxlength)（设置最大字符限制）一起使用。字符计数器显示的效果是 当前输入字符数/最大可输入字符数。当输入字符数大于最大字符数乘百分比值时，显示字符计数器。如果用户设置计数器时不设置InputCounterOptions，那么当前输入字符数超过最大字符数时，边框和计数器下标将变为红色。用户同时设置参数value为true和 [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md)，当thresholdPercentage数值在有效区间内，且输入字符数超过最大字符数时，边框和计数器下标将变为红色，框体抖动。 highlightBorder设置为false，则不显示红色边框，计数器默认显示红色，框体抖动。  
[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式、[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)下字符计数器不显 示。  
示例5（设置计数器）展示了设置showCounter的效果。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示计数器。 true表示显示计数器，false表示不显示。 |
| options | [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | 否 | 计数器的配置项，用于设置计数器阈值百分比、边框高亮等。当需要自定义计数器显示规则时传入此参数。不传入时使用默认计数器配置（阈值百分比为100%，边框 高亮为true）。 |

## showError

```TypeScript
showError(value?: ResourceStr | undefined)
```

设置错误状态下提示的错误文本或者不显示错误状态。当参数类型为ResourceStr并且输入内容不符合定义规范时，提示错误文本，当提示错误单行文本超长时，末尾以省略号显示。当参数类型为undefined时，不显示错误状态。请参考 示例2。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined | 否 | 错误状态下提示的错误文本或者不显示错误状态。 默认不显示错误状态。 Wearable设备上字体大小为：13fp，对齐方式为：居中对齐    **说明：** 从API version 12开始，value支持Resource类型。 不支持[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式。<br>**起始版本：** 12 |

## showPassword

```TypeScript
showPassword(visible: boolean)
```

设置密码的显隐状态。未通过该接口设置时，默认不显示密码。当[InputType](arkts-arkui-inputtype-e.md)设置为Password、NEW_PASSWORD和NUMBER_PASSWORD模式时，密码保护功能才能生效。非密码输入模式则不会触发该功能。  
[密码模式](../../../ui/arkts-common-components-text-input.md#密码模式)时，由于输入框后端的状态和前端应用侧的状态管理变量会不一致，可能导致末尾图标的状态异常。建议在 [onSecurityStateChange](#onsecuritystatechange)上增加状态同步。参考 示例1（设置与获取光标位置）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 是否显示密码。 true表示会显示密码，false表示不会显示密码。 建议在[onSecurityStateChange](#onsecuritystatechange)回调中同步状态，避免末尾图标状态异常。 |

## showPasswordIcon

```TypeScript
showPasswordIcon(value: boolean)
```

设置在密码模式下，输入框末尾的图标是否显示。未通过该接口设置时，默认TV设备为false，其他设备为true。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 密码输入模式时，输入框末尾的图标是否显示。 true表示显示，false表示不显示。 |

## showUnderline

```TypeScript
showUnderline(value: boolean)
```

设置是否开启下划线。未通过该接口设置时，默认不开启下划线，下划线默认颜色为'#33182431'（深灰色，不透明度为20%），默认粗细为1px，文本框尺寸48vp，下划线只支持InputType.Normal类型。设置密码模式时， 下划线不生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启下划线。 true表示开启，false表示不开启。 |

## showUnit

```TypeScript
showUnit(value: CustomBuilder)
```

设置控件作为文本框单位。需搭配[showUnderline](#showunderline)使用，当showUnderline为true时生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 文本输入时，文本框的显示单位。 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

设置是否阻止返回键事件向其他组件或系统传递。设置为true时，TextInput拦截返回键事件，不向其他组件传递；设置为false时，返回键事件正常向其他组件或系统传递。适用于需要自定义返回键行为的场景，如表单未保存时拦截返回操作 并弹出确认提示、自定义导航流程、游戏或特殊交互场景中需要接管返回键控制等。未通过该接口设置时，默认为true，异常值取默认值。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否阻止返回键。 true表示阻止，false表示不阻止。 |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

设置文本描边的颜色。未通过该接口设置时，默认为字体颜色，设置异常值时取默认值。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 描边颜色。 |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

设置文本描边拐角样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) \| undefined | 是 | 文本描边拐角样式。 值为undefined时，按照StrokeJoinStyle.MITER_JOIN处理，请参考[StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md)，文本拐角处表现为锐角。 |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

设置文本描边的宽度。未通过该接口设置时，默认值为0，不做描边处理。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 文本描边的宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。 若设置值小于0，显示实心字；若大于0，显示空心字。 |

## style

```TypeScript
style(value: TextInputStyle | TextContentStyle)
```

设置输入框为默认风格或内联输入风格，内联输入风格只支持InputType.Normal类型。输入框类型介绍请参考[type](#type)接口。未通过该接口设置时，默认为TextInputStyle.Default。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextInputStyle](arkts-arkui-textinputstyle-e.md) \| [TextContentStyle](../arkts-apis/arkts-arkui-textcontentstyle-e.md) | 是 | 输入框为默认风格或内联输入风格。 |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

设置文本在输入框中的水平对齐方式。未通过该接口设置时，默认为TextAlign.Start。支持TextAlign.Start、TextAlign.Center和TextAlign.End。TextAlign.JUSTIFY的对齐方式按照TextAlign.Start处理。可通过align属性控制文本段落在垂直方向上的位置。此组件不支持通过align属性控制文本段落在水平方向上的位置。  
- Alignment.TopStart、Alignment.Top、Alignment.TopEnd：内容顶部对齐。  
- Alignment.Start、Alignment.Center、Alignment.End：内容垂直居中。  
- Alignment.BottomStart、Alignment.Bottom、Alignment.BottomEnd：内容底部对齐。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | TextAlign | 是 | 文本在输入框中的水平对齐方式。 |

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

## textIndent

```TypeScript
textIndent(value: Dimension)
```

设置首行文本缩进。未通过该接口设置时，默认为0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 首行文本缩进。 单位：[vp](../arkts-apis/arkts-arkui-length-t.md) 取值范围：大于等于0。设置负数时，按默认值处理。 |

## textOverflow

```TypeScript
textOverflow(value: TextOverflow)
```

设置文本超长时的显示方式。仅在[TextInputStyle](arkts-arkui-textinputstyle-e.md)值为内联模式的编辑态、非编辑态下支持。未通过该接口设置时，内联模式非编辑态下默认为 TextOverflow.Ellipsis，内联模式编辑态下默认为TextOverflow.Clip。文本截断是按字进行。例如，英文以单词为最小单位进行截断，若需要以字母为单位进行截断，可将wordBreak属性设置为WordBreak.BREAK_ALL。当overflow设置为TextOverflow.None时，效果与TextOverflow.Clip相同。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md) | 是 | 文本超长时的显示方式。 |

## type

```TypeScript
type(value: InputType)
```

设置输入框类型。不同的InputType会拉起对应类型的键盘，同时限制输入。未通过该接口设置时，默认为InputType.Normal。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [InputType](arkts-arkui-inputtype-e.md) | 是 | 输入框类型。 |

## underlineColor

```TypeScript
underlineColor(value: ResourceColor | UnderlineColor | undefined)
```

设置下划线颜色。未通过该接口设置时，默认为主题配置的下划线颜色，主题配置的默认下划线颜色为'#33182431'（深灰色，不透明度为20%）。开启输入框下划线[showUnderline](#showunderline)时，支持配置下划线颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| [UnderlineColor](arkts-arkui-underlinecolor-i.md) \| undefined | 是 | 设置下划线颜色。 当设置下划线颜色模式时，修改下划线颜色。当只设定非特殊状态下的颜色，可以直接输入ResourceColor。设定值为undefined、null、无效值时，所有下划线恢复为默认值。 |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

设置文本断行规则。该属性在组件设置[TextInputStyle](arkts-arkui-textinputstyle-e.md)的内联模式时样式生效，但对placeholder文本无效。未通过该接口设置时，默认为 WordBreak.BREAK_WORD。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | WordBreak | 是 | 内联输入风格编辑态时断行规则。 |
