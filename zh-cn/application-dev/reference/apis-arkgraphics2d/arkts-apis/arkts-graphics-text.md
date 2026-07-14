# @ohos.graphics.text

本模块提供一系列用于文本布局和字体管理的编程接口。文本布局相关的接口旨在提供高质量的排版，包括字符到字形的转换、字距调整、换行、对齐、文本测量等。字体管理接口提供字体注册、字体描述符、字体集管理等功能。

该模块提供以下创建复杂样式的文本段落的常用类：

- [TextStyle](arkts-arkgraphics2d-textstyle-i.md)：文本样式，控制文本的字体类型、大小、间距等属性。
- [FontCollection](arkts-arkgraphics2d-fontcollection-c.md)：字体集，控制各种不同的字体。
- [FontDescriptor](arkts-arkgraphics2d-fontdescriptor-i.md)：字体描述符信息。
- [ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)：段落样式，控制整个段落的断行策略、断词策略等属性。
- [ParagraphBuilder](arkts-arkgraphics2d-paragraphbuilder-c.md)：段落生成器，控制生成不同的段落对象。
- [Paragraph](arkts-arkgraphics2d-paragraph-c.md)：段落，由ParagraphBuilder类调用[build()](arkts-arkgraphics2d-paragraphbuilder-c.md#build-1)接口构建而成。
- [LineTypeset](arkts-arkgraphics2d-linetypeset-c.md)：行排版器，由ParagraphBuilder类调用
[buildLineTypeset()](arkts-arkgraphics2d-paragraphbuilder-c.md#buildlinetypeset-1)接口构建而成。
- [TextLine](arkts-arkgraphics2d-textline-c.md)：以行为单位的段落文本的载体，由Paragraph类调用[getTextLines()](arkts-arkgraphics2d-paragraph-c.md#gettextlines-1)接口获取。
- [Run](arkts-arkgraphics2d-runmetrics-i.md)：文本排版单元，由TextLine类调用[getGlyphRuns()](arkts-arkgraphics2d-textline-c.md#getglyphruns-1)接口获取。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontCount](arkts-arkgraphics2d-getfontcount-f.md#getfontcount-1) | 根据字体文件路径获取包含的字体文件数。如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回0。 |
| [getFontDescriptorByFullName](arkts-arkgraphics2d-getfontdescriptorbyfullname-f.md#getfontdescriptorbyfullname-1) | 根据字体名称和类型获取字体描述符，使用Promise异步回调。字体描述符是描述字体特征的数据结构，包含字体外观和属性的详细信息。 |
| [getFontDescriptorsFromPath](arkts-arkgraphics2d-getfontdescriptorsfrompath-f.md#getfontdescriptorsfrompath-1) | 根据字体文件路径获取字体描述符数组。使用Promise异步回调。@link text.FontDescriptor}中的weight字段并不精准对应字体文件内部的字重数值，而是将字体文件中的实际字重四舍五入映射到&gt; [FontWeight](arkts-arkgraphics2d-fontweight-e.md)枚举值后的结果。例如，字体文件字重350会映射为400，对应枚举为W400。 |
| [getFontPathsByType](arkts-arkgraphics2d-getfontpathsbytype-f.md#getfontpathsbytype-1) | 获取指定字体类型的所有字体文件路径。 |
| [getFontUnicodeSet](arkts-arkgraphics2d-getfontunicodeset-f.md#getfontunicodeset-1) | 根据字体文件路径获取字体unicode数组。使用Promise异步回调。如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回空数组。 |
| [getSystemFontFullNamesByType](arkts-arkgraphics2d-getsystemfontfullnamesbytype-f.md#getsystemfontfullnamesbytype-1) | 根据字体类型返回该类型对应的所有字体的字体名称，使用Promise异步回调。 |
| [isFontSupported](arkts-arkgraphics2d-isfontsupported-f.md#isfontsupported-1) | 检查系统是否支持指定的字体文件。 |
| [matchFontDescriptors](arkts-arkgraphics2d-matchfontdescriptors-f.md#matchfontdescriptors-1) | 根据指定的字体描述符返回所有符合要求的系统字体描述符，使用Promise异步回调。 |
| [setTextHighContrast](arkts-arkgraphics2d-settexthighcontrast-f.md#settexthighcontrast-1) | 用于设置文字渲染高对比度模式。该接口设置后整个进程都会生效，进程内所有页面共用相同模式。可调用此接口设置，也可通过系统设置界面中**高对比度文字配置开关**进行开启/关闭。使用此接口设置开启/关闭文字渲染高对比度配置的优先级高于系统开关设置。该接口针对应用的文字自绘制场景不生效。 |
| [setTextUndefinedGlyphDisplay](arkts-arkgraphics2d-settextundefinedglyphdisplay-f.md#settextundefinedglyphdisplay-1) | 设置字符映射到.notdef（未定义）字形时要使用的字形类型。影响此调用后呈现的所有文本。此配置会影响显示字体中未定义字符的方式：- 默认行为遵循字体的内部.notdef字形设计。- 开启后将强制使缺失字形的字符以豆腐块形式显示。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-fontcollection-c.md) | 字体集。 |
| [LineTypeset](arkts-arkgraphics2d-linetypeset-c.md) | 保存着文本内容以及样式的载体，可以用于计算单行排版信息。下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-paragraphbuilder-c.md)类的[buildLineTypeset()](arkts-arkgraphics2d-paragraphbuilder-c.md#buildlinetypeset-1)接口获取到LineTypeset对象实例，再通过此实例调用对应方法。 |
| [Paragraph](arkts-arkgraphics2d-paragraph-c.md) | 保存文本内容及样式的载体，支持排版与绘制操作。下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-paragraphbuilder-c.md)类的[build()](arkts-arkgraphics2d-paragraphbuilder-c.md#build-1)接口获取到Paragraph对象实例，再通过此实例调用对应方法。 |
| [ParagraphBuilder](arkts-arkgraphics2d-paragraphbuilder-c.md) | 段落生成器。 |
| [Run](arkts-arkgraphics2d-run-c.md) | 文本排版单元。下列API示例中都需先使用[TextLine](arkts-arkgraphics2d-textline-c.md)类的[getGlyphRuns()](arkts-arkgraphics2d-textline-c.md#getglyphruns-1)接口获取Run对象实例，再通过此实例调用对应方法。 |
| [TextLine](arkts-arkgraphics2d-textline-c.md) | 描述段落基础文本行结构的载体。下列API示例中都需先使用[Paragraph](arkts-arkgraphics2d-paragraphstyle-i.md)类的[getTextLines()](arkts-arkgraphics2d-paragraph-c.md#gettextlines-1)接口或者[LineTypeset](arkts-arkgraphics2d-linetypeset-c.md)类的[createLine()](arkts-arkgraphics2d-linetypeset-c.md#createline-1)接口获取到TextLine对象实例，再通过此实例调用对应方法。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Decoration](arkts-arkgraphics2d-decoration-i.md) | 文本装饰线。 |
| [FontDescriptor](arkts-arkgraphics2d-fontdescriptor-i.md) | 字体描述符信息。 |
| [FontFeature](arkts-arkgraphics2d-fontfeature-i.md) | 文本字体特征。 |
| [FontVariation](arkts-arkgraphics2d-fontvariation-i.md) | 可变字体属性。 |
| [FontVariationAxis](arkts-arkgraphics2d-fontvariationaxis-i.md) | 字体可变轴信息。 |
| [FontVariationInstance](arkts-arkgraphics2d-fontvariationinstance-i.md) | 字体可变实例信息，存放预设的可变字体样式信息。 |
| [LineMetrics](arkts-arkgraphics2d-linemetrics-i.md) | 描述文本布局中单行文字的度量信息。 |
| [ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md) | 段落样式。 |
| [PlaceholderSpan](arkts-arkgraphics2d-placeholderspan-i.md) | 描述占位符样式。 |
| [PositionWithAffinity](arkts-arkgraphics2d-positionwithaffinity-i.md) | 位置和亲和度。 |
| [Range](arkts-arkgraphics2d-range-i.md) | 描述左闭右开区间。 |
| [RectStyle](arkts-arkgraphics2d-rectstyle-i.md) | 矩形框样式。 |
| [RunMetrics](arkts-arkgraphics2d-runmetrics-i.md) | 描述文本行中连续文本块的布局信息和度量数据。 |
| [StrutStyle](arkts-arkgraphics2d-strutstyle-i.md) | 支柱样式，用于控制绘制文本的行间距、基线对齐方式以及其他与行高相关的属性，默认不开启。 |
| [TextBox](arkts-arkgraphics2d-textbox-i.md) | 文本矩形区域，表示文本在布局时所占用的矩形空间。 |
| [TextLayoutResult](arkts-arkgraphics2d-textlayoutresult-i.md) | 文本布局结果。 |
| [TextRectSize](arkts-arkgraphics2d-textrectsize-i.md) | 文本矩形尺寸，用于描述文本的矩形宽高属性。值为浮点数，单位为物理像素px。 |
| [TextShadow](arkts-arkgraphics2d-textshadow-i.md) | 字体阴影。 |
| [TextStyle](arkts-arkgraphics2d-textstyle-i.md) | 文本样式。 |
| [TextTab](arkts-arkgraphics2d-texttab-i.md) | 段落风格的文本制表符，储存了对齐方式和位置。 |
| [TypographicBounds](arkts-arkgraphics2d-typographicbounds-i.md) | 文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版边界相同，即与字符本身无关。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Affinity](arkts-arkgraphics2d-affinity-e.md) | 位置亲和度枚举。 |
| [BreakStrategy](arkts-arkgraphics2d-breakstrategy-e.md) | 断行策略枚举。 |
| [EllipsisMode](arkts-arkgraphics2d-ellipsismode-e.md) | 省略号类型枚举。EllipsisMode.START和EllipsisMode.MIDDLE仅在单行超长文本生效。 |
| [FontStyle](arkts-arkgraphics2d-fontstyle-e.md) | 字体样式枚举。 |
| [FontWeight](arkts-arkgraphics2d-fontweight-e.md) | 字重枚举。 |
| [FontWidth](arkts-arkgraphics2d-fontwidth-e.md) | 字体宽度的枚举。 |
| [LineHeightStyle](arkts-arkgraphics2d-lineheightstyle-e.md) | 行高缩放基数枚举。 |
| [PlaceholderAlignment](arkts-arkgraphics2d-placeholderalignment-e.md) | 占位符相对于周围文本的纵向对齐方式。![zh-ch_image_PlaceholderAlignment.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_PlaceholderAlignment.png) |
| [RectHeightStyle](arkts-arkgraphics2d-rectheightstyle-e.md) | 矩形区域高度规格枚举。 |
| [RectWidthStyle](arkts-arkgraphics2d-rectwidthstyle-e.md) | 矩形区域宽度规格枚举。 |
| [TextAlign](arkts-arkgraphics2d-textalign-e.md) | 文本对齐方式枚举。 |
| [TextBadgeType](arkts-arkgraphics2d-textbadgetype-e.md) | 文本上下标枚举。 |
| [TextBaseline](arkts-arkgraphics2d-textbaseline-e.md) | 文本基线类型枚举。 |
| [TextDecorationStyle](arkts-arkgraphics2d-textdecorationstyle-e.md) | 装饰线样式枚举。 |
| [TextDecorationType](arkts-arkgraphics2d-textdecorationtype-e.md) | 装饰线类型枚举。 |
| [TextDirection](arkts-arkgraphics2d-textdirection-e.md) | 文本排版方向枚举。 |
| [TextDisplayState](arkts-arkgraphics2d-textdisplaystate-e.md) | 文本显示状态的枚举。表示文本排版后的原生结果，与外部画布裁切、溢出屏幕等外部显示因素无关。 |
| [TextHeightBehavior](arkts-arkgraphics2d-textheightbehavior-e.md) | 文本高度修饰符模式枚举。 |
| [TextHighContrast](arkts-arkgraphics2d-texthighcontrast-e.md) | 文字渲染高对比度配置类型枚举。 |
| [TextProcessState](arkts-arkgraphics2d-textprocessstate-e.md) | 文本处理状态的枚举。 |
| [TextUndefinedGlyphDisplay](arkts-arkgraphics2d-textundefinedglyphdisplay-e.md) | 文本未定义字形时的显示方式枚举。 |
| [TextVerticalAlign](arkts-arkgraphics2d-textverticalalign-e.md) | 文本垂直对齐方式枚举。 |
| [WordBreak](arkts-arkgraphics2d-wordbreak-e.md) | 断词策略枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemFontType](arkts-arkgraphics2d-systemfonttype-e.md) | 字体类型枚举，通过位或运算可实现组合类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [CaretOffsetsCallback](arkts-arkgraphics2d-caretoffsetscallback-t.md) | 将文本行中每个字符的偏移量和索引值作为参数的回调方法。 |

