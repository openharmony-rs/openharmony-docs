# @ohos.graphics.text

本模块提供一系列用于文本布局和字体管理的编程接口。文本布局相关的接口旨在提供高质量的排版，包括字符到字形的转换、字距调整、换行、对齐、文本测量等。字体管理接口提供字体注册、字体描述符、字体集管理等功能。

该模块提供以下创建复杂样式的文本段落的常用类：

- [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md#TextStyle)：文本样式，控制文本的字体类型、大小、间距等属性。
- [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md#FontCollection)：字体集，控制各种不同的字体。
- [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md#FontDescriptor)：字体描述符信息。
- [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md#ParagraphStyle)：段落样式，控制整个段落的断行策略、断词策略等属性。
- [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md#ParagraphBuilder)：段落生成器，控制生成不同的段落对象。
- [Paragraph](arkts-arkgraphics2d-text-paragraph-c.md#Paragraph)：段落，由ParagraphBuilder类调用[build()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#build-1)接口构建而成。
- [LineTypeset](arkts-arkgraphics2d-text-linetypeset-c.md#LineTypeset)：行排版器，由ParagraphBuilder类调用
[buildLineTypeset()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#buildLineTypeset-1)接口构建而成。
- [TextLine](arkts-arkgraphics2d-text-textline-c.md#TextLine)：以行为单位的段落文本的载体，由Paragraph类调用[getTextLines()](arkts-arkgraphics2d-text-paragraph-c.md#getTextLines-1)接口获取。
- [Run](arkts-arkgraphics2d-text-runmetrics-i.md#RunMetrics)：文本排版单元，由TextLine类调用[getGlyphRuns()](arkts-arkgraphics2d-text-textline-c.md#getGlyphRuns-1)接口获取。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontCount](arkts-arkgraphics2d-text-getfontcount-f.md#getFontCount-1) | 根据字体文件路径获取包含的字体文件数。<br/><br/>如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回0。<br/> |
| [getFontDescriptorByFullName](arkts-arkgraphics2d-text-getfontdescriptorbyfullname-f.md#getFontDescriptorByFullName-1) | 根据字体名称和类型获取字体描述符，使用Promise异步回调。<br/><br/>字体描述符是描述字体特征的数据结构，包含字体外观和属性的详细信息。<br/> |
| [getFontDescriptorsFromPath](arkts-arkgraphics2d-text-getfontdescriptorsfrompath-f.md#getFontDescriptorsFromPath-1) | 根据字体文件路径获取字体描述符数组。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回空数组。<br/>&gt;<br/>&gt; - [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md#FontDescriptor)中的weight字段并不精准对应字体文件内部的字重数值，而是将字体文件中的实际字重四舍五入映射到<br/>&gt; [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md#FontWeight)枚举值后的结果。例如，字体文件字重350会映射为400，对应枚举为W400。<br/> |
| [getFontPathsByType](arkts-arkgraphics2d-text-getfontpathsbytype-f.md#getFontPathsByType-1) | 获取指定字体类型的所有字体文件路径。<br/> |
| [getFontUnicodeSet](arkts-arkgraphics2d-text-getfontunicodeset-f.md#getFontUnicodeSet-1) | 根据字体文件路径获取字体unicode数组。使用Promise异步回调。<br/><br/>如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回空数组。<br/> |
| [getSystemFontFullNamesByType](arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md#getSystemFontFullNamesByType-1) | 根据字体类型返回该类型对应的所有字体的字体名称，使用Promise异步回调。<br/> |
| [isFontSupported](arkts-arkgraphics2d-text-isfontsupported-f.md#isFontSupported-1) | 检查系统是否支持指定的字体文件。<br/> |
| [matchFontDescriptors](arkts-arkgraphics2d-text-matchfontdescriptors-f.md#matchFontDescriptors-1) | 根据指定的字体描述符返回所有符合要求的系统字体描述符，使用Promise异步回调。<br/> |
| [setTextHighContrast](arkts-arkgraphics2d-text-settexthighcontrast-f.md#setTextHighContrast-1) | 用于设置文字渲染高对比度模式。<br/><br/>该接口设置后整个进程都会生效，进程内所有页面共用相同模式。<br/><br/>可调用此接口设置，也可通过系统设置界面中**高对比度文字配置开关**进行开启/关闭。使用此接口设置开启/关闭文字渲染高对比度配置的优先级高于系统开关设置。<br/><br/>该接口针对应用的文字自绘制场景不生效。<br/> |
| [setTextUndefinedGlyphDisplay](arkts-arkgraphics2d-text-settextundefinedglyphdisplay-f.md#setTextUndefinedGlyphDisplay-1) | 设置字符映射到.notdef（未定义）字形时要使用的字形类型。<br/><br/>影响此调用后呈现的所有文本。<br/><br/>此配置会影响显示字体中未定义字符的方式：<br/><br/>- 默认行为遵循字体的内部.notdef字形设计。<br/>- 开启后将强制使缺失字形的字符以豆腐块形式显示。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | 字体集。<br/> |
| [LineTypeset](arkts-arkgraphics2d-text-linetypeset-c.md) | 保存着文本内容以及样式的载体，可以用于计算单行排版信息。<br/><br/>下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md#ParagraphBuilder)类的<br/>[buildLineTypeset()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#buildLineTypeset-1)接口获取到LineTypeset对象实例，再通过此实例调用对应方法。<br/> |
| [Paragraph](arkts-arkgraphics2d-text-paragraph-c.md) | 保存文本内容及样式的载体，支持排版与绘制操作。<br/><br/>下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md#ParagraphBuilder)类的[build()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#build-1)接口获取到<br/>Paragraph对象实例，再通过此实例调用对应方法。<br/> |
| [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md) | 段落生成器。<br/> |
| [Run](arkts-arkgraphics2d-text-run-c.md) | 文本排版单元。<br/><br/>下列API示例中都需先使用[TextLine](arkts-arkgraphics2d-text-textline-c.md#TextLine)类的[getGlyphRuns()](arkts-arkgraphics2d-text-textline-c.md#getGlyphRuns-1)接口获取Run对象实例，再通过此实例调<br/>用对应方法。<br/> |
| [TextLine](arkts-arkgraphics2d-text-textline-c.md) | 描述段落基础文本行结构的载体。<br/><br/>下列API示例中都需先使用[Paragraph](arkts-arkgraphics2d-text-paragraphstyle-i.md#ParagraphStyle)类的[getTextLines()](arkts-arkgraphics2d-text-paragraph-c.md#getTextLines-1)接口或者<br/>[LineTypeset](arkts-arkgraphics2d-text-linetypeset-c.md#LineTypeset)类的[createLine()](arkts-arkgraphics2d-text-linetypeset-c.md#createLine-1)接口获取到TextLine对象实例，再通过此实例调用对<br/>应方法。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Decoration](arkts-arkgraphics2d-text-decoration-i.md) | 文本装饰线。<br/> |
| [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md) | 字体描述符信息。<br/> |
| [FontFeature](arkts-arkgraphics2d-text-fontfeature-i.md) | 文本字体特征。<br/> |
| [FontVariation](arkts-arkgraphics2d-text-fontvariation-i.md) | 可变字体属性。<br/> |
| [FontVariationAxis](arkts-arkgraphics2d-text-fontvariationaxis-i.md) | 字体可变轴信息。<br/> |
| [FontVariationInstance](arkts-arkgraphics2d-text-fontvariationinstance-i.md) | 字体可变实例信息，存放预设的可变字体样式信息。<br/> |
| [LineMetrics](arkts-arkgraphics2d-text-linemetrics-i.md) | 描述文本布局中单行文字的度量信息。<br/> |
| [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md) | 段落样式。<br/> |
| [PlaceholderSpan](arkts-arkgraphics2d-text-placeholderspan-i.md) | 描述占位符样式。<br/> |
| [PositionWithAffinity](arkts-arkgraphics2d-text-positionwithaffinity-i.md) | 位置和亲和度。<br/> |
| [Range](arkts-arkgraphics2d-text-range-i.md) | 描述左闭右开区间。<br/> |
| [RectStyle](arkts-arkgraphics2d-text-rectstyle-i.md) | 矩形框样式。<br/> |
| [RunMetrics](arkts-arkgraphics2d-text-runmetrics-i.md) | 描述文本行中连续文本块的布局信息和度量数据。<br/> |
| [StrutStyle](arkts-arkgraphics2d-text-strutstyle-i.md) | 支柱样式，用于控制绘制文本的行间距、基线对齐方式以及其他与行高相关的属性，默认不开启。<br/> |
| [TextBox](arkts-arkgraphics2d-text-textbox-i.md) | 文本矩形区域，表示文本在布局时所占用的矩形空间。<br/> |
| [TextLayoutResult](arkts-arkgraphics2d-text-textlayoutresult-i.md) | 文本布局结果。<br/> |
| [TextRectSize](arkts-arkgraphics2d-text-textrectsize-i.md) | 文本矩形尺寸，用于描述文本的矩形宽高属性。值为浮点数，单位为物理像素px。<br/> |
| [TextShadow](arkts-arkgraphics2d-text-textshadow-i.md) | 字体阴影。<br/> |
| [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) | 文本样式。<br/> |
| [TextTab](arkts-arkgraphics2d-text-texttab-i.md) | 段落风格的文本制表符，储存了对齐方式和位置。<br/> |
| [TypographicBounds](arkts-arkgraphics2d-text-typographicbounds-i.md) | 文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版边界相同<br/>，即与字符本身无关。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示意图展示文本行排版参数：width（包含左右空格的文本行宽度）、ascent（上升高度最高点）、descent（下降高度最低点）、leading（行间距）、top（当前行最高点）、baseline（字符基线）、bottom（<br/>&gt; 当前行最低点）、next line top（下一行最高点）。<br/>&gt;<br/>&gt; ![zh-ch_image_Typographic.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_Typographic.png)<br/>&gt;<br/>&gt; 示意图展示了字符串为" a b "的排版边界。<br/>&gt;<br/>&gt; !<br/>&gt; [zh-ch_image_TypographicBounds.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds.png)<br/>&gt;<br/>&gt; 示意图展示了字符串为"j"或"E"的排版边界。<br/>&gt;<br/>&gt; !<br/>&gt; [zh-ch_image_TypographicBounds_Character.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds_Character.png)<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Affinity](arkts-arkgraphics2d-text-affinity-e.md) | 位置亲和度枚举。<br/> |
| [BreakStrategy](arkts-arkgraphics2d-text-breakstrategy-e.md) | 断行策略枚举。<br/> |
| [EllipsisMode](arkts-arkgraphics2d-text-ellipsismode-e.md) | 省略号类型枚举。<br/><br/>EllipsisMode.START和EllipsisMode.MIDDLE仅在单行超长文本生效。<br/> |
| [FontStyle](arkts-arkgraphics2d-text-fontstyle-e.md) | 字体样式枚举。<br/> |
| [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md) | 字重枚举。<br/> |
| [FontWidth](arkts-arkgraphics2d-text-fontwidth-e.md) | 字体宽度的枚举。<br/> |
| [LineHeightStyle](arkts-arkgraphics2d-text-lineheightstyle-e.md) | 行高缩放基数枚举。<br/> |
| [PlaceholderAlignment](arkts-arkgraphics2d-text-placeholderalignment-e.md) | 占位符相对于周围文本的纵向对齐方式。<br/><br/>!<br/>[zh-ch_image_PlaceholderAlignment.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_PlaceholderAlignment.png)<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示意图展示了后三种对齐方式，前三种对齐方式在文本基线对齐方式上类似，比较位置是文本基线，即绿色线条部分。<br/>&gt;<br/>&gt; ![zh-ch_image_Baseline.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_Baseline.png)<br/> |
| [RectHeightStyle](arkts-arkgraphics2d-text-rectheightstyle-e.md) | 矩形区域高度规格枚举。<br/> |
| [RectWidthStyle](arkts-arkgraphics2d-text-rectwidthstyle-e.md) | 矩形区域宽度规格枚举。<br/> |
| <!--DelRow-->[SystemFontType](arkts-arkgraphics2d-text-systemfonttype-e.md) | 字体类型枚举，通过位或运算可实现组合类型。<br/> |
| [TextAlign](arkts-arkgraphics2d-text-textalign-e.md) | 文本对齐方式枚举。<br/> |
| [TextBadgeType](arkts-arkgraphics2d-text-textbadgetype-e.md) | 文本上下标枚举。<br/> |
| [TextBaseline](arkts-arkgraphics2d-text-textbaseline-e.md) | 文本基线类型枚举。<br/> |
| [TextDecorationStyle](arkts-arkgraphics2d-text-textdecorationstyle-e.md) | 装饰线样式枚举。<br/> |
| [TextDecorationType](arkts-arkgraphics2d-text-textdecorationtype-e.md) | 装饰线类型枚举。<br/> |
| [TextDirection](arkts-arkgraphics2d-text-textdirection-e.md) | 文本排版方向枚举。<br/> |
| [TextDisplayState](arkts-arkgraphics2d-text-textdisplaystate-e.md) | 文本显示状态的枚举。表示文本排版后的原生结果，与外部画布裁切、溢出屏幕等外部显示因素无关。<br/> |
| [TextHeightBehavior](arkts-arkgraphics2d-text-textheightbehavior-e.md) | 文本高度修饰符模式枚举。<br/> |
| [TextHighContrast](arkts-arkgraphics2d-text-texthighcontrast-e.md) | 文字渲染高对比度配置类型枚举。<br/> |
| [TextProcessState](arkts-arkgraphics2d-text-textprocessstate-e.md) | 文本处理状态的枚举。<br/> |
| [TextUndefinedGlyphDisplay](arkts-arkgraphics2d-text-textundefinedglyphdisplay-e.md) | 文本未定义字形时的显示方式枚举。<br/> |
| [TextVerticalAlign](arkts-arkgraphics2d-text-textverticalalign-e.md) | 文本垂直对齐方式枚举。<br/> |
| [WordBreak](arkts-arkgraphics2d-text-wordbreak-e.md) | 断词策略枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CaretOffsetsCallback](arkts-arkgraphics2d-text-caretoffsetscallback-t.md) | 将文本行中每个字符的偏移量和索引值作为参数的回调方法。<br/> |

