# RichEditorBaseController

RichEditor组件控制器基类。

**继承/实现关系：** RichEditorBaseController implements [TextEditControllerEx](../arkts-apis/arkts-arkui-texteditcontrollerex-i.md)

**起始版本：** 12

<!--Device-unnamed-declare class RichEditorBaseController implements TextEditControllerEx--><!--Device-unnamed-declare class RichEditorBaseController implements TextEditControllerEx-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

关闭自定义选择菜单或系统默认选择菜单。

当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-closeSelectionMenu(): void--><!--Device-RichEditorBaseController-closeSelectionMenu(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

删除光标前字符或选中内容。没有内容被选中时，删除当前光标位置前的1个字符；有内容被选中时，删除选中内容。

该接口不支持预上屏场景使用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-deleteBackward(): void--><!--Device-RichEditorBaseController-deleteBackward(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): number
```

返回当前光标所在位置。

当无法获取光标位置时（例如controller未与组件绑定时），该接口返回-1。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-getCaretOffset(): number--><!--Device-RichEditorBaseController-getCaretOffset(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前光标所在位置。 |

## getCaretRect

```TypeScript
getCaretRect(): RectResult | undefined
```

返回当前光标与RichEditor组件的相对位置。如果光标不闪烁或controller未绑定组件，返回undefined。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-getCaretRect(): RectResult | undefined--><!--Device-RichEditorBaseController-getCaretRect(): RectResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](arkts-arkui-rectresult-i.md) | 当前光标与RichEditor的相对位置。 |

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

获取布局管理器对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-getLayoutManager(): LayoutManager--><!--Device-RichEditorBaseController-getLayoutManager(): LayoutManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LayoutManager](../arkts-apis/arkts-arkui-layoutmanager-i.md) | 布局管理器对象，可用于获取组件内容的布局位置等信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getPreviewText

```TypeScript
getPreviewText(): PreviewText
```

获取预上屏信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-getPreviewText(): PreviewText--><!--Device-RichEditorBaseController-getPreviewText(): PreviewText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PreviewText](../arkts-apis/arkts-arkui-previewtext-i.md) | 预上屏文本信息，包含输入法预显示的候选文本内容及起始位置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getTypingStyle

```TypeScript
getTypingStyle(): RichEditorTextStyle
```

获取用户预设的文本样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-getTypingStyle(): RichEditorTextStyle--><!--Device-RichEditorBaseController-getTypingStyle(): RichEditorTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | 用户预设的文本输入样式对象，包含字体颜色、大小、粗细等样式属性，可用于查询当前组件的输入文本样式配置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## isEditing

```TypeScript
isEditing(): boolean
```

获取当前富文本的编辑状态。当controller未绑定组件或绑定controller的组件被释放时，返回false。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-isEditing(): boolean--><!--Device-RichEditorBaseController-isEditing(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示编辑态，false表示非编辑态。 |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

将指定范围内的内容滚动到可视区域。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-scrollToVisible(range?: TextRange): void--><!--Device-RichEditorBaseController-scrollToVisible(range?: TextRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | 否 | 滚动到可视区域的内容范围，包括内容起始位置和终止位置。<br>起始位置应小于等于结束位置，否则接口调用无效。起始位置小于0视为0，结束位置大于全文长度视为全文长度。<br>未指定范围时，默认为全部内容。未指定起始位置，默认起始位置为0；未指定结束位置，默认结束位置为全文长度。 |

## setCaretOffset

```TypeScript
setCaretOffset(offset: number): boolean
```

设置光标位置。

当controller未绑定组件或绑定controller的组件被释放时，该接口返回false，设置不成功。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-setCaretOffset(offset: number): boolean--><!--Device-RichEditorBaseController-setCaretOffset(offset: number): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 光标偏移位置。超出所有内容范围时，设置失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 光标是否设置成功。<br/>true表示光标位置设置成功，false表示未成功。 |

## setSelection

```TypeScript
setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

设置组件内的内容选中，选中部分背板高亮。

selectionStart和selectionEnd均为-1时表示全选，均为0时可以清空选中区。

未获焦时调用该接口不产生选中效果。

从API version 12开始，在PC/2in1设备（可通过deviceInfo.deviceType获取设备类型进行判断）中，无论options取何值，调用setSelection接口都不会弹出菜单；如果组件中已经存在菜单，调用setSelection接口会关闭菜单。在非PC/2in1设备中，options取值为MenuPolicy.DEFAULT时，遵循以下规则：

1. 组件内有手柄菜单时，接口调用后不关闭菜单，并且调整菜单位置。2. 组件内有不带手柄的菜单时，接口调用后不关闭菜单，并且菜单位置不变。3. 组件内无菜单时，接口调用后也无菜单显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-RichEditorBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 选中开始位置。 |
| selectionEnd | number | 是 | 选中结束位置。 |
| options | [SelectionOptions](arkts-arkui-selectionoptions-i.md) | 否 | 选择项配置，用于控制选中操作时的菜单弹出策略。<br>当需要自定义菜单弹出行为（如强制显示或隐藏菜单）时传入此参数；<br>省略时默认使用MenuPolicy.DEFAULT，遵循系统默认菜单弹出策略。<br>各MenuPolicy取值的适用场景请参考SelectionOptions对象说明。<br>**起始版本：** 12 |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

设置无输入时的属性字符串样式的提示文本。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-setStyledPlaceholder(styledString: StyledString): void--><!--Device-RichEditorBaseController-setStyledPlaceholder(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | 是 | 设置属性字符串样式的提示文本，其优先级高于[placeholder](RichEditorAttribute#placeholder)属性设置的提示文本。<br>提示文本不支持触发属性字符串[GestureStyle](../arkts-apis/arkts-arkui-gesturestyle-c.md)样式绑定的手势事件，以及[UrlStyle](../arkts-apis/arkts-arkui-urlstyle-c.md)样式的超链接跳转能力。 |

## setTypingParagraphStyle

```TypeScript
setTypingParagraphStyle(style: RichEditorParagraphStyle): void
```

设置用户预设的段落样式。仅在组件内容为空或组件末尾换行后，输入文本生效。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-setTypingParagraphStyle(style: RichEditorParagraphStyle): void--><!--Device-RichEditorBaseController-setTypingParagraphStyle(style: RichEditorParagraphStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md) | 是 | 预设段落样式。 |

## setTypingStyle

```TypeScript
setTypingStyle(value: RichEditorTextStyle): void
```

设置用户预设的文本样式。

当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-setTypingStyle(value: RichEditorTextStyle): void--><!--Device-RichEditorBaseController-setTypingStyle(value: RichEditorTextStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | 是 | 预设的文本输入样式，包含字体颜色、大小、粗细等属性，用于设置后续输入文本的默认样式。 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorBaseController-stopEditing(): void--><!--Device-RichEditorBaseController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

