# component/textCommon

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorShaderStyle](textcommon-colorshaderstyle-c.md) | 显示为纯色。ColorShaderStyle继承自[ShaderStyle]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [ContentTransition](textcommon-contenttransition-c.md) | 文本动效基类。 |
| [LinearGradientStyle](textcommon-lineargradientstyle-c.md) | 显示为线性渐变。LinearGradientStyle继承自[ShaderStyle]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [NumericTextTransition](textcommon-numerictexttransition-c.md) | 数字翻牌动效。仅限正整数，不支持小数和负数。不支持渐变色和Text跑马灯模式。不支持选中， \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_属性无效。当文本存在子组件时或通过属性字符串设置 时，数字翻牌失效。 NumericTextTransition继承自[ContentTransition]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [RadialGradientStyle](textcommon-radialgradientstyle-c.md) | 显示为径向渐变。RadialGradientStyle继承自[ShaderStyle]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [ShaderStyle](textcommon-shaderstyle-c.md) | 文本着色器效果基类。 |
| [TextMenuItemId](textcommon-textmenuitemid-c.md) | 自定义菜单项的Id值。用于识别菜单选项，内置菜单项Id值见下列属性表格。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilitySpanOptions](textcommon-accessibilityspanoptions-i.md) | Span的无障碍朗读功能属性。 |
| [CaretStyle](textcommon-caretstyle-i.md) | 光标样式。 |
| [DecorationStyleResult](textcommon-decorationstyleresult-i.md) | 后端返回的文本装饰线样式信息。 |
| [DeleteValue](textcommon-deletevalue-i.md) | 删除内容对象。 |
| [EditMenuOptions](textcommon-editmenuoptions-i.md) | EditMenuOptions |
| [EditableTextChangeValue](textcommon-editabletextchangevalue-i.md) | 文本变化的详细信息，包括预上屏。 |
| [FontConfigs](textcommon-fontconfigs-i.md) | 字体配置项。 |
| [FontSettingOptions](textcommon-fontsettingoptions-i.md) | 字体配置项。 |
| [FontWeightConfigs](textcommon-fontweightconfigs-i.md) | 字体粗细配置项。当传入该配置对象时（包括空对象{}），未显式设置的属性将使用默认值。当传入null或undefined时，不应用默认值，字体粗细行为与父组件文本保持一致。 |
| [IMEClient](textcommon-imeclient-i.md) | 输入控件绑定输入法客户端类型。 |
| [InsertValue](textcommon-insertvalue-i.md) | 插入内容对象。 |
| [LayoutManager](textcommon-layoutmanager-i.md) | 布局管理器对象。 |
| [LineSpacingOptions](textcommon-linespacingoptions-i.md) | 设置文本的行间距，是否仅在行与行之间生效。 |
| [MaxLinesOptions](textcommon-maxlinesoptions-i.md) | 配置TextArea组件，文本超长时的显示效果。 |
| [NumericTextTransitionOptions](textcommon-numerictexttransitionoptions-i.md) | 数字翻牌的参数。 |
| [PositionWithAffinity](textcommon-positionwithaffinity-i.md) | 位置以及亲和度。 |
| [PreviewText](textcommon-previewtext-i.md) | 预上屏信息。 |
| [SelectedDragPreviewStyle](textcommon-selecteddragpreviewstyle-i.md) | 文本拖拽时的背板样式。 |
| [StyledStringChangeValue](textcommon-styledstringchangevalue-i.md) | 属性字符串的文本变化信息。 |
| [StyledStringChangedListener](textcommon-styledstringchangedlistener-i.md) | 属性字符串的文本内容变化监听器。 |
| [StyledStringController](textcommon-styledstringcontroller-i.md) | 定义StyledString控制器。 |
| [TextBaseController](textcommon-textbasecontroller-i.md) | 文本选择控制器。 |
| [TextChangeOptions](textcommon-textchangeoptions-i.md) | 变化前的文本信息，以及变化后的选区范围。 |
| [TextDataDetectorConfig](textcommon-textdatadetectorconfig-i.md) | 文本识别配置项。该配置只支持\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_组件和 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_组件。 |
| [TextEditControllerEx](textcommon-texteditcontrollerex-i.md) | 文本扩展编辑控制器。 继承自[TextBaseController]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [TextLayoutOptions](textcommon-textlayoutoptions-i.md) | 文本布局选项。 |
| [TextMenuItem](textcommon-textmenuitem-i.md) | TextMenuItem |
| [TextMenuOptions](textcommon-textmenuoptions-i.md) | 菜单选项。 |
| [TextRange](textcommon-textrange-i.md) | 文本范围。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyboardAppearanceConfig](textcommon-keyboardappearanceconfig-i-sys.md) | 键盘外观样式属性。 |
| [VoiceButtonOptions](textcommon-voicebuttonoptions-i-sys.md) | 语音按钮选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AutoCapitalizationMode](textcommon-autocapitalizationmode-e.md) | 自动大小写模式类型，只提供接口能力，具体实现以输入法应用为主。 |
| [FlipDirection](textcommon-flipdirection-e.md) | 翻牌方向。默认值为DOWN。 |
| [IncrementalUpdatePolicy](textcommon-incrementalupdatepolicy-e.md) | 文本渲染的增量更新策略。 |
| [KeyboardAppearance](textcommon-keyboardappearance-e.md) | 键盘外观。 |
| [MaxLinesMode](textcommon-maxlinesmode-e.md) | TextArea组件在文本超长时显示效果。默认值为CLIP，按最大行截断显示。 |
| [MenuType](textcommon-menutype-e.md) | 菜单类型。 |
| [StrokeJoinStyle](textcommon-strokejoinstyle-e.md) | 定义线条拐角的样式，即在绘制折线时线段拐角处的画笔样式。 |
| [SuperscriptStyle](textcommon-superscriptstyle-e.md) | 定义文本上下角标样式。 |
| [TextContentAlign](textcommon-textcontentalign-e.md) | 文本内容区垂直对齐方向。 |
| [TextDataDetectorType](textcommon-textdatadetectortype-e.md) | 文本识别实体类型。 |
| [TextDeleteDirection](textcommon-textdeletedirection-e.md) | 定义删除文本方向。 |
| [TextDirection](textcommon-textdirection-e.md) | 文本排版方向。 |
| [TextMenuShowMode](textcommon-textmenushowmode-e.md) | 菜单的显示模式。 |
| [TextVerticalAlign](textcommon-textverticalalign-e.md) | 文本垂直对齐的方式。默认值BASELINE，沿基线对齐。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyboardFluidLightMode](textcommon-keyboardfluidlightmode-e-sys.md) | 键盘流光效果。 |
| [KeyboardGradientMode](textcommon-keyboardgradientmode-e-sys.md) | 键盘渐变模糊效果。 |
| [TextChangeReason](textcommon-textchangereason-e-sys.md) | 组件内容变化原因。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Affinity](arkts-arkui-affinity-t.md) | 位置亲和度枚举。 |
| [EditableTextOnChangeCallback](arkts-arkui-editabletextonchangecallback-t.md) | 输入内容发生变化时，触发该回调。 |
| [FontVariation](arkts-arkui-fontvariation-t.md) | 可变字体的属性。 |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | 用于描述文本布局中单行文字的度量信息。 |
| [OnCreateMenuCallback](arkts-arkui-oncreatemenucallback-t.md) | 在菜单创建时触发该回调，可在该回调中进行菜单数据设置。入参和返回值只包含一级菜单项，不包含二级菜单项。 |
| [OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md) | 文本变换后回调。 |
| [OnMenuItemClickCallback](arkts-arkui-onmenuitemclickcallback-t.md) | 菜单项功能函数。 |
| [OnPrepareMenuCallback](arkts-arkui-onpreparemenucallback-t.md) | 当文本选择区域变化后显示菜单之前触发该回调，可在该回调中进行菜单数据设置。入参和返回值只包含一级菜单项，不包含二级菜单项。 |
| [Paragraph](arkts-arkui-paragraph-t.md) | 保存文本内容及样式的载体，支持排版与绘制操作。 |
| [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | 矩形区域高度规格枚举。 |
| [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | 矩形区域宽度规格枚举。 |
| [TextBox](arkts-arkui-textbox-t.md) | 文本矩形区域。 |

