# SearchController

Search组件的控制器继承自TextContentControllerBase，涉及的接口有 getTextContentRect、 getTextContentLineCount、 getCaretOffset、addText、 deleteText、getSelection 、clearPreviewText、 setStyledPlaceholder、 deleteBackward、 scrollToVisible&lt;!--Del--&gt;以及系统接口 getText&lt;!--DelEnd--&gt;。

## 导入对象 ```ts controller: SearchController = new SearchController(); ```

**继承/实现关系：** SearchController extends TextContentControllerBase

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-unnamed-declare class SearchController--><!--Device-unnamed-declare class SearchController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchController-caretPosition(value: number): void--><!--Device-SearchController-caretPosition(value: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的长度。&lt;/br&gt;当value&lt;0时，按照0处理。当value&gt;字符串长度时，按照字符串长度处理。 |

## constructor

```TypeScript
constructor()
```

SearchController的构造函数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchController-constructor()--><!--Device-SearchController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取并高亮显示。 > **说明：** > > - 如果selectionStart或selectionEnd被赋值为undefined时，当作0处理。 > > - 如果selectionMenuHidden被赋值为true或设备为2in1时，即使options被赋值为MenuPolicy.SHOW，调用setTextSelection也不弹出菜单。 > > - 如果选中的文本含有emoji表情时，表情的起始位置包含在设置的文本选中区域内就会被选中。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SearchController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-SearchController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。 &lt;br&gt;当selectionStart小于0时，按照0处理；当selectionStart大于文字最大长度时，按照文字最大长度处理。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。 &lt;br&gt;当selectionEnd小于0时、按照0处理；当selectionEnd大于文字最大长度时、按照文字最大长度处理。 |
| options | SelectionOptions | 否 | 选中文字时的配置。 &lt;br&gt;默认值：MenuPolicy.DEFAULT。 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchController-stopEditing(): void--><!--Device-SearchController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

