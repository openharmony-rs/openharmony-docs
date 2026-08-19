# TextInputController

TextInput组件的控制器继承自TextContentControllerBase，涉及的接口有 getTextContentRect、 getTextContentLineCount、 getCaretOffset、addText、 deleteText、getSelection 、clearPreviewText、 setStyledPlaceholder、 deleteBackward、 scrollToVisible<!--Del-->以及系统接口 getText<!--DelEnd-->。

## 导入对象 ```ts controller: TextInputController = new TextInputController(); ```

**继承/实现关系：** TextInputController extends TextContentControllerBase

**起始版本：** 8

<!--Device-unnamed-declare class TextInputController--><!--Device-unnamed-declare class TextInputController-End-->

**系统能力：** 
- API版本10+：SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。当取值小于0时，取0，大于文本长度时，显示在文本末尾。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputController-caretPosition(value: number): void--><!--Device-TextInputController-caretPosition(value: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的字符长度。 |

## constructor

```TypeScript
constructor()
```

TextInputController的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputController-constructor()--><!--Device-TextInputController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

设置文本选择区域并高亮显示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextInputController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。当selectionStart&lt;0时，按照0处理；当selectionStart大于文本长度时，按照文本长度处 理。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。当selectionEnd&lt;0时，按照0处理；当selectionEnd大于文本长度时，按照文本长度处理。 |
| options | SelectionOptions | 否 | 选中文字时的配置，用于控制文本选择菜单的显示策略。 <br>配置项包括menuPolicy，用于指定菜单显示方式：MenuPolicy.DEFAULT表示按系统默认行为显示菜单；MenuPolicy.SHOW表示强制显示菜单；MenuPolicy.HIDE表示强制隐藏菜单。 <br>默认值MenuPolicy.DEFAULT <br>从API version 12开始，该接口中的options参数支持在原子化服务中使用。<br>**起始版本：** 12 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextInputController-stopEditing(): void--><!--Device-TextInputController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

