# SearchController

Search组件的控制器继承自[TextContentControllerBase](arkts-arkui-textcontentcontrollerbase-c.md)，涉及的接口有 [getTextContentRect](arkts-arkui-textcontentcontrollerbase-c.md#gettextcontentrect)、 [getTextContentLineCount](arkts-arkui-textcontentcontrollerbase-c.md#gettextcontentlinecount)、 getCaretOffset、addText、 [deleteText](arkts-arkui-textcontentcontrollerbase-c.md#deletetext)、getSelection 、[clearPreviewText](arkts-arkui-textcontentcontrollerbase-c.md#clearpreviewtext)、 setStyledPlaceholder、 deleteBackward、 scrollToVisible<!--Del-->以及系统接口 getText<!--DelEnd-->。

## 导入对象

```ts
controller: SearchController = new SearchController();
```

**继承/实现关系：** SearchController extends [TextContentControllerBase](arkts-arkui-textcontentcontrollerbase-c.md)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的长度。 & lt;/br & gt;当value & lt;0时，按照0处理。当value & gt;字符串长度时，按照字符串长度处理。 |

## constructor

```TypeScript
constructor()
```

SearchController的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取并高亮显示。

> **说明：**
> 
> - 如果selectionStart或selectionEnd被赋值为undefined时，当作0处理。
> 
> - 如果selectionMenuHidden被赋值为true或设备为2in1时，即使options被赋值为MenuPolicy.SHOW，调用setTextSelection也不弹出菜单。
> 
> - 如果选中的文本含有emoji表情时，表情的起始位置包含在设置的文本选中区域内就会被选中。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。 当selectionStart小于0时，按照0处理；当selectionStart大于文字最大长度时，按照文字最大长度处理。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。 当selectionEnd小于0时、按照0处理；当selectionEnd大于文字最大长度时、按照文字最大长度处理。 |
| options | [SelectionOptions](arkts-arkui-selectionoptions-i.md) | 否 | 选中文字时的配置。 默认值：MenuPolicy.DEFAULT。 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
