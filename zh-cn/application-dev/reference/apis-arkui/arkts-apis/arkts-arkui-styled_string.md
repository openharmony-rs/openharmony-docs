# styled_string

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BackgroundColorStyle](arkts-arkui-backgroundcolorstyle-c.md) | 文本背景颜色对象说明。 |
| [BaselineOffsetStyle](arkts-arkui-baselineoffsetstyle-c.md) | 文本基线偏移量对象说明。适用于需要微调文本垂直位置的场景，例如化学公式、数学表达式中的上下标文本与正常文本的对齐调整。 |
| [CustomSpan](arkts-arkui-customspan-c.md) | 自定义绘制Span，仅提供基类，具体实现由开发者定义。适用于需要在文本流中嵌入自定义绘制内容的场景，例如在文本中绘制自定义图标、进度条、特殊装饰效果等。 |
| [DecorationStyle](arkts-arkui-decorationstyle-c.md) | 文本装饰线样式对象说明。 |
| [GestureStyle](arkts-arkui-gesturestyle-c.md) | 事件手势对象说明。 |
| [ImageAttachment](arkts-arkui-imageattachment-c.md) | 图片对象说明。 |
| [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md) | 文本段落的自定义缩进，仅提供基类，具体实现由开发者定义。适用于需要在段落首行或各行开头绘制自定义标记、图标等内容的场景，例如列表项前的自定义符号、段落首行装饰图案等。 |
| [LetterSpacingStyle](arkts-arkui-letterspacingstyle-c.md) | 文本字符间距对象说明。适用于需要调整字符间距的场景，例如标题文字加宽间距以增强视觉效果、密集文本缩小间距以节省空间等。 |
| [LineHeightStyle](arkts-arkui-lineheightstyle-c.md) | 文本行高对象说明。 |
| [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md) | 文本行间距对象说明。适用于需要调整段落内各行间距的场景，例如提升文本阅读舒适度、调整文档排版密度等。 |
| [MutableStyledString](arkts-arkui-mutablestyledstring-c.md) | 继承于[StyledString](arkts-arkui-styledstring-c.md)类。 |
| [ParagraphStyle](arkts-arkui-paragraphstyle-c.md) | 文本段落样式对象说明。 |
| [StyledString](arkts-arkui-styledstring-c.md) | 属性字符串。 |
| [TextShadowStyle](arkts-arkui-textshadowstyle-c.md) | 文本阴影对象说明。 |
| [TextStyle](arkts-arkui-textstyle-c.md) | 文本字体样式对象说明。 |
| [UrlStyle](arkts-arkui-urlstyle-c.md) | 超链接对象说明。 |
| [UserDataSpan](arkts-arkui-userdataspan-c.md) | 支持存储自定义扩展信息，用于存储和获取用户数据，仅提供基类，具体实现由开发者定义。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-c-sys.md) | 属性字符串。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomSpanDrawInfo](arkts-arkui-customspandrawinfo-i.md) | 定义自定义绘制Span的绘制信息接口。 |
| [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md) | 定义自定义绘制Span的测量信息接口。 |
| [CustomSpanMetrics](arkts-arkui-customspanmetrics-i.md) | 定义自定义绘制Span的尺寸信息接口。 |
| [DecorationOptions](arkts-arkui-decorationoptions-i.md) | 文本装饰线样式的额外配置选项对象说明。 |
| [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | 文本装饰线样式接口对象说明。 |
| [GestureStyleInterface](arkts-arkui-gesturestyleinterface-i.md) | 定义事件手势接口。 |
| [ImageAttachmentInterface](arkts-arkui-imageattachmentinterface-i.md) | 定义图片设置项接口。 |
| [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md) | 定义图片布局样式。 |
| [LeadingMarginSpanDrawInfo](arkts-arkui-leadingmarginspandrawinfo-i.md) | 自定义绘制信息。 |
| [ParagraphStyleInterface](arkts-arkui-paragraphstyleinterface-i.md) | 文本段落样式。 |
| [ResourceImageAttachmentOptions](arkts-arkui-resourceimageattachmentoptions-i.md) | ResourceStr类型图片设置项。 |
| [SpanStyle](arkts-arkui-spanstyle-i.md) | 属性字符串样式。 |
| [StyleOptions](arkts-arkui-styleoptions-i.md) | 属性字符串样式。 |
| [TextStyleInterface](arkts-arkui-textstyleinterface-i.md) | 文本字体样式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StyledStringKey](arkts-arkui-styledstringkey-e.md) | 范围属性字符串样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AttachmentType](arkts-arkui-attachmenttype-t.md) | 图片设置项类型，用于设置属性字符串PixelMap类型或[ResourceStr](arkts-arkui-resourcestr-t.md)类型图片。 |
| [ColorFilterType](arkts-arkui-colorfiltertype-t.md) | 图片颜色滤镜设置项类型。 |
| [StyledStringValue](arkts-arkui-styledstringvalue-t.md) | 样式对象类型，用于设置属性字符串的样式。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StyledStringMarshallCallback](arkts-arkui-styledstringmarshallcallback-t-sys.md) | 属性字符串[StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)序列化回调类型。 |
| [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | 属性字符串自定义序列化对象类型，需要开发者定义序列化和反序列化的方式。 |
| [StyledStringUnmarshallCallback](arkts-arkui-styledstringunmarshallcallback-t-sys.md) | 属性字符串反序列化ArrayBuffer得到[StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md)回调类型。 |
<!--DelEnd-->

## 示例

```TypeScript
### 示例1 (属性字符串序列化和反序列化)

该示例通过marshalling、unmarshalling方法实现了属性字符串序列化和反序列化的功能。


```

```TypeScript
### 示例2 (带UserDataSpan的属性字符串序列化和反序列化)

该示例通过marshalling、unmarshalling函数实现了属性字符串及其UserDataSpan序列化和反序列化的功能。
```

```TypeScript
### 示例1（属性字符串处理）

从API version 12开始，该示例通过[insertString](arkts-arkui-mutablestyledstring-c.md#insertstring)、[removeStyles](arkts-arkui-mutablestyledstring-c.md#removestyles)、[replaceStyle](arkts-arkui-mutablestyledstring-c.md#replacestyle)、[getStyles](arkts-arkui-styledstring-c.md#getstyles)接口实现属性字符串的插入、删除、替换、查看。


```

```TypeScript
### 示例2（设置事件）

从API version 12开始，该示例通过StyleOptions中的styledKey、styledValue接口实现属性字符串绑定事件。


```

```TypeScript
### 示例3（设置文本样式）

从API version 12开始，该示例通过[getStyles](arkts-arkui-styledstring-c.md#getstyles)、[setStyle](arkts-arkui-mutablestyledstring-c.md#setstyle)接口实现属性字符串查询和设置样式。


```

```TypeScript
### 示例4（设置图片）

从API version 12开始，该示例通过ImageAttachment接口实现属性字符串设置图片。


```

```TypeScript
### 示例5（设置文本行高和段落样式）

从API version 12开始，该示例通过LineHeightStyle、ParagraphStyle接口实现属性字符串设置文本行高和段落样式。


```

```TypeScript
### 示例6（设置自定义绘制Span）

从API version 12开始，该示例通过[CustomSpan](arkts-arkui-customspan-c.md)接口和[measureTextSize](../arkts-apis-uicontext-measureutils.md#measuretextsize12)实现属性字符串设置自定义绘制Span。

从API版本26.0.0开始，CustomSpanMeasureInfo新增maxWidth、layoutPolicy属性。


```

```TypeScript
### 示例7（支持存储自定义扩展信息）

从API version 12开始，该示例通过[UserDataSpan](arkts-arkui-userdataspan-c.md)接口实现属性字符串支持存储自定义扩展信息的功能。


```

```TypeScript
### 示例8（设置超链接）

从API version 14开始，该示例通过UrlStyle接口，实现了对属性字符串中超链接设置的支持。


```

```TypeScript
### 示例9 （给图片设置colorFilter）

从API version 15开始，该示例通过给ImageAttachment设置colorFilter实现了给图像设置颜色滤镜效果。


```

```TypeScript
### 示例10（属性字符串的插入、删除、替换）

从API version 12开始，该示例通过[subStyledString](arkts-arkui-styledstring-c.md#substyledstring)、[removeString](arkts-arkui-mutablestyledstring-c.md#removestring)、[removeStyle](arkts-arkui-mutablestyledstring-c.md#removestyle)、[clearStyles](arkts-arkui-mutablestyledstring-c.md#clearstyles)、[replaceStyledString](arkts-arkui-mutablestyledstring-c.md#replacestyledstring)、[insertStyledString](arkts-arkui-mutablestyledstring-c.md#insertstyledstring)接口实现属性字符串的插入、删除、替换。


```

```TypeScript
### 示例11（属性字符串的文本描边）

从API version 20开始，该示例通过TextStyle设置strokeWidth和strokeColor接口实现属性字符串的文本描边。

从API版本26.0.0开始，TextStyle新增strokeJoinStyle接口实现文本拐角描边样式。


```

```TypeScript
### 示例12（fromHtml和toHtml互相转换）

该示例通过[fromHtml](arkts-arkui-styledstring-c.md#fromhtml)（从API version 12开始）、[toHtml](arkts-arkui-styledstring-c.md#tohtml)（从API version 14开始）接口，将HTML中strong、b20+、em20+、i20+、u20+、del20+、s20+、a20+、sub20+、sup20+标签及其style属性中的background-color转换为属性字符串并转回HTML。


```

```TypeScript
### 示例13（多装饰线与加粗装饰线）

从API version 20开始，该示例通过DecorationStyle中设置enableMultiType、thicknessScale接口，实现多装饰线显示与加粗装饰线的效果。


```

```TypeScript
### 示例14（获取以vp为单位的图片尺寸）

从API version 21开始，该示例通过ImageAttachmentInterface实现属性字符串设置图片，并且获取该图片以vp为单位的尺寸。


```

```TypeScript
### 示例15（设置段落自定义缩进）

从API version 22开始，该示例通过LeadingMarginSpan设置段落缩进，并且自定义缩进图案。


```

```TypeScript
### 示例16（使用supportSvg2属性时，SVG图片的显示效果）

从API version 22开始，该示例通过给[ResourceImageAttachmentOptions](arkts-arkui-resourceimageattachmentoptions-i.md)设置supportSvg2属性，使[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md)的[SVG易用性提升](ts-image-svg2-capabilities.md#svg易用性提升)能力生效。


```

```TypeScript
### 示例17（设置字体配置）

该示例通过TextStyleInterface中的[fontConfigs](ts-text-common.md#fontconfigs24对象说明)实现属性字符串的字体配置。

从API version 24开始，TextStyleInterface新增fontConfigs属性。


```

```TypeScript
### 示例18（fromHtml转换）

该示例通过[fromHtml](arkts-arkui-styledstring-c.md#fromhtml)接口，将HTML中<cite>、<dfn>、<small>、<h1>、<h2>、<h3>、<h4>、<h5>、<h6>、<ol>、<ul>、<li>标签转换为属性字符串。

从API版本26.0.0开始，fromHtml新增支持<cite>、<dfn>、<small>、<h1>、<h2>、<h3>、<h4>、<h5>、<h6>、<ol>、<ul>、<li>标签。


```

```TypeScript
### 示例19（设置可变字体的属性）

该示例通过TextStyle的fontVariations属性设置可变字体的属性。

从API版本26.0.0开始，TextStyle新增了fontVariations属性。


```

```TypeScript
### 示例20（设置文本着色器效果）

该示例通过ParagraphStyle中shaderStyle接口实现文本着色效果。

从API版本26.0.0开始，ParagraphStyle新增shaderStyle接口。


```

```TypeScript
### 示例21（设置文本尾部缩进）

该示例通过ParagraphStyle中的tailIndents属性，为属性字符串设置文本尾部缩进。

从API版本26.0.0开始，ParagraphStyle接口新增tailIndents属性。


```

```TypeScript
### 示例22（设置图片拉伸）

该示例通过设置ImageAttachment中的resizable属性，对图片不同方向进行拉伸。

从API版本26.1.0开始，ImageAttachment接口新增resizable属性。
```
