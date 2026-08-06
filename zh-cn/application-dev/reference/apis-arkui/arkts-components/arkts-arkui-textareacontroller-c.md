# TextAreaController

TextArea组件的控制器继承自[TextContentControllerBase]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，涉及的接口有 [getTextContentRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [getTextContentLineCount]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [getCaretOffset]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、[addText]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、 [deleteText]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_、[getSelection]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_ 、[clearPreviewText]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_、 [setStyledPlaceholder]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_、 [deleteBackward]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_、 [scrollToVisible]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_\_\_\_MD\_COMMENT\_DESC\_USD\_12\_\_\_以及系统接口 [getText]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_\_\_\_MD\_COMMENT\_DESC\_USD\_13\_\_\_。

## 导入对象 ```ts controller: TextAreaController = new TextAreaController(); ```

**继承/实现关系：** TextAreaController extends [TextContentControllerBase](../../apis-na/arkts-apis/arkts-na-component/common-textcontentcontrollerbase-c.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-unnamed-declare class TextAreaController extends TextContentControllerBase--><!--Device-unnamed-declare class TextAreaController extends TextContentControllerBase-End-->

**系统能力：** 
- API版本10+：SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaController-caretPosition(value: number): void--><!--Device-TextAreaController-caretPosition(value: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的字符长度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value&lt;0时，按照0处理。当value&gt;字符串长度时，按照字符串长度处理。 |

## constructor

```TypeScript
constructor()
```

TextAreaController的构造函数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaController-constructor()--><!--Device-TextAreaController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextAreaController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当selectionStart小于0时，按0处理；当selectionStart大于文字最大长度时，按照文字最大长度处理。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当selectionEnd小于0时，按0处理；当selectionEnd大于文字最大长度时，按照文字最大长度处理。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 选中文字时的配置。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：MenuPolicy.DEFAULT\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaController-stopEditing(): void--><!--Device-TextAreaController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

