# TextContentControllerBase

TextContentControllerBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class TextContentControllerBase--><!--Device-unnamed-export declare abstract class TextContentControllerBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addText

```TypeScript
addText(text: string, textOperationOptions?: TextContentControllerOptions): int | undefined
```

Add a text.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-addText(text: string, textOperationOptions?: TextContentControllerOptions): int | undefined--><!--Device-TextContentControllerBase-addText(text: string, textOperationOptions?: TextContentControllerOptions): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | text value. |
| textOperationOptions | [TextContentControllerOptions](arkts-na-common-textcontentcontrolleroptions-i.md) | 否 | operation info. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | caret index |

## clearPreviewText

```TypeScript
clearPreviewText(): void
```

Clear the content of preview.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-clearPreviewText(): void--><!--Device-TextContentControllerBase-clearPreviewText(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

Delete the last character of the input field component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-deleteBackward(): void--><!--Device-TextContentControllerBase-deleteBackward(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteText

```TypeScript
deleteText(range?: TextRange): void
```

Delete text in TextRange.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-deleteText(range?: TextRange): void--><!--Device-TextContentControllerBase-deleteText(range?: TextRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../../apis-arkui/arkts-apis/arkts-arkui-textcommon-textrange-i.md) | 否 | range for deleting. |

## getCaretOffset

```TypeScript
getCaretOffset(): CaretOffset | undefined
```

Get the index and relative position of the CaretOffset. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: &lt;br&gt;If this API is called when the caret position is updated in the current frame, it will not take effect. &lt;br&gt;For the Search component, the returned position information is the offset of the first character relative to the search icon in the component. &lt;br&gt;If no text is entered in the Search component, the return value contains the position information relative to the component. &lt;br&gt;The location information in the return value is the location of the caret relative to the editable component. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-getCaretOffset(): CaretOffset | undefined--><!--Device-TextContentControllerBase-getCaretOffset(): CaretOffset | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CaretOffset](arkts-na-common-caretoffset-i.md) | index and relative position of the CaretOffset. |

## getSelection

```TypeScript
getSelection(): TextRange | undefined
```

Gets the selected range of text content.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-getSelection(): TextRange | undefined--><!--Device-TextContentControllerBase-getSelection(): TextRange | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextRange](../../apis-arkui/arkts-apis/arkts-arkui-textcommon-textrange-i.md) | range for selecting. |

## getTextContentLineCount

```TypeScript
getTextContentLineCount(): int | undefined
```

Get the lines number of the text content. The getTextContentLineCount type is used to obtain the number of lines of the edited text.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-getTextContentLineCount(): int | undefined--><!--Device-TextContentControllerBase-getTextContentLineCount(): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Text content line count |

## getTextContentRect

```TypeScript
getTextContentRect(): RectResult | undefined
```

Get the start and end positions of the text content. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: &lt;br&gt;If no text is entered, the return value contains the position information, but the size is 0. &lt;br&gt;The position information is the offset of the first character relative to the editable area. &lt;br&gt;For the Search component, the returned position information is the offset of the first character relative to the search icon in the component. &lt;br&gt;If there is input, the width in the return value is the fixed width of the editable area. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-getTextContentRect(): RectResult | undefined--><!--Device-TextContentControllerBase-getTextContentRect(): RectResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](arkts-na-common-rectresult-i.md) | Text content rect.The unit of the return value is pixel. |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

Scroll the input field component to make the specified content visible.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-scrollToVisible(range?: TextRange): void--><!--Device-TextContentControllerBase-scrollToVisible(range?: TextRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../../apis-arkui/arkts-apis/arkts-arkui-textcommon-textrange-i.md) | 否 | The visible range. If the parameter is invalid, this method will have no effect. |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

Set the styled placeholder.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-setStyledPlaceholder(styledString: StyledString): void--><!--Device-TextContentControllerBase-setStyledPlaceholder(styledString: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | [StyledString](../../apis-arkui/arkts-apis/arkts-arkui-styledstring-styledstring-c.md) | 是 | The styledString for placeholder. If the parameter is invalid, this method will have no effect. |

