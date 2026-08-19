# RichEditor

支持图文混排和文本交互式编辑的组件。 > **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件 不包含子组件。

## RichEditor

```TypeScript
RichEditor(value: RichEditorOptions)
```

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorInterface-(value: RichEditorOptions): RichEditorAttribute--><!--Device-RichEditorInterface-(value: RichEditorOptions): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorOptions](arkts-arkui-richeditoroptions-i.md) | 是 | 富文本组件初始化选项。 |

## RichEditor

```TypeScript
RichEditor(options: RichEditorStyledStringOptions)
```

创建富文本组件时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorInterface-(options: RichEditorStyledStringOptions): RichEditorAttribute--><!--Device-RichEditorInterface-(options: RichEditorStyledStringOptions): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | 是 | 富文本组件初始化选项。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CopyEvent](arkts-arkui-copyevent-i.md) | 定义用户复制事件。 |
| [CutEvent](arkts-arkui-cutevent-i.md) | 定义用户剪切事件。 |
| [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | 设置自定义键盘是否支持避让功能。 |
| [LeadingMarginPlaceholder](arkts-arkui-leadingmarginplaceholder-i.md) | 前导边距占位符，用于表示文本段落左侧与组件边缘之间的距离。 |
| [PasteEvent](arkts-arkui-pasteevent-i.md) | 定义用户粘贴事件。 |
| [PlaceholderStyle](arkts-arkui-placeholderstyle-i.md) | 设置提示文本的字体样式。 |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md) | 设置builder的偏移位置和样式。 |
| [RichEditorChangeValue](arkts-arkui-richeditorchangevalue-i.md) | 图文变化信息。 |
| [RichEditorDeleteValue](arkts-arkui-richeditordeletevalue-i.md) | 删除操作和被删除内容的信息。 |
| [RichEditorGesture](arkts-arkui-richeditorgesture-i.md) | 用户手势事件。 |
| [RichEditorImageSpan](arkts-arkui-richeditorimagespan-i.md) | 图片Span信息。 |
| [RichEditorImageSpanOptions](arkts-arkui-richeditorimagespanoptions-i.md) | 设置图片的偏移位置和图片样式信息。 |
| [RichEditorImageSpanResult](arkts-arkui-richeditorimagespanresult-i.md) | 后端返回的图片信息。 |
| [RichEditorImageSpanStyle](arkts-arkui-richeditorimagespanstyle-i.md) | 图片样式。 |
| [RichEditorImageSpanStyleResult](arkts-arkui-richeditorimagespanstyleresult-i.md) | 后端返回的图片样式信息。 |
| [RichEditorInsertValue](arkts-arkui-richeditorinsertvalue-i.md) | 插入文本的信息。 |
| [RichEditorLayoutStyle](arkts-arkui-richeditorlayoutstyle-i.md) | 图片布局信息。 |
| [RichEditorOptions](arkts-arkui-richeditoroptions-i.md) | RichEditor初始化参数。 |
| [RichEditorParagraphResult](arkts-arkui-richeditorparagraphresult-i.md) | 后端返回的段落信息。 |
| [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md) | 段落样式。 |
| [RichEditorParagraphStyleOptions](arkts-arkui-richeditorparagraphstyleoptions-i.md) | 段落样式选项。 继承自[RichEditorRange](arkts-arkui-richeditorrange-i.md)。 |
| [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 定义RichEditor的范围。 |
| [RichEditorSelection](arkts-arkui-richeditorselection-i.md) | 选中内容信息。 |
| [RichEditorSpanPosition](arkts-arkui-richeditorspanposition-i.md) | Span位置信息。 |
| [RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md) | 文本样式选项。 继承自[RichEditorRange](arkts-arkui-richeditorrange-i.md)。 |
| [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | RichEditor初始化参数。 |
| [RichEditorSymbolSpanOptions](arkts-arkui-richeditorsymbolspanoptions-i.md) | 设置SymbolSpan组件的偏移位置和样式。 |
| [RichEditorSymbolSpanStyle](arkts-arkui-richeditorsymbolspanstyle-i.md) | 组件SymbolSpan样式信息。 |
| [RichEditorSymbolSpanStyleResult](arkts-arkui-richeditorsymbolspanstyleresult-i.md) | 后端返回的SymbolSpan样式信息。 |
| [RichEditorTextSpan](arkts-arkui-richeditortextspan-i.md) | 文本Span信息。 |
| [RichEditorTextSpanOptions](arkts-arkui-richeditortextspanoptions-i.md) | 添加文本的偏移位置和文本样式信息。 |
| [RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md) | 文本Span信息。 |
| [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | 文本样式信息。 |
| [RichEditorTextStyleResult](arkts-arkui-richeditortextstyleresult-i.md) | 后端返回的文本样式信息。 在RichEditorTextStyle中，fontWeight是设置字体粗细的输入参数。 而在RichEditorTextStyleResult中，会将之前设置的字体粗细转换为数字后返回。 RichEditorSymbolSpanStyle和RichEditorSymbolSpanStyleResult中fontWeight的转换关系，与RichEditorTextStyle和 RichEditorTextStyleResult中fontWeight的转换关系一致。 |
| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditorupdateimagespanstyleoptions-i.md) | 图片的样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md)。 |
| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditorupdatesymbolspanstyleoptions-i.md) | SymbolSpan样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md)。 |
| [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditorupdatetextspanstyleoptions-i.md) | 文本样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md)。 |
| [RichEditorUrlStyle](arkts-arkui-richeditorurlstyle-i.md) | Url信息。 |
| [SelectionMenuOptions](arkts-arkui-selectionmenuoptions-i.md) | 菜单的选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [MenuCallback](arkts-arkui-menucallback-t.md) | 自定义选择菜单显示或隐藏时触发的回调事件。 |
| [MenuOnAppearCallback](arkts-arkui-menuonappearcallback-t.md) | 自定义选择菜单弹出时触发的回调事件。 |
| [OnHoverCallback](arkts-arkui-onhovercallback-t.md) | 鼠标悬浮触发回调。 |
| [PasteEventCallback](arkts-arkui-pasteeventcallback-t.md) | 粘贴完成前，触发回调。 |
| [RichEditorSpan](arkts-arkui-richeditorspan-t.md) | RichEditor span信息。 |
| [SubmitCallback](arkts-arkui-submitcallback-t.md) | 软键盘按下回车键时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RichEditorDeleteDirection](arkts-arkui-richeditordeletedirection-e.md) | 删除方向。 |
| [RichEditorResponseType](arkts-arkui-richeditorresponsetype-e.md) | 菜单的响应类型。 |
| [RichEditorSpanType](arkts-arkui-richeditorspantype-e.md) | Span类型信息。 |
| [UndoStyle](arkts-arkui-undostyle-e.md) | 撤销还原是否保留原样式选项。 |

