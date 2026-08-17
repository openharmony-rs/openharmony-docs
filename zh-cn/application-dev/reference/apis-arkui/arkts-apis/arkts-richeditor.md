# richEditor

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md) | RichEditor组件控制器基类。 |
| [RichEditorController](arkts-arkui-richeditor-richeditorcontroller-c.md) | RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md#richeditorbasecontroller)。 |
| [RichEditorStyledStringController](arkts-arkui-richeditor-richeditorstyledstringcontroller-c.md) | 使用属性字符串构建的RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md#richeditorbasecontroller)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CopyEvent](arkts-arkui-richeditor-copyevent-i.md) | 定义用户复制事件。 |
| [CutEvent](arkts-arkui-richeditor-cutevent-i.md) | 定义用户剪切事件。 |
| [KeyboardOptions](arkts-arkui-richeditor-keyboardoptions-i.md) | 设置自定义键盘是否支持避让功能。 |
| [LeadingMarginPlaceholder](arkts-arkui-richeditor-leadingmarginplaceholder-i.md) | 前导边距占位符，用于表示文本段落左侧与组件边缘之间的距离。 |
| [PasteEvent](arkts-arkui-richeditor-pasteevent-i.md) | 定义用户粘贴事件。 |
| [PlaceholderStyle](arkts-arkui-richeditor-placeholderstyle-i.md) | 设置提示文本的字体样式。 |
| [PreviewMenuOptions](arkts-arkui-richeditor-previewmenuoptions-i.md) | 预览菜单的选项。 |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-richeditorbuilderspanoptions-i.md) | 设置builder的偏移位置和样式。 |
| [RichEditorChangeValue](arkts-arkui-richeditor-richeditorchangevalue-i.md) | 图文变化信息。 |
| [RichEditorDeleteValue](arkts-arkui-richeditor-richeditordeletevalue-i.md) | 删除操作和被删除内容的信息。 |
| [RichEditorGesture](arkts-arkui-richeditor-richeditorgesture-i.md) | 用户手势事件。 |
| [RichEditorImageSpan](arkts-arkui-richeditor-richeditorimagespan-i.md) | 图片Span信息。 |
| [RichEditorImageSpanOptions](arkts-arkui-richeditor-richeditorimagespanoptions-i.md) | 设置图片的偏移位置和图片样式信息。 |
| [RichEditorImageSpanResult](arkts-arkui-richeditor-richeditorimagespanresult-i.md) | 后端返回的图片信息。 |
| [RichEditorImageSpanStyle](arkts-arkui-richeditor-richeditorimagespanstyle-i.md) | 图片样式。 |
| [RichEditorImageSpanStyleResult](arkts-arkui-richeditor-richeditorimagespanstyleresult-i.md) | 后端返回的图片样式信息。 |
| [RichEditorInsertValue](arkts-arkui-richeditor-richeditorinsertvalue-i.md) | 插入文本的信息。 |
| [RichEditorLayoutStyle](arkts-arkui-richeditor-richeditorlayoutstyle-i.md) | 图片布局信息。 |
| [RichEditorOptions](arkts-arkui-richeditor-richeditoroptions-i.md) | RichEditor初始化参数。 |
| [RichEditorParagraphResult](arkts-arkui-richeditor-richeditorparagraphresult-i.md) | 后端返回的段落信息。 |
| [RichEditorParagraphStyle](arkts-arkui-richeditor-richeditorparagraphstyle-i.md) | 段落样式。 |
| [RichEditorParagraphStyleOptions](arkts-arkui-richeditor-richeditorparagraphstyleoptions-i.md) | 段落样式选项。 继承自[RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md#richeditorrange)。 |
| [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 定义RichEditor的范围。 |
| [RichEditorSelection](arkts-arkui-richeditor-richeditorselection-i.md) | 选中内容信息。 |
| [RichEditorSpanPosition](arkts-arkui-richeditor-richeditorspanposition-i.md) | Span位置信息。 |
| [RichEditorSpanStyleOptions](arkts-arkui-richeditor-richeditorspanstyleoptions-i.md) | 文本样式选项。 继承自[RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md#richeditorrange)。 |
| [RichEditorStyledStringOptions](arkts-arkui-richeditor-richeditorstyledstringoptions-i.md) | RichEditor初始化参数。 |
| [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-richeditorsymbolspanoptions-i.md) | 设置SymbolSpan组件的偏移位置和样式。 |
| [RichEditorSymbolSpanStyle](arkts-arkui-richeditor-richeditorsymbolspanstyle-i.md) | 组件SymbolSpan样式信息。 |
| [RichEditorSymbolSpanStyleResult](arkts-arkui-richeditor-richeditorsymbolspanstyleresult-i.md) | 后端返回的SymbolSpan样式信息。 |
| [RichEditorTextSpan](arkts-arkui-richeditor-richeditortextspan-i.md) | 文本Span信息。 |
| [RichEditorTextSpanOptions](arkts-arkui-richeditor-richeditortextspanoptions-i.md) | 添加文本的偏移位置和文本样式信息。 |
| [RichEditorTextSpanResult](arkts-arkui-richeditor-richeditortextspanresult-i.md) | 文本Span信息。 |
| [RichEditorTextStyle](arkts-arkui-richeditor-richeditortextstyle-i.md) | 文本样式信息。 |
| [RichEditorTextStyleResult](arkts-arkui-richeditor-richeditortextstyleresult-i.md) | 后端返回的文本样式信息。 在RichEditorTextStyle中，fontWeight是设置字体粗细的输入参数。 而在RichEditorTextStyleResult中，会将之前设置的字体粗细转换为数字后返回。 转换关系如下： \| RichEditorTextStyle中的fontWeight \| RichEditorTextStyleResult中的fontWeight \| \| ---- \| ----------------------------------- \| \| 100 \| 0 \| \| 200 \| 1 \| \| 300 \| 2 \| \| 400 \| 3 \| \| 500 \| 4 \| \| 600 \| 5 \| \| 700 \| 6 \| \| 800 \| 7 \| \| 900 \| 8 \| \| Lighter \| 12 \| \| Normal \| 10 \| \| Regular \| 14 \| \| Medium \| 13 \| \| Bold \| 9 \| \| Bolder \| 11 \| RichEditorSymbolSpanStyle和RichEditorSymbolSpanStyleResult中fontWeight的转换关系，与RichEditorTextStyle和 RichEditorTextStyleResult中fontWeight的转换关系一致。 |
| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditor-richeditorupdateimagespanstyleoptions-i.md) | 图片的样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditor-richeditorspanstyleoptions-i.md#richeditorspanstyleoptions)。 |
| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditor-richeditorupdatesymbolspanstyleoptions-i.md) | SymbolSpan样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditor-richeditorspanstyleoptions-i.md#richeditorspanstyleoptions)。 |
| [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditor-richeditorupdatetextspanstyleoptions-i.md) | 文本样式选项。 继承自[RichEditorSpanStyleOptions](arkts-arkui-richeditor-richeditorspanstyleoptions-i.md#richeditorspanstyleoptions)。 |
| [RichEditorUrlStyle](arkts-arkui-richeditor-richeditorurlstyle-i.md) | Url信息。 |
| [SelectionMenuOptions](arkts-arkui-richeditor-selectionmenuoptions-i.md) | 菜单的选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-richeditorbuilderspanoptions-i-sys.md) | 设置builder的偏移位置和样式。 |
| [RichEditorChangeValue](arkts-arkui-richeditor-richeditorchangevalue-i-sys.md) | 图文变化信息。 |
| [RichEditorGesture](arkts-arkui-richeditor-richeditorgesture-i-sys.md) | 用户手势事件。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RichEditorDeleteDirection](arkts-arkui-richeditor-richeditordeletedirection-e.md) | 删除方向。 |
| [RichEditorResponseType](arkts-arkui-richeditor-richeditorresponsetype-e.md) | 菜单的响应类型。 |
| [RichEditorSpanType](arkts-arkui-richeditor-richeditorspantype-e.md) | Span类型信息。 |
| [UndoStyle](arkts-arkui-richeditor-undostyle-e.md) | 撤销还原是否保留原样式选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [MenuCallback](arkts-arkui-menucallback-t.md) | 自定义选择菜单显示或隐藏时触发的回调事件。 |
| [MenuOnAppearCallback](arkts-arkui-menuonappearcallback-t.md) | 自定义选择菜单弹出时触发的回调事件。 |
| [OnHoverCallback](arkts-arkui-onhovercallback-t.md) | 鼠标悬浮触发回调。 |
| [PasteEventCallback](arkts-arkui-pasteeventcallback-t.md) | 粘贴完成前，触发回调。 |
| [RichEditorSpan](arkts-arkui-richeditorspan-t.md) | RichEditor span信息。 |
| [SubmitCallback](arkts-arkui-submitcallback-t.md) | 软键盘按下回车键时的回调事件。 |

