# TextContentControllerBase

```TypeScript
declare abstract class TextContentControllerBase
```

TextInput、TextArea、Search的基础控制器。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addText

```TypeScript
addText(text: string, textOperationOptions?: TextContentControllerOptions): number
```

在已编辑文本的指定位置插入文本，默认插入至文本末尾。

拖拽文本的状态下不生效。

> **说明：** 
> 
> `addText`仅影响应用内部的UI表现，不影响输入法应用的内部逻辑。预上屏状态由输入法管理，应用层调用`addText`/`deleteText`会破坏输入法的状态管理，因此应避免在预上屏状态下调用`addText`。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 插入的文本内容。 |
| textOperationOptions | [TextContentControllerOptions](arkts-arkui-common-comp-textcontentcontrolleroptions-i.md) | 否 | 插入文本的配置选项，用于自定义插入位置等参数。当需要在指定位置插入文本时传入此参数，不设置时默认插入文本至末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 插入文本后光标的位置。 |

## clearPreviewText

```TypeScript
clearPreviewText(): void
```

通知输入法清除当前的预上屏文本内容。

> **说明：** 
> 
> 当controller未绑定组件或绑定controller的组件被释放时，该接口不生效。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

删除基础控制器`controller`绑定的文本输入框内文本光标前的一个字符。如果在调用此功能前已用鼠标或键盘选中了部分文本，则会删除被选中的文本。

拖拽文本的状态下不生效。

`deleteBackward`仅影响应用内部的UI表现，不影响输入法应用的内部逻辑，不支持在预上屏场景下使用。

> **说明：** 
> 
> 当controller未绑定组件或绑定controller的组件被释放时，该接口不生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteText

```TypeScript
deleteText(range?: TextRange): void
```

删除已编辑文本的指定区域的内容。

> **说明：** 
> 
> - 拖拽文本的状态下不生效。
> 
> - `deleteText`仅影响应用内部的UI表现，不影响输入法应用的内部逻辑，不推荐在预上屏状态下调用。
> 
> - 当controller未绑定组件或绑定controller的组件被释放时，该接口不生效。

> **与`deleteBackward`的差异**
> 
> - `deleteText`支持范围删除，可删除任意指定区域的文本；`deleteBackward`模拟用户删除操作，删除光标前一个字符或已选中文本。
> 
> - `deleteText`在预上屏状态下应避免调用，`deleteBackward`在预上屏场景下不支持使用。
> 
> - 建议根据删除需求选择：需要删除指定范围文本时使用`deleteText`，需要删除光标前字符时使用`deleteBackward`。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | 否 | 删除文本的范围，包括删除文本的起始位置和终止位置。<br>起始位置应小于等于结束位置，否则接口调用无效。起始位置小于0视为0，结束位置大于文本长度视为文本长度。<br>未指定删除范围时，默认将删除全部文本。未指定删除文本的起始位置，则默认从下标0开始删除；未指定删除文本的终止位置，则默认以文本末尾作为删除的结束点。 |

## getCaretOffset

```TypeScript
getCaretOffset() : CaretOffset
```

返回当前光标所在位置信息。

> **说明：** 
> 
> - 在当前帧更新光标位置同时调用该接口，该接口不生效。
> 
> - 在Search组件中，返回的位置信息是相对Search组件中搜索图标的偏移值。
> 
> - 在Search组件中，不输入文本时，返回值中有相对Search组件的位置信息。
> 
> - 返回值中的位置信息是光标相对于可编辑组件的位置。
> 
> - 当无法获取光标位置时（例如[TextInputController](arkts-arkui-textinput-comp-textinputcontroller-c.md)未与[TextInput](arkts-arkui-textinput-comp.md#text_input)组件绑定时），该接口返回undefined。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CaretOffset](arkts-arkui-common-comp-caretoffset-i.md) | 光标相对输入框的位置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSelection

```TypeScript
getSelection(): TextRange
```

返回当前文本的选择范围。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | 文本当前的选择范围，未选中返回光标位置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getTextContentLineCount

```TypeScript
getTextContentLineCount() : number
```

获取已编辑文本内容的行数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已编辑文本内容行数。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getTextContentRect

```TypeScript
getTextContentRect() : RectResult
```

获取已编辑文本内容区域相对于组件的位置和大小，返回值的单位为像素。

> **说明：** 
> 
> - 初始不输入文本时，返回值中有相对组件的位置信息，大小为0。
> - 返回值中的位置信息是第一个字符相对于可编辑组件的位置。
> - 在Search组件中，返回的位置信息是相对Search组件中搜索图标的偏移值。
> - 有输入时，返回信息中的宽度是组件编辑区域的固定宽度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](arkts-arkui-common-comp-rectresult-i.md) | 获取已编辑文本内容区域相对组件的位置和大小。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

将起始索引与结束索引传递给与其绑定的输入框（TextInput、TextArea、Search）组件，并将此范围内的文字滚动到可视区域。

> **说明：** 
> 
> 当controller未绑定组件或绑定controller的组件被释放时，该接口不生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | 否 | 滚动到可视区域的文本范围，包括文本起始位置和终止位置。<br>起始位置应小于等于结束位置，否则接口调用无效。起始位置小于0视为0，结束位置大于全文长度视为全文长度。<br>未指定范围时，默认为全部文本。未指定起始位置，默认起始位置为0；未指定结束位置，默认结束位置为全文长度。 |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

设置属性字符串样式的占位文本，触发绑定或更新。

> **说明：** 
> 
> 当controller未绑定组件或绑定controller的组件被释放时，该接口不生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | 是 | 设置属性字符串样式的Placeholder，其优先级高于纯文本的placeholder属性。<br>Placeholder不支持属性字符串事件手势，超链接跳转。 |
