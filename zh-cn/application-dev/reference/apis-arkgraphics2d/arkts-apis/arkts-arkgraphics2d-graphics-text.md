# @ohos.graphics.text

文本模块


**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontCount](arkts-arkgraphics2d-text-getfontcount-f.md) | 根据字体文件路径获取包含的字体文件数。 |
| [getFontDescriptorByFullName](arkts-arkgraphics2d-text-getfontdescriptorbyfullname-f.md) | 根据字体名称和类型获取字体描述符，使用Promise异步回调。 |
| [getFontDescriptorsFromPath](arkts-arkgraphics2d-text-getfontdescriptorsfrompath-f.md) | 根据字体文件路径获取字体描述符数组。使用Promise异步回调。 |
| [getFontPathsByType](arkts-arkgraphics2d-text-getfontpathsbytype-f.md) | 获取指定字体类型的所有字体文件路径。 |
| [getFontUnicodeSet](arkts-arkgraphics2d-text-getfontunicodeset-f.md) | 根据字体文件路径获取字体unicode数组。使用Promise异步回调。 |
| [getSystemFontFullNamesByType](arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) | 根据字体类型返回该类型对应的所有字体的字体名称，使用Promise异步回调。 |
| [isFontSupported](arkts-arkgraphics2d-text-isfontsupported-f.md) | 检查系统是否支持指定的字体文件。可在加载自定义字体前预先验证字体文件的可用性，避免因字体不支持导致文本渲染异常。 |
| [matchFontDescriptors](arkts-arkgraphics2d-text-matchfontdescriptors-f.md) | 根据指定的字体描述符返回所有符合要求的系统字体描述符，使用Promise异步回调。 |
| [setTextHighContrast](arkts-arkgraphics2d-text-settexthighcontrast-f.md) | 用于设置文字渲染高对比度模式。 |
| [setTextUndefinedGlyphDisplay](arkts-arkgraphics2d-text-settextundefinedglyphdisplay-f.md) | 设置字符映射到.notdef（未定义）字形时要使用的字形类型。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | 字体集，用于管理文本排版所需的字体资源。FontCollection为[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md)提供字体匹配和字形查找能力，是文本排版管线的基础组件。提供全局实例（[getGlobalInstance](arkts-arkgraphics2d-text-fontcollection-c.md#getglobalinstance)）和本地实例（[getLocalInstance](arkts-arkgraphics2d-text-fontcollection-c.md#getlocalinstance)），全局实例加载的字体在应用内共享，适用于普通应用场景；本地实例各实例独立，加载的字体仅对当前实例生效、实例间互不影响，推荐卡片场景使用。支持通过[loadFontSync](arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)或[loadFont](arkts-arkgraphics2d-text-fontcollection-c.md#loadfont)加载自定义字体。 |
| [LineTypeset](arkts-arkgraphics2d-text-linetypeset-c.md) | 保存文本内容及样式的载体，可用于计算单行排版信息。 |
| [Paragraph](arkts-arkgraphics2d-text-paragraph-c.md) | 保存文本内容及样式的载体，支持排版与绘制操作。 |
| [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md) | 段落生成器，采用建造者模式构建段落对象。开发者通过构造函数传入[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)和[FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md)初始化ParagraphBuilder，然后通过[pushStyle](arkts-arkgraphics2d-text-paragraphbuilder-c.md#pushstyle)设置文本样式、[addText](arkts-arkgraphics2d-text-paragraphbuilder-c.md#addtext)添加文本内容，最终调用[build()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#build)接口生成[Paragraph](arkts-arkgraphics2d-text-paragraph-c.md)对象进行排版和绘制。 |
| [Run](arkts-arkgraphics2d-text-run-c.md) | 文本排版单元，表示一段具有相同样式属性的连续文本片段。Run由[TextLine](arkts-arkgraphics2d-text-textline-c.md)类的[getGlyphRuns()](arkts-arkgraphics2d-text-textline-c.md#getglyphruns)接口获取。 |
| [TextLine](arkts-arkgraphics2d-text-textline-c.md) | 描述段落基础文本行结构的载体。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Decoration](arkts-arkgraphics2d-text-decoration-i.md) | 文本装饰线。 |
| [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md) | 字体描述符信息。 |
| [FontFeature](arkts-arkgraphics2d-text-fontfeature-i.md) | 文本字体特征。 |
| [FontVariation](arkts-arkgraphics2d-text-fontvariation-i.md) | 可变字体属性。 |
| [FontVariationAxis](arkts-arkgraphics2d-text-fontvariationaxis-i.md) | 字体可变轴信息。 |
| [FontVariationInstance](arkts-arkgraphics2d-text-fontvariationinstance-i.md) | 字体可变实例信息，存放预设的可变字体样式信息。 |
| [LineMetrics](arkts-arkgraphics2d-text-linemetrics-i.md) | 描述文本布局中单行文字的度量信息。 |
| [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md) | 段落样式，用于控制段落的整体布局行为，包括对齐方式、断行策略和最大行数等属性。ParagraphStyle作为[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md)构造函数的必要参数，与[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)（控制文本级别样式）分工协作，共同决定段落的最终排版效果。 |
| [PlaceholderSpan](arkts-arkgraphics2d-text-placeholderspan-i.md) | 描述占位符样式。 |
| [PositionWithAffinity](arkts-arkgraphics2d-text-positionwithaffinity-i.md) | 位置和亲和度。 |
| [Range](arkts-arkgraphics2d-text-range-i.md) | 描述左闭右开区间。 |
| [RectStyle](arkts-arkgraphics2d-text-rectstyle-i.md) | 矩形框样式。 |
| [RunMetrics](arkts-arkgraphics2d-text-runmetrics-i.md) | 描述文本行中连续文本块的布局信息和度量数据。 |
| [StrutStyle](arkts-arkgraphics2d-text-strutstyle-i.md) | 支柱样式，用于控制绘制文本的行间距、基线对齐方式以及其他与行高相关的属性，默认不开启。 |
| [TextBox](arkts-arkgraphics2d-text-textbox-i.md) | 文本矩形区域，表示文本在布局时所占用的矩形空间。 |
| [TextLayoutResult](arkts-arkgraphics2d-text-textlayoutresult-i.md) | 文本布局结果。 |
| [TextRectSize](arkts-arkgraphics2d-text-textrectsize-i.md) | 文本矩形尺寸，用于描述文本的矩形宽高属性。值为浮点数，单位为物理像素px。 |
| [TextShadow](arkts-arkgraphics2d-text-textshadow-i.md) | 文本阴影。 |
| [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) | 文本样式，用于控制文本的视觉表现属性，包括字体、颜色、字号、间距、装饰线和阴影等。TextStyle通过[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md)的[pushStyle](arkts-arkgraphics2d-text-paragraphbuilder-c.md#pushstyle)方法应用到后续添加的文本内容，与[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)（控制段落级别属性）配合使用。同一段落中可通过多次pushStyle实现对不同文本片段应用不同样式。 |
| [TextTab](arkts-arkgraphics2d-text-texttab-i.md) | 段落风格的文本制表符，储存了对齐方式和位置。 |
| [TypographicBounds](arkts-arkgraphics2d-text-typographicbounds-i.md) | 文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版边界相同，即与字符本身无关。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Affinity](arkts-arkgraphics2d-text-affinity-e.md) | 位置亲和度枚举。 |
| [BreakStrategy](arkts-arkgraphics2d-text-breakstrategy-e.md) | 断行策略枚举。 |
| [EllipsisMode](arkts-arkgraphics2d-text-ellipsismode-e.md) | 省略号类型枚举。 |
| [FontStyle](arkts-arkgraphics2d-text-fontstyle-e.md) | 字体样式枚举。 |
| [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md) | 字重枚举。 |
| [FontWidth](arkts-arkgraphics2d-text-fontwidth-e.md) | 字体宽度的枚举。 |
| [LineHeightStyle](arkts-arkgraphics2d-text-lineheightstyle-e.md) | 行高缩放基数枚举。 |
| [PlaceholderAlignment](arkts-arkgraphics2d-text-placeholderalignment-e.md) | 占位符相对于周围文本的纵向对齐方式。 |
| [RectHeightStyle](arkts-arkgraphics2d-text-rectheightstyle-e.md) | 矩形区域高度规格枚举。 |
| [RectWidthStyle](arkts-arkgraphics2d-text-rectwidthstyle-e.md) | 矩形区域宽度规格枚举。 |
| [SystemFontType](arkts-arkgraphics2d-text-systemfonttype-e.md) | 字体类型枚举，通过位或运算可实现组合类型。 |
| [TextAlign](arkts-arkgraphics2d-text-textalign-e.md) | 文本对齐方式枚举。 |
| [TextBadgeType](arkts-arkgraphics2d-text-textbadgetype-e.md) | 文本上下标枚举。 |
| [TextBaseline](arkts-arkgraphics2d-text-textbaseline-e.md) | 文本基线类型枚举。 |
| [TextDecorationStyle](arkts-arkgraphics2d-text-textdecorationstyle-e.md) | 装饰线样式枚举。 |
| [TextDecorationType](arkts-arkgraphics2d-text-textdecorationtype-e.md) | 装饰线类型枚举。 |
| [TextDirection](arkts-arkgraphics2d-text-textdirection-e.md) | 文本排版方向枚举。 |
| [TextDisplayState](arkts-arkgraphics2d-text-textdisplaystate-e.md) | 文本显示状态的枚举。表示文本排版后的原生结果，与外部画布裁切、溢出屏幕等外部显示因素无关。 |
| [TextHeightBehavior](arkts-arkgraphics2d-text-textheightbehavior-e.md) | 文本高度修饰符模式枚举。 |
| [TextHighContrast](arkts-arkgraphics2d-text-texthighcontrast-e.md) | 文字渲染高对比度配置类型枚举。 |
| [TextProcessState](arkts-arkgraphics2d-text-textprocessstate-e.md) | 文本处理状态的枚举。 |
| [TextUndefinedGlyphDisplay](arkts-arkgraphics2d-text-textundefinedglyphdisplay-e.md) | 文本未定义字形时的显示方式枚举。 |
| [TextVerticalAlign](arkts-arkgraphics2d-text-textverticalalign-e.md) | 文本垂直对齐方式枚举。 |
| [WordBreak](arkts-arkgraphics2d-text-wordbreak-e.md) | 断词策略枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CaretOffsetsCallback](arkts-arkgraphics2d-text-caretoffsetscallback-t.md) | 将文本行中每个字符的偏移量和索引值作为参数的回调方法。 |
