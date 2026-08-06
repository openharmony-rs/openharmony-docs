# TextInputController

TextInput组件的控制器继承自 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_， 涉及的接口有 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ 、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 、\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_8\_\_\_ 、\_\_\_MD\_LINK\_DESC\_USD\_9\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_10\_\_\_&lt;!- -Del--&gt;以及系统接口\_\_\_MD\_LINK\_DESC\_USD\_11\_\_\_\_\_\_MD\_COMMENT\_DESC\_USD\_12\_\_\_。

**继承/实现关系：** TextInputController extends [TextContentControllerBase](../../../apis-na/arkts-apis/arkts-na-component/common-textcontentcontrollerbase-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class TextInputController extends TextContentControllerBase--><!--Device-unnamed-export declare class TextInputController extends TextContentControllerBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: int): void
```

设置输入光标的位置。当取值小于0时，取0，大于文本长度时，显示在文本末尾。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-caretPosition(value: int): void--><!--Device-TextInputController-caretPosition(value: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 |  |

## constructor

```TypeScript
constructor()
```

TextInputController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-constructor()--><!--Device-TextInputController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void
```

设置文本选择区域并高亮显示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void--><!--Device-TextInputController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | int | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。 |
| selectionEnd | int | 是 | 文本选择区域结束位置。当selectionEnd<0时，按照0处理；当selectionEnd大于文本长度时，按照文本长度处理。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 选中文字时的配置。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：MenuPolicy.DEFAULT |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-stopEditing(): void--><!--Device-TextInputController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

