# text_common

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorShaderStyle](arkts-arkui-colorshaderstyle-c.md) | 显示为纯色。ColorShaderStyle继承自[ShaderStyle](arkts-arkui-shaderstyle-c.md)。 |
| [ContentTransition](arkts-arkui-contenttransition-c.md) | 文本动效基类。 |
| [LinearGradientStyle](arkts-arkui-lineargradientstyle-c.md) | 显示为线性渐变。LinearGradientStyle继承自[ShaderStyle](arkts-arkui-shaderstyle-c.md)。 |
| [NumericTextTransition](arkts-arkui-numerictexttransition-c.md) | 数字翻牌动效。仅限正整数，不支持小数和负数。不支持渐变色和Text跑马灯模式。不支持选中，[copyOption](TextAttribute#copyOption)属性无效。当文本存在子组件时或通过属性字符串设置时，数字翻牌失效。  NumericTextTransition继承自[ContentTransition](arkts-arkui-contenttransition-c.md)。 |
| [RadialGradientStyle](arkts-arkui-radialgradientstyle-c.md) | 显示为径向渐变。RadialGradientStyle继承自[ShaderStyle](arkts-arkui-shaderstyle-c.md)。 |
| [ShaderStyle](arkts-arkui-shaderstyle-c.md) | 文本着色器效果基类。 |
| [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | 自定义菜单项的Id值。用于识别菜单选项，内置菜单项Id值见下列属性表格。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilitySpanOptions](arkts-arkui-accessibilityspanoptions-i.md) | Span的无障碍朗读功能属性。 |
| [CaretStyle](arkts-arkui-caretstyle-i.md) | 定义光标样式。 |
| [DecorationStyleResult](arkts-arkui-decorationstyleresult-i.md) | 后端返回的文本装饰线样式信息。 |
| [DeleteValue](arkts-arkui-deletevalue-i.md) | 提供从文本中删除值的接口。 |
| [EditMenuOptions](arkts-arkui-editmenuoptions-i.md) | 编辑菜单选项 |
| [EditableTextChangeValue](arkts-arkui-editabletextchangevalue-i.md) | 文本变化的详细信息，包括预上屏。 |
| [FontConfigs](arkts-arkui-fontconfigs-i.md) | 字体配置项。 |
| [FontSettingOptions](arkts-arkui-fontsettingoptions-i.md) | 字体配置项。 |
| [FontWeightConfigs](arkts-arkui-fontweightconfigs-i.md) | 字体粗细配置项。当传入该配置对象时（包括空对象{}），未显式设置的属性将使用默认值。当传入null或undefined时，不应用默认值，字体粗细行为与父组件文本保持一致。 |
| [IMEClient](arkts-arkui-imeclient-i.md) | 输入控件绑定输入法客户端类型。 |
| [InsertValue](arkts-arkui-insertvalue-i.md) | 定义插入的文本值信息。 |
| [LayoutManager](arkts-arkui-layoutmanager-i.md) | 布局管理器对象。 |
| [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | 设置文本的行间距，是否仅在行与行之间生效。 |
| [MaxLinesOptions](arkts-arkui-maxlinesoptions-i.md) | 配置TextArea组件，文本超长时的显示效果。 |
| [NumericTextTransitionOptions](arkts-arkui-numerictexttransitionoptions-i.md) | 数字翻牌的参数。 |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) | 位置以及亲和度。 |
| [PreviewText](arkts-arkui-previewtext-i.md) | 预上屏信息。 |
| [SelectedDragPreviewStyle](arkts-arkui-selecteddragpreviewstyle-i.md) | 文本拖拽时的背板样式。 |
| [StyledStringChangeValue](arkts-arkui-styledstringchangevalue-i.md) | 属性字符串的文本变化信息。 |
| [StyledStringChangedListener](arkts-arkui-styledstringchangedlistener-i.md) | 属性字符串的文本内容变化监听器。 |
| [StyledStringController](arkts-arkui-styledstringcontroller-i.md) | 定义StyledString控制器。 |
| [TextBaseController](arkts-arkui-textbasecontroller-i.md) | 文本选择控制器。 |
| [TextChangeOptions](arkts-arkui-textchangeoptions-i.md) | 变化前的文本信息，以及变化后的选区范围。 |
| [TextDataDetectorConfig](arkts-arkui-textdatadetectorconfig-i.md) | 该配置只支持[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)组件和[RichEditor](../arkts-components/arkts-arkui-richeditor.md)组件。 |
| [TextEditControllerEx](arkts-arkui-texteditcontrollerex-i.md) | 文本扩展编辑控制器。  继承自[TextBaseController](arkts-arkui-textbasecontroller-i.md)。 |
| [TextLayoutOptions](arkts-arkui-textlayoutoptions-i.md) | 文本布局选项。 |
| [TextMenuItem](arkts-arkui-textmenuitem-i.md) | 文本菜单项 |
| [TextMenuOptions](arkts-arkui-textmenuoptions-i.md) | 菜单选项。 |
| [TextRange](arkts-arkui-textrange-i.md) | 文本范围。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyboardAppearanceConfig](arkts-arkui-keyboardappearanceconfig-i-sys.md) | 键盘外观样式属性。 |
| [VoiceButtonOptions](arkts-arkui-voicebuttonoptions-i-sys.md) | 语音按钮选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AutoCapitalizationMode](arkts-arkui-autocapitalizationmode-e.md) | 自动大小写模式类型，只提供接口能力，具体实现以输入法应用为主。 |
| [FlipDirection](arkts-arkui-flipdirection-e.md) | 翻牌方向。默认值为DOWN。 |
| [IncrementalUpdatePolicy](arkts-arkui-incrementalupdatepolicy-e.md) | 文本渲染的增量更新策略。 |
| [KeyboardAppearance](arkts-arkui-keyboardappearance-e.md) | 键盘外观。 |
| [MaxLinesMode](arkts-arkui-maxlinesmode-e.md) | TextArea组件在文本超长时显示效果。默认值为CLIP，按最大行截断显示。 |
| [MenuType](arkts-arkui-menutype-e.md) | 菜单类型。 |
| [StrokeJoinStyle](arkts-arkui-strokejoinstyle-e.md) | 定义线条拐角的样式，即在绘制折线时线段拐角处的画笔样式。 |
| [SuperscriptStyle](arkts-arkui-superscriptstyle-e.md) | 定义文本上下角标样式。 |
| [TextContentAlign](arkts-arkui-textcontentalign-e.md) | 文本内容区垂直对齐方向。 |
| [TextDataDetectorType](arkts-arkui-textdatadetectortype-e.md) | 定义文本数据检测类型。 |
| [TextDeleteDirection](arkts-arkui-textdeletedirection-e.md) | 定义删除文本方向。 |
| [TextDirection](arkts-arkui-textdirection-e.md) | 文本排版方向。 |
| [TextMenuShowMode](arkts-arkui-textmenushowmode-e.md) | 菜单的显示模式。 |
| [TextVerticalAlign](arkts-arkui-textverticalalign-e.md) | 文本垂直对齐的方式。默认值BASELINE，沿基线对齐。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyboardFluidLightMode](arkts-arkui-keyboardfluidlightmode-e-sys.md) | 键盘流光效果。 |
| [KeyboardGradientMode](arkts-arkui-keyboardgradientmode-e-sys.md) | 键盘模糊效果。 |
| [TextChangeReason](arkts-arkui-textchangereason-e-sys.md) | 组件内容变化原因。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Affinity](arkts-arkui-affinity-t.md) | 位置亲和度枚举。 |
| [EditableTextOnChangeCallback](arkts-arkui-editabletextonchangecallback-t.md) | 输入内容发生变化时，触发该回调。 |
| [FontVariation](arkts-arkui-fontvariation-t.md) | 可变字体的属性。 |
| [InputMethodExtraConfig](arkts-arkui-inputmethodextraconfig-t.md) | 输入法扩展信息。 |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | 用于描述文本布局中单行文字的度量信息。 |
| [OnCreateMenuCallback](arkts-arkui-oncreatemenucallback-t.md) | 菜单创建时触发。 |
| [OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md) | 文本变换后回调。 |
| [OnPrepareMenuCallback](arkts-arkui-onpreparemenucallback-t.md) | 当文本选择区域变化后显示菜单之前触发该回调，可在该回调中进行菜单数据设置。入参和返回值只包含一级菜单项，不包含二级菜单项。 |
| [Paragraph](arkts-arkui-paragraph-t.md) | 保存文本内容及样式的载体，支持排版与绘制操作。 |
| [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | 矩形区域高度规格枚举。 |
| [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | 矩形区域宽度规格枚举。 |
| [TextBox](arkts-arkui-textbox-t.md) | 文本矩形区域。 |

