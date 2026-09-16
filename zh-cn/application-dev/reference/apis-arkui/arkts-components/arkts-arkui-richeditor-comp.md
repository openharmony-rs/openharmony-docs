# RichEditor

支持图文混排和文本交互式编辑的组件。

> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

不包含子组件。

## RichEditor

```TypeScript
RichEditor(value: RichEditorOptions)
```

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | 是 | 富文本组件初始化选项。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md) | 定义**RichEditor**中BuilderSpan的身份与位置信息。 |
| [CopyEvent](arkts-arkui-copyevent-i.md) | 定义用户复制事件。 |
| [CutEvent](arkts-arkui-cutevent-i.md) | 定义用户剪切事件。 |
| [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | 设置自定义键盘是否支持避让功能。 |
| [LeadingMarginPlaceholder](arkts-arkui-leadingmarginplaceholder-i.md) | 前导边距占位符，用于表示文本段落左侧与组件边缘之间的距离。 |
| [PasteEvent](arkts-arkui-pasteevent-i.md) | 定义用户粘贴事件。 |
| [PlaceholderStyle](arkts-arkui-placeholderstyle-i.md) | 设置提示文本的字体样式。 |
| [PreviewMenuOptions](arkts-arkui-previewmenuoptions-i.md) | 预览菜单的选项。 |
| [RichEditorBuilderSpan](arkts-arkui-richeditorbuilderspan-i.md) | 定义**RichEditor**的BuilderSpan对象，提供身份识别与生命周期感知能力。 |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md) | 设置builder插入的偏移位置和样式。 |
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
| [RichEditorParagraphStyleOptions](arkts-arkui-richeditorparagraphstyleoptions-i.md) | 段落样式选项。 |
| [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 定义RichEditor的范围。 |
| [RichEditorSelection](arkts-arkui-richeditorselection-i.md) | 选中内容信息。 |
| [RichEditorSpanPosition](arkts-arkui-richeditorspanposition-i.md) | Span位置信息。 |
| [RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md) | 文本样式选项。 |
| [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | RichEditor初始化参数。 |
| [RichEditorSymbolSpanOptions](arkts-arkui-richeditorsymbolspanoptions-i.md) | 设置SymbolSpan组件的偏移位置和样式。 |
| [RichEditorSymbolSpanStyle](arkts-arkui-richeditorsymbolspanstyle-i.md) | 组件SymbolSpan样式信息。 |
| [RichEditorSymbolSpanStyleResult](arkts-arkui-richeditorsymbolspanstyleresult-i.md) | 后端返回的SymbolSpan样式信息。 |
| [RichEditorTextSpan](arkts-arkui-richeditortextspan-i.md) | 文本Span信息。 |
| [RichEditorTextSpanOptions](arkts-arkui-richeditortextspanoptions-i.md) | 添加文本的偏移位置和文本样式信息。 |
| [RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md) | 文本Span信息。 |
| [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | 文本样式信息。 |
| [RichEditorTextStyleResult](arkts-arkui-richeditortextstyleresult-i.md) | 后端返回的文本样式信息。 |
| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditorupdateimagespanstyleoptions-i.md) | 图片的样式选项。 |
| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditorupdatesymbolspanstyleoptions-i.md) | SymbolSpan样式选项。 |
| [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditorupdatetextspanstyleoptions-i.md) | 文本样式选项。 |
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

## 示例

```TypeScript
### 示例1（更新文本样式）

通过[updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle)接口更新已有文本样式，更改样式后，使用[getSpans](arkts-arkui-richeditorcontroller-c.md#getspans)获取文本新的样式信息。


```

```TypeScript
### 示例2（绑定自定义键盘）

通过[customKeyboard](#customkeyboard)给组件绑定自定义键盘。


```

```TypeScript
### 示例3（绑定自定义菜单）

通过[bindSelectionMenu](#bindselectionmenu)给组件绑定自定义菜单。

示例中的粘贴菜单项涉及读取剪贴板数据，因此需按规范[申请访问剪贴板权限](../../../basic-services/pasteboard/get-pastedata-permission-guidelines.md)。

> 说明：
> 
> 系统暂未预置加粗、斜体等图标，示例代码使用系统默认图标，开发者使用时需自行替换icons中的资源。


```

```TypeScript
### 示例4（更新图片样式）

通过[updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle)接口更新图片样式。


```

```TypeScript
### 示例5（Span绑定手势事件）

为Span绑定[gesture](arkts-arkui-richeditorgesture-i.md)回调。


```

```TypeScript
### 示例6（更新和获取段落样式）

通过[updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle)接口更新段落样式，通过[getParagraphs](#getparagraphs11)接口获取指定范围段落的信息。


```

```TypeScript
### 示例7（更新预设样式与缩进）

通过[setTypingStyle](arkts-arkui-richeditorbasecontroller-c.md#settypingstyle)接口更新文本预设样式，通过[updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle)接口设置段落缩进。


```

```TypeScript
### 示例8（设置文本字重与阴影）

通过[updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle)接口设置文本字重与阴影。


```

```TypeScript
### 示例9（添加用户自定义布局Span）

通过[addBuilderSpan](arkts-arkui-richeditorcontroller-c.md#addbuilderspan)接口添加用户自定义布局Span。


```

```TypeScript
### 示例10（使用和管理组件内的BuilderSpan）

通过[addBuilderSpan](arkts-arkui-richeditorcontroller-c.md#addbuilderspan)接口添加的自定义布局Span，[getSpans](arkts-arkui-richeditorcontroller-c.md#getspans)、[onWillChange](#onwillchange12)等API不会返回BuilderSpan内部的信息。开发者需要自行维护BuilderSpan的状态，并且在组件内容发生变化时同步更新。


```

```TypeScript
### 示例11（设置文本识别配置）

设置[enableDataDetector](#enabledatadetector11)为true时，通过[dataDetectorConfig](#datadetectorconfig11)接口设置文本识别配置。
```

```TypeScript
### 示例12（设置光标、手柄和高亮颜色）

通过[caretColor](#caretcolor12)属性设置输入框光标、手柄颜色，通过[selectedBackgroundColor](#selectedbackgroundcolor12)属性设置文本选中高亮颜色。


```

```TypeScript
### 示例13（设置行高和字符间距）

通过[updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle)接口配置文本行高（[lineHeight](arkts-arkui-richeditortextstyle-i.md)）和字符间距（[letterSpacing](arkts-arkui-richeditortextstyle-i.md)）。


```

```TypeScript
### 示例14（自定义粘贴事件）

为组件添加[onPaste](#onpaste11)事件，通过[PasteEvent](arkts-arkui-pasteevent-i.md)自定义用户粘贴事件。


```

```TypeScript
### 示例15（配置文字特性效果）

该示例通过[addTextSpan](arkts-arkui-richeditorcontroller-c.md#addtextspan)接口设置文字特性效果（[fontFeature](arkts-arkui-richeditortextstyle-i.md)）。当添加“ss01”特性的FontFeature属性时，数字“0”由原来的椭圆形改变为带有倒圆角形。同时通过[RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md)的strokeJoinStyle接口设置文本描边拐角样式。

从API版本26.0.0开始，[RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md)新增strokeJoinStyle接口。


```

```TypeScript
### 示例16（自定义键盘避让）

通过[customKeyboard](#customkeyboard)属性绑定自定义键盘，通过参数[KeyboardOptions](arkts-arkui-keyboardoptions-i.md)设置自定义键盘是否支持避让功能。


```

```TypeScript
### 示例17（查看编辑状态）

通过[isEditing](#isediting12)接口获取当前富文本的编辑状态。为组件添加[onEditingChange](arkts-arkui-richeditor-comp-attribute.md#oneditingchange)事件，可通过打印日志，获取当前组件是否在编辑态。


```

```TypeScript
### 示例18（配置文本变化回调）

为组件添加[onWillChange](#onwillchange12)事件，能够在组件执行增删操作前，触发回调。


```

```TypeScript
### 示例19（配置输入法回车键功能）

通过[enterKeyType](#enterkeytype12)属性设置软键盘输入法回车键类型。


```

```TypeScript
### 示例20（设置段落折行规则）

通过[updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle)接口设置折行类型（[lineBreakStrategy](arkts-arkui-richeditorparagraphstyle-i.md)），通过[getParagraphs](#getparagraphs11)接口获取当前段落的折行类型。


```

```TypeScript
### 示例21（属性字符串基本功能）

从API version 20开始，该示例中[属性字符串](./ts-universal-styled-string.md)通过[RichEditorStyledStringController](arkts-arkui-richeditorstyledstringcontroller-c.md)中的[setStyledString](#setstyledstring12)方法与RichEditor组件绑定。通过[getStyledString](#getstyledstring12)接口获取富文本组件显示的属性字符串。


```

```TypeScript
### 示例22（获取布局信息）

通过[getLayoutManager](#getlayoutmanager12)接口获取布局管理器对象，通过[getLineCount](ts-text-common.md#getlinecount12)接口获取组件内容或[placeholder](#placeholder12)的总行数，通过[getGlyphPositionAtCoordinate](ts-text-common.md#getglyphpositionatcoordinate12)接口获取较为接近给定坐标的字形的位置信息，通过[getLineMetrics](ts-text-common.md#getlinemetrics12)接口获取指定行的行信息、文本样式信息、以及字体属性信息。


```

```TypeScript
### 示例23（设置系统默认菜单扩展项）

从API version 20开始，该示例通过[editMenuOptions](#editmenuoptions12)属性设置系统默认菜单的扩展项，允许配置扩展项的文本内容、图标和回调方法。


```

```TypeScript
### 示例24（组件部分常用属性）

从API version 18开始，该示例通过[barState](#barstate13)属性设置组件滚动条的显示模式。通过[enableKeyboardOnFocus](#enablekeyboardonfocus12)属性设置组件通过点击以外的方式获焦时，是否主动拉起软键盘。通过[enableHapticFeedback](#enablehapticfeedback13)属性设置组件是否支持触感反馈。通过[getPreviewText](#getpreviewtext12)接口获取组件预上屏信息。通过[stopBackPress](#stopbackpress18)属性设置是否阻止返回键向其他组件或应用侧传递。从API version 21开始，该示例通过[scrollBarColor](#scrollbarcolor21)属性设置RichEditor组件滚动条颜色。


```

```TypeScript
### 示例25（获取光标相对组件位置的矩形）

从API version 18开始，该示例通过RichEditorBaseController的[getCaretRect](arkts-arkui-richeditorbasecontroller-c.md#getcaretrect)方法来获取当前光标相对于组件位置的Rect。


```

```TypeScript
### 示例26（设置最大行数和最大字符数）

从API version 18开始，该示例通过[maxLength](#maxlength18)设置可输入的最大字符数，通过[maxLines](#maxlines18)设置可输入的最大行数。


```

```TypeScript
### 示例27（文本设置Url样式）

从API version 19开始，该示例通过在addTextSpan和UpdateSpanStyle接口中加入[UrlStyle](arkts-arkui-richeditorurlstyle-i.md)，来实现文本点击时跳转到指定链接的功能。


```

```TypeScript
### 示例28（开启带样式的撤销还原能力）

从API version 20开始，该示例对于不使用属性字符串的富文本组件，可以通过配置[undoStyle](#undostyle20)属性为UndoStyle.KEEP_STYLE，以支持撤销还原时保留原内容的样式。


```

```TypeScript
### 示例29（文本设置预设段落样式）

从API version 20开始，该示例通过[setTypingParagraphStyle](arkts-arkui-richeditorbasecontroller-c.md#settypingparagraphstyle)接口设置预设段落样式。


```

```TypeScript
### 示例30（设置装饰线粗细和多装饰线）

从API version 20开始，该示例通过[DecorationStyle](ts-universal-styled-string.md#decorationstyle)中的thicknessScale设置装饰线粗细，通过[enableMultiType](ts-universal-styled-string.md#decorationoptions20)设置多装饰线。


```

```TypeScript
### 示例31（设置开启中西文自动间距）

从API version 20开始，该示例通过[enableAutoSpacing](#enableautospacing20)属性设置中西文自动间距。


```

```TypeScript
### 示例32（设置文本选择的AI菜单）

从API version 22开始，该示例通过[enableSelectedDataDetector](#enableselecteddatadetector22)，配置文本选择AI菜单功能。
```

```TypeScript
### 示例33（设置监听输入法绑定事件）

从API version 22开始，该示例通过[onWillAttachIME](#onwillattachime22)事件监听输入法绑定事件。


```

```TypeScript
### 示例34（删除输入框文本尾部字符）

从API version 23开始，该示例通过[deleteBackward](#deletebackward23)事件在编辑态用自定义键盘删除光标前字符。


```

```TypeScript
### 示例35（优化小语种文字显示）

该示例通过[includeFontPadding](#includefontpadding23)属性，在首行文字顶部和尾行文字底部添加文字内边距，同时通过[fallbackLineSpacing](#fallbacklinespacing23)属性实现行高自适应，基于文字实际高度动态调整。

从API version 23开始，新增includeFontPadding、fallbackLineSpacing属性。


```

```TypeScript
### 示例36（设置行首标点符号压缩和行尾标点符号悬挂）

本示例通过[compressLeadingPunctuation](#compressleadingpunctuation23)设置行首标点符号压缩，通过[punctuationOverflow](#punctuationoverflow)设置行尾标点符号悬挂。

文本自动换行后，剩余内容（含标点符号）需能放入上一行，标点符号悬挂才生效。

从API version 23开始，新增compressLeadingPunctuation接口。

从API版本26.0.0开始，新增punctuationOverflow接口。


```

```TypeScript
### 示例37（设置拖动预览样式）

该示例通过[selectedDragPreviewStyle](#selecteddragpreviewstyle23)接口设置拖动预览样式。

从API version 23开始，新增selectedDragPreviewStyle接口。


```

```TypeScript
### 示例38（设置单行模式）

该示例通过[singleLine](arkts-arkui-richeditor-comp-attribute.md#singleline)接口设置单行模式。

从API version 23开始，新增singleLine接口。


```

```TypeScript
### 示例39（设置属性字符串样式的提示文本）

该示例通过[setStyledPlaceholder](#setstyledplaceholder24)接口设置属性字符串样式的提示文本。

从API version 24开始，新增setStyledPlaceholder接口。


```

```TypeScript
### 示例40（设置孤立字符不成行）

该示例通过[orphanCharOptimization](#orphancharoptimization)接口启用孤字优化，确保段落最后一行不出现孤字。

从API版本26.0.0开始，新增orphanCharOptimization接口。


```

```TypeScript
### 示例41（设置水平滚动）

本示例通过[horizontalScrolling](#horizontalscrolling)设置水平滚动。

从API版本26.0.0开始，新增horizontalScrolling接口。


```

```TypeScript
### 示例42（设置文本着色器效果）

该示例通过[RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md)中shaderStyle接口实现文本着色效果。

从API版本26.0.0开始，RichEditorParagraphStyle新增shaderStyle接口。


```

```TypeScript
### 示例43（将指定范围的文字滚动到可视区内）

本示例通过[scrollToVisible](#scrolltovisible)将可视区外的文本滚动到可视区内。

从API版本26.0.0开始，新增scrollToVisible接口。


```

```TypeScript
### 示例44（设置图片拉伸）

该示例通过设置[RichEditorImageSpanStyle](arkts-arkui-richeditorimagespanstyle-i.md)的resizable属性，对图片不同方向进行拉伸。

从API版本26.1.0开始，RichEditorImageSpanStyle新增resizable属性。
```
