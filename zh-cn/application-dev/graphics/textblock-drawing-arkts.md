# 字块绘制（ArkTS）

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 场景介绍

字块（TextBlob）是指文本的集合。无论是单个的文字还是大块的文本，都可以通过字块来绘制。

除了基本的字块绘制之外，还可以给文字添加各种绘制效果。常见的字块绘制场景包括[文字描边](#文字描边)、[文字渐变](#文字渐变)、[字体回退](#字体回退)等，更多效果请见[绘制效果](drawing-effect-overview.md)。

本节不涉及文本测量和布局排版相关内容，如需在开发中处理此类文本绘制需求，可参考[文本开发概述](text-overview.md)，该文档系统讲解了排版策略与相关使用指导。

## 基本字块绘制

Canvas通过drawTextBlob()来绘制字块。函数接受三个参数：TextBlob字块对象，以及文字基线左端点的x坐标和y坐标。

画布Canvas对象具体可见[画布的获取与绘制结果的显示（ArkTS）](canvas-get-result-draw-arkts.md)。

字块对象可以通过多种方式创建得到，详细的字块创建方式和接口使用请参考[TextBlob](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md)。

此处以使用makeFromString()接口创建字块为例，接口接受3个参数，分别为：

- 需要显示的字符串text。

- font字型对象。其中font用于设置和获取字体的各种属性，如字体大小、文本样式、字体对齐方式、字体渲染方式、字体描边方式等，详细的API介绍请参考[Font](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md)。

- 文本编码方式。当前支持的文本编码方式如下：
  - TEXT_ENCODING_UTF8：使用1个字节表示UTF-8或ASCII；
  - TEXT_ENCODING_UTF16：使用2个字节表示大部分unicode；
  - TEXT_ENCODING_UTF32：使用4个字节表示全部unicode；
  - TEXT_ENCODING_GLYPH_ID：使用2个字节表示glyph index。

基本效果的示例代码和效果图如下：

<!-- @[arkts_graphics_draw_base_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 设置字体大小
font.setSize(100);
// 创建字块对象
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// 绘制字块
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
```

![Screenshot_20241225151030139](figures/Screenshot_20241225151030139.jpg)

## 文字描边

基于基本的字块绘制，还可以通过画笔实现文字描边效果，描边效果的更多介绍请参考[描边效果](basic-drawing-effect-arkts.md#描边效果)。

以下以英文文字描边和中文文字描边给出示例和指导。

### 英文文字描边

英文文字描边的简要示例和示意图如下：

<!-- @[arkts_graphics_draw_stroke_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建画笔
let pen = new drawing.Pen();
// 设置抗锯齿
pen.setAntiAlias(true);
// 设置描边线宽
pen.setStrokeWidth(3.0);
// 设置描边颜色
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// 创建字型对象
const font = new drawing.Font();
// 设置字体大小
font.setSize(100);
// 添加画笔描边效果
canvas.attachPen(pen);
// 创建字块对象
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// 绘制字块
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
// 去除描边效果
canvas.detachPen();
```

![Screenshot_20241225152446749](figures/Screenshot_20241225152446749.jpg)

### 中文文字描边

首先需要通过画笔描边，然后需要调用画刷填充内部颜色，去除字体中间的杂质和重叠部分，实现中文文字描边效果。

中文文字描边的简要示例和示意图如下：

<!-- @[arkts_graphics_draw_chinese_stroke_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript

// 创建画刷
let brush = new drawing.Brush();
// 创建画笔
let pen = new drawing.Pen();
// 设置抗锯齿
brush.setAntiAlias(true);
// 设置填充颜色
brush.setColor(0xFF, 0xFF, 0xFF, 0xFF);

pen.setAntiAlias(true);
// 设置描边线宽
pen.setStrokeWidth(3.0);
// 设置描边颜色
pen.setColor(0xFF, 0xFF, 0x00, 0x00);

// 创建字型对象
const font = new drawing.Font();
// 设置字体大小
font.setSize(100);
// 添加画笔描边效果
canvas.attachPen(pen);
// 创建字块对象
const textBlob = drawing.TextBlob.makeFromString(STROKE_SAMPLE, font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// 绘制字块
canvas.drawTextBlob(textBlob, VALUE_200,  VALUE_300);
// 去除描边效果
canvas.detachPen(); 

canvas.attachBrush(brush);
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
canvas.detachBrush();
```

![chinese_stroke_text_ark](figures/chinese_stroke_text_ark.png)

## 文字渐变

基于基本字块绘制，还可以通过着色器实现文字渐变的效果，着色器的更多介绍请参考[着色器效果](complex-drawing-effect-arkts.md#着色器效果)。

以下为文字添加了线性渐变着色器效果的简要示例和示意图：

<!-- @[arkts_graphics_draw_gradient_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
let startPt: common2D.Point = { x: VALUE_100, y: VALUE_100 };
let endPt: common2D.Point = { x: VALUE_900, y: VALUE_900 };
let colors = [0xFFFFFF00, 0xFFFF0000, 0xFF0000FF];
// 创建线性渐变着色器
let shaderEffect = drawing.ShaderEffect.createLinearGradient(startPt, endPt, colors, drawing.TileMode.CLAMP);
// 创建画刷
let brush = new drawing.Brush();
// 设置着色器
brush.setShaderEffect(shaderEffect);
// 添加画刷填充效果
canvas.attachBrush(brush);
// 创建字型
const font = new drawing.Font();
// 设置字体大小
font.setSize(VALUE_200);
// 创建字块
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// 绘制字块
canvas.drawTextBlob(textBlob, VALUE_100, VALUE_300);
// 去除填充效果
canvas.detachBrush();
```

![Screenshot_20241225155707415](figures/Screenshot_20241225155707415.jpg)

## 主题字体

主题字体，特指系统**主题应用**中能使用的字体，属于一种特殊的自定义字体。如需涉及文本测量和布局排版相关内容，可参考[使用主题字体（ArkTS）](theme-font-arkts.md)。

设置跟随主题字体的示例代码和效果图如下：

<!-- @[arkts_graphics_draw_theme_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) --> 

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 设置文字大小
font.setSize(100);
// 设置跟随主题字体
font.setThemeFontFollowed(true);
// 创建字块对象
const textBlob = drawing.TextBlob.makeFromString('Hello World', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// 绘制字块
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
```

| 未跟随主题字体的效果图 | 跟随主题字体的效果图（不同主题字体显示效果不同，此处仅示意） |
| -------- | -------- |
| ![Snapshot_setThemeFontFollowed_sys](figures/Snapshot_setThemeFontFollowed_sys.jpg) | ![Snapshot_setThemeFontFollowed](figures/Snapshot_setThemeFontFollowed.jpg) |

> **说明**
>
> 需要在应用入口文件（默认工程中为EntryAbility.ets）中复写onConfigurationUpdate函数，以响应切换主题字体的操作，确保切换后页面能够及时刷新并生效。具体实现可参考[使用主题字体（ArkTS）](theme-font-arkts.md)。

## 单字绘制

单字绘制是图形渲染中针对文本渲染的一种精细化控制技术。相比字块绘制，其核心优势在于能够利用字体退化机制，在当前字体无法显示某字符时，自动退化到使用系统字体绘制字符，提升对特殊字符的兼容性，避免字符缺失。同时，单字绘制支持逐字符配置字体特征（如连字、替代字形），满足复杂排版需求，增强用户体验。详细API说明请见[drawSingleCharacter](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#drawsinglecharacter12)。

基础场景：绘制无字体特征的字符。

对于无需字体特征的常规文本渲染场景，可以使用drawSingleCharacter绘制单个字符，使用measureSingleCharacter测量单个字符的宽度，示例代码和效果图如下：

<!-- @[arkts_graphics_draw_single_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 设置文字大小
font.setSize(100);
let startX = 100;
let startY = 100;
let text = ['H', 'e', 'l', 'l', 'o'];
for (let s of text) {
  // 单字绘制
  canvas.drawSingleCharacter(s, font, startX, startY);
  // 测量单个字符的宽度
  let textWidth = font.measureSingleCharacter(s);
  startX += textWidth;
}
```

![Snapshot_drawSingleCharacter](figures/Snapshot_drawSingleCharacter.jpg)

进阶场景：绘制带字体特征的字符。

对于需要字体特征的文本渲染场景，可以使用drawSingleCharacterWithFeatures绘制单个字符，使用measureSingleCharacterWithFeatures测量单个字符的宽度，示例代码和效果图如下：

<!-- @[arkts_graphics_draw_feature_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 设置文字大小
font.setSize(100);
let startX = 100;
let startY = 100;
let text = ['a', '2', '+', 'b', '2'];
// 创建字体特征对象数组
let fontFeatures: drawing.FontFeature[] = [{name: 'frac', value: 1}];
for (let s of text) {
  // 单字绘制
  canvas.drawSingleCharacterWithFeatures(s, font, startX, startY, fontFeatures);
  // 测量单个字符的宽度
  let textWidth = font.measureSingleCharacterWithFeatures(s, fontFeatures);
  startX += textWidth;
}
```

![Snapshot_drawSingleCharacter](figures/Snapshot_drawSingleCharacterWithFeatures.png)

> **说明**
>
> 如果 `drawSingleCharacterWithFeatures` 与 `measureSingleCharacter` 混合使用，或者 `drawSingleCharacter` 与 `measureSingleCharacterWithFeatures` 混合使用，字体绘制可能会重叠。

## 字体回退

在实际开发中，开发者指定的字体未必能覆盖文本中的全部字符，例如一个仅包含拉丁字符的字体无法显示中文、阿拉伯文等字符。此时若直接使用该字体绘制文本，不在字体覆盖范围内的字符将无法正常显示。字体回退（Font Fallback）能力可以自动从系统字体中查找能够支持这些字符的字体进行显示，从而兼顾字体风格统一与文本的完整呈现，开发者无需自行判断字符覆盖范围，也无需为不同语言单独指定字体。若系统字体中仍无支持某字符的字体，则该字符依旧无法正常显示。

当需要注意字符覆盖范围、或需要在一段文本中混用多种语言时，即可使用本节介绍的支持字体回退的接口。[单字绘制](#单字绘制)也具备字体回退能力，适用于逐字符渲染场景；本节介绍的是字块创建、字形转换与文本宽度测量场景下的字体回退接口。详细的API介绍请参考[TextBlob](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md)和[Font](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md)。

> **说明**
>
> 从API版本26.0.1开始，新增字体回退功能。

### 字块绘制支持字体回退

当指定的字体无法覆盖文本中的所有字符时，可以使用支持字体回退的字块创建接口[makeFromStringWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md#makefromstringwithfallback)或[makeFromPosTextWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md#makefrompostextwithfallback)。接口会自动为不支持的字符查找系统回退字体，并按字体将文本分组，生成一组字块对象。绘制时，需将所有字块绘制在同一坐标原点，即可完整呈现整段文本。

主要实现步骤如下：创建字型对象并设置字体 → 准备文本 → 调用回退接口获取字块数组 → 遍历数组，在同一原点绘制每个字块。

使用[makeFromStringWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md#makefromstringwithfallback)接口从字符串创建支持字体回退的字块数组并绘制的示例代码如下：

<!-- @[arkts_graphics_draw_textblob_string_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 创建字体对象
const myTypeface = drawing.Typeface.makeFromFile('/system/fonts/NotoSansArmenian[wdth,wght].ttf');
// 为字型设置字体
font.setTypeface(myTypeface);
// 设置字体大小
font.setSize(VALUE_100);
// 创建支持字体回退的字块数组
const textBlobs = drawing.TextBlob.makeFromStringWithFallback('Hello世界', font);
// 遍历字块数组并绘制，每个TextBlob绘制在相同原点
for (let textBlob of textBlobs) {
  canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
}
```

| 使用不回退接口makeFromString()的效果图 | 使用回退接口makeFromStringWithFallback()的效果图 |
| -------- | -------- |
| ![字体不回退](figures/makefromstring.png) | ![字体回退](figures/makefromstringwithfallback.png) |

使用[makeFromPosTextWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md#makefrompostextwithfallback)接口从文本和坐标点数组创建支持字体回退的字块数组并绘制的示例代码如下：

<!-- @[arkts_graphics_draw_textblob_postext_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 创建字体对象
const myTypeface = drawing.Typeface.makeFromFile('/system/fonts/NotoSansArmenian[wdth,wght].ttf');
// 为字型设置字体
font.setTypeface(myTypeface);
// 设置字体大小
font.setSize(VALUE_100);
// 需要绘制的文本
const text = 'Hello世界';
// 获取glyph数量
const glyphCount = font.countText(text);
// 为每个字符指定坐标位置
let points: common2D.Point[] = [];
let xOffset = 0;
for (let i = 0; i < glyphCount; i++) {
  points.push({ x: VALUE_200 + xOffset, y: VALUE_300 });
  xOffset += 60;
}
// 创建支持字体回退的字块数组
const textBlobs = drawing.TextBlob.makeFromPosTextWithFallback(text, glyphCount, points, font);
// 遍历字块数组并绘制
for (let textBlob of textBlobs) {
  canvas.drawTextBlob(textBlob, 0, 0);
}
```

| 使用不回退接口makeFromPosText()的效果图 | 使用回退接口makeFromPosTextWithFallback()的效果图 |
| -------- | -------- |
| ![字体不回退](figures/makefrompostext.png) | ![字体回退](figures/makefrompostextwithfallback.png) |

### 字形转换与文本宽度测量支持字体回退

当需要将文本转换为字形，或测量文本在字体回退后的实际宽度时，可以使用Font提供的支持字体回退的字形转换接口[textToGlyphsWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#texttoglyphswithfallback)和文本宽度测量接口[measureTextWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#measuretextwithfallback)。

使用[textToGlyphsWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#texttoglyphswithfallback)将文本转换为字形信息（转换时自动按回退字体分组），再逐组设置对应字体、根据字形宽度计算位置，最后通过[drawGlyphs()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#drawglyphs)绘制。示例代码如下：

<!-- @[arkts_graphics_draw_font_texttoglyphs_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 创建字体对象
const myTypeface = drawing.Typeface.makeFromFile('/system/fonts/NotoSansArmenian[wdth,wght].ttf');
// 为字型设置字体
font.setTypeface(myTypeface);
// 设置字体大小
font.setSize(VALUE_100);
// 需要转换的文本
const text = 'Hello世界';
// 获取glyph数量
const glyphCount = font.countText(text);
// 将文本转换为glyph索引，支持字体回退
const fallbackInfos = font.textToGlyphsWithFallback(text, glyphCount);
// 使用drawGlyphs按回退字体分组绘制字形
let xOffset = 0;
// 遍历回退信息，每个元素包含相同typeface的glyph ID数组
for (let info of fallbackInfos) {
  // info.typeface为匹配的字体
  // info.glyphIds为该字体对应的glyph ID数组
  font.setTypeface(info.typeface);
  let positions: common2D.Point[] = [];
  let glyphWidths = font.getWidths(info.glyphIds);
  for (let j = 0; j < info.glyphIds.length; j++) {
    positions.push({ x: VALUE_200 + xOffset, y: VALUE_300 });
    xOffset += glyphWidths[j];
  }
  canvas.drawGlyphs(info.glyphIds, 0, positions, 0, info.glyphIds.length, font);
}
```

| 使用不回退接口textToGlyphs()的效果图 | 使用回退接口textToGlyphsWithFallback()的效果图 |
| -------- | -------- |
| ![字体不回退](figures/textToGlyphs.png) | ![字体回退](figures/textToGlyphsWithFallback.png) |

使用[measureTextWithFallback()](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#measuretextwithfallback)接口测量文本在字体回退后实际宽度的示例代码如下：

<!-- @[arkts_graphics_draw_font_measure_fallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// 创建字型对象
const font = new drawing.Font();
// 创建字体对象
const myTypeface = drawing.Typeface.makeFromFile('/system/fonts/NotoSansArmenian[wdth,wght].ttf');
// 为字型设置字体
font.setTypeface(myTypeface);
// 设置字体大小
font.setSize(VALUE_100);
// 需要测量的文本
const text = 'Hello世界';
// 测量文本宽度，支持字体回退
const textWidth = font.measureTextWithFallback(text, drawing.TextEncoding.TEXT_ENCODING_UTF8);
console.info('textWidth: ' + textWidth);
```

<!--RP1-->
## 相关实例

针对Drawing(ArkTS)的开发，有以下相关实例可供参考：

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->