# TextContentControllerBase

TextContentControllerBase

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addText

```TypeScript
addText(text: string, textOperationOptions?: TextContentControllerOptions): number
```

Add a text.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | text value. |
| textOperationOptions | TextContentControllerOptions | 否 | operation info. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | caret index |

## clearPreviewText

```TypeScript
clearPreviewText(): void
```

Clear the content of preview.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

删除输入框文本末尾字符。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteText

```TypeScript
deleteText(range?: TextRange): void
```

Delete text in TextRange.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | TextRange | 否 | range for deleting. |

## getCaretOffset

```TypeScript
getCaretOffset() : CaretOffset
```

Get the index and relative position of the CaretOffset.

<p><strong>NOTE</strong>:
<br>If this API is called when the caret position is updated in the current frame, it will not take effect.
<br>For the Search component, the returned position information is the offset of the first character
relative to the search icon in the component.
<br>If no text is entered in the Search component,
the return value contains the position information relative to the component.
<br>The location information in the return value is the location of the caret relative to the editable component.
</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CaretOffset | index and relative position of the CaretOffset. |

## getSelection

```TypeScript
getSelection(): TextRange
```

Gets the selected range of text content.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextRange | range for selecting. |

## getTextContentLineCount

```TypeScript
getTextContentLineCount() : number
```

Get the lines number of the text content.
The getTextContentLineCount type is used to obtain the number of lines of the edited text.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Text content line count |

## getTextContentRect

```TypeScript
getTextContentRect() : RectResult
```

Get the start and end positions of the text content.

<p><strong>NOTE</strong>:
<br>If no text is entered, the return value contains the position information, but the size is 0.
<br>The position information is the offset of the first character relative to the editable area.
<br>For the Search component, the returned position information is the offset of the first character
relative to the search icon in the component.
<br>If there is input, the width in the return value is the fixed width of the editable area.
</p>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RectResult | Text content rect.The unit of the return value is pixel. |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

将输入框文本滚动到可见区。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | TextRange | 否 | 可见区范围。若该参数非法，则本方法不会生效。 |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

设置提示文本的样式。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | StyledString | 是 | 设置提示文本样式的属性字符串若传入的入参无效，则本接口不生效 |

