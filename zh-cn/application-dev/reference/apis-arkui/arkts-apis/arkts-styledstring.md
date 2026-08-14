# styledString

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BackgroundColorStyle](arkts-arkui-styledstring-backgroundcolorstyle-c.md) | 文本背景颜色对象说明。 |
| [BaselineOffsetStyle](arkts-arkui-styledstring-baselineoffsetstyle-c.md) | 文本基线偏移量对象说明。 |
| [CustomSpan](arkts-arkui-styledstring-customspan-c.md) | 自定义绘制Span，仅提供基类，具体实现由开发者定义。 自定义绘制Span拖拽显示的缩略图为空白。 |
| [DecorationStyle](arkts-arkui-styledstring-decorationstyle-c.md) | 文本装饰线样式对象说明。 |
| [GestureStyle](arkts-arkui-styledstring-gesturestyle-c.md) | 事件手势对象说明。 |
| [ImageAttachment](arkts-arkui-styledstring-imageattachment-c.md) | 图片对象说明。 |
| [LeadingMarginSpan](arkts-arkui-styledstring-leadingmarginspan-c.md) | 文本段落的自定义缩进，仅提供基类，具体实现由开发者定义。 |
| [LetterSpacingStyle](arkts-arkui-styledstring-letterspacingstyle-c.md) | 文本字符间距对象说明。 |
| [LineHeightStyle](arkts-arkui-styledstring-lineheightstyle-c.md) | 文本行高对象说明。 |
| [LineSpacingStyle](arkts-arkui-styledstring-linespacingstyle-c.md) | 文本行间距对象说明。 |
| [MutableStyledString](arkts-arkui-styledstring-mutablestyledstring-c.md) | 继承于[StyledString](arkts-arkui-styledstring-styledstring-c.md#StyledString)类。 > **以下接口异常入参处理统一说明：** > > 当start和length越界或者必填传入undefined时，会抛出异常； > > 当styledKey和styledValue传入异常值或者两者对应关系不匹配时，会抛出异常。 |
| [ParagraphStyle](arkts-arkui-styledstring-paragraphstyle-c.md) | 文本段落样式对象说明。 除首个段落外，后续段落按'\n'划分。 每个段落的段落样式按首个占位设置的段落样式生效，未设置时，段落按被绑定组件的段落样式生效。 在API版本26.0.0之前，如果属性字符串段落内首个占位为[CustomSpan](arkts-arkui-styledstring-customspan-c.md#CustomSpan)或[ImageAttachment](arkts-arkui-styledstring-imageattachment-c.md#ImageAttachment)时，设置在该段落上的段落样式不生 效。从API版本26.0.0开始，设置段落样式生效。 |
| [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 属性字符串 |
| [TextShadowStyle](arkts-arkui-styledstring-textshadowstyle-c.md) | 文本阴影对象说明。 |
| [TextStyle](arkts-arkui-styledstring-textstyle-c.md) | 文本字体样式对象说明。 |
| [UrlStyle](arkts-arkui-styledstring-urlstyle-c.md) | 超链接对象说明。 默认颜色、字号、字重分别是'#ff0a59f7'、'16fp'、'FontWeight.Regular'，若属性字符串设置TextStyle，则TextStyle优先级更高。 |
| [UserDataSpan](arkts-arkui-styledstring-userdataspan-c.md) | 支持存储自定义扩展信息，用于存储和获取用户数据，仅提供基类，具体实现由开发者定义。 扩展信息不影响实际显示效果。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-styledstring-c-sys.md) | 属性字符串 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomSpanDrawInfo](arkts-arkui-styledstring-customspandrawinfo-i.md) | 定义CustomSpanDrawInfo接口。 |
| [CustomSpanMeasureInfo](arkts-arkui-styledstring-customspanmeasureinfo-i.md) | 定义CustomSpanMeasureInfo接口。 |
| [CustomSpanMetrics](arkts-arkui-styledstring-customspanmetrics-i.md) | 定义CustomSpanMetrics接口。 |
| [DecorationOptions](arkts-arkui-styledstring-decorationoptions-i.md) | 文本装饰线样式的额外配置选项对象说明。 |
| [DecorationStyleInterface](arkts-arkui-styledstring-decorationstyleinterface-i.md) | 文本装饰线样式接口对象说明。 |
| [GestureStyleInterface](arkts-arkui-styledstring-gesturestyleinterface-i.md) | Defines the Gesture Events. |
| [ImageAttachmentInterface](arkts-arkui-styledstring-imageattachmentinterface-i.md) | Defines the ImageAttachmentInterface. |
| [ImageAttachmentLayoutStyle](arkts-arkui-styledstring-imageattachmentlayoutstyle-i.md) | 定义ImageAttachment布局样式。 |
| [LeadingMarginSpanDrawInfo](arkts-arkui-styledstring-leadingmarginspandrawinfo-i.md) | 自定义绘制信息。 |
| [ParagraphStyleInterface](arkts-arkui-styledstring-paragraphstyleinterface-i.md) | 段落样式 |
| [ResourceImageAttachmentOptions](arkts-arkui-styledstring-resourceimageattachmentoptions-i.md) | ResourceStr类型图片设置项。 |
| [SpanStyle](arkts-arkui-styledstring-spanstyle-i.md) | SpanStyle |
| [StyleOptions](arkts-arkui-styledstring-styleoptions-i.md) | 属性字符串初始化选项。 |
| [TextStyleInterface](arkts-arkui-styledstring-textstyleinterface-i.md) | TextStyleInterface |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StyledStringKey](arkts-arkui-styledstring-styledstringkey-e.md) | 范围属性字符串样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AttachmentType](arkts-arkui-attachmenttype-t.md) | 图片设置项类型，用于设置属性字符串PixelMap类型或[ResourceStr](../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr)类型图片。 |
| [ColorFilterType](arkts-arkui-colorfiltertype-t.md) | 图片颜色滤镜设置项类型。 |
| [StyledStringValue](arkts-arkui-styledstringvalue-t.md) | 样式对象类型，用于设置属性字符串的样式。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StyledStringMarshallCallback](arkts-arkui-styledstringmarshallcallback-t-sys.md) | 属性字符串序列化回调类型。 |
| [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | 属性字符串自定义序列化对象类型，需要开发者定义序列化和反序列化的方式。 |
| [StyledStringUnmarshallCallback](arkts-arkui-styledstringunmarshallcallback-t-sys.md) | 反序列化后得到属性字符串，通过定义回调来反序列化StyledStringMarshallingValue。 |
<!--DelEnd-->

