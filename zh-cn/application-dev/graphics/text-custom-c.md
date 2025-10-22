# 自定义文本绘制与显示（C/C++）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @KejiePeng-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

在复杂的文本排版场景中，开发者常常需要在不依赖系统排版的前提下，获取文本的字形信息、宽度、方向等底层数据，以便实现自定义的排版逻辑。系统提供了独立的文本塑形能力，允许开发者通过API获取文字的测量信息，从而支持自定义排版、绘制、断行等操作。

这种能力特别适用于以下场景：

- 自定义富文本渲染（如社交媒体、新闻客户端）

- 跨平台一致性排版需求应用

- 精细化排版管理（如艺术排版、动态文字布局）

## 独立塑形

### 接口说明

独立塑形中常用接口如下表所示，详细接口说明参考[drawing_text_typography.h](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md)和[drawing_text_blob.h](../reference/apis-arkgraphics2d/capi-drawing-text-blob-h.md)。

| 接口名 | 描述 | 
| -------- | -------- |
| OH_Drawing_LineTypography* OH_Drawing_CreateLineTypography(OH_Drawing_TypographyCreate* handler) | 创建一个排版行对象OH_Drawing_LineTypography的指针，排版行对象保存着文本内容以及样式的载体，可以用于计算单行排版信息。 | 
| OH_Drawing_TextLine* OH_Drawing_LineTypographyCreateLine(OH_Drawing_LineTypography* lineTypography,size_t startIndex, size_t count) | 根据指定区间文本内容创建一个指向文本行对象OH_Drawing_TextLine的指针。 | 
| OH_Drawing_Array* OH_Drawing_TextLineGetGlyphRuns(OH_Drawing_TextLine* line) | 获取文本行对象中的文本渲染单元数组。 | 
| OH_Drawing_Array* OH_Drawing_GetRunGlyphs(OH_Drawing_Run* run, int64_t start, int64_t length) | 获取渲染单元指定范围内的字形数组。 | 
| OH_Drawing_Font* OH_Drawing_GetRunFont(OH_Drawing_Run* run) | 获取渲染单元字体对象。 | 
| OH_Drawing_Array* OH_Drawing_GetRunGlyphAdvances(OH_Drawing_Run* run, uint32_t start, uint32_t length) | 获取渲染单元字体宽度数组。 | 
| OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void) | 用于创建一个文本构造器对象。 | 
| OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder) | 用于从文本构造器中创建文本对象。 | 
| void OH_Drawing_CanvasDrawTextBlob(OH_Drawing_Canvas* canvas, const OH_Drawing_TextBlob* textBlob, float x, float y) | 用于画一段文字。 | 



### 开发步骤

1. 在工程的`src/main/cpp/CMakeLists.txt`文件中添加以下lib。
   ```c++
   libnative_drawing.so
   ```

2. 导入依赖的相关头文件。

   ```c++
   #include <native_drawing/drawing_font_collection.h>
   #include <native_drawing/drawing_text_typography.h>
   #include <native_drawing/drawing_text_blob.h>
   #include <native_drawing/drawing_text_line.h>
   #include <native_drawing/drawing_text_run.h>
   #include <native_drawing/drawing_text_lineTypography.h>
   #include <native_drawing/drawing_rect.h>
   #include <native_drawing/drawing_point.h>
   ```

3. 创建段落样式，并使用构造段落生成器ParagraphBuilder生成段落实例。

   ```c++
    // 创建一个 TypographyStyle，创建 TypographyCreate 时需要使用
    OH_Drawing_TypographyStyle *typoStyle = OH_Drawing_CreateTypographyStyle();
    // 设置文字颜色、大小、字重，不设置 TextStyle 会使用 TypographyStyle 中的默认 TextStyle
    OH_Drawing_TextStyle *txtStyle = OH_Drawing_CreateTextStyle();
    OH_Drawing_SetTextStyleFontSize(txtStyle, 100);

    // 创建 FontCollection，FontCollection 用于管理字体匹配逻辑
    OH_Drawing_FontCollection *fc = OH_Drawing_CreateSharedFontCollection();
    // 使用 FontCollection 和 之前创建的 TypographyStyle 创建 TypographyCreate。TypographyCreate 用于创建 Typography
    OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typoStyle, fc);
   ```

4. 设置文本样式，添加文本内容。

   ```c++
    // 设置文本内容，并将文本添加到 handler 中
    OH_Drawing_TypographyHandlerPushTextStyle(handler, txtStyle);
    const char *text = "Hello World";
    OH_Drawing_TypographyHandlerAddText(handler, text);
   ```

5. 创建行对象。获取行中所有文字的塑形结果。

   ```c++
    // 通过 handler 创建一个 Typography
    OH_Drawing_LineTypography *lineTypography = OH_Drawing_CreateLineTypography(handler);
    OH_Drawing_TextLine *textLine = OH_Drawing_LineTypographyCreateLine(lineTypography, 0, 11);
    // 获取塑形结果
    OH_Drawing_Array *runs = OH_Drawing_TextLineGetGlyphRuns(textLine);
   ```

6. 遍历所有字形，创建textBlob对象并重新定义字形位置，通过drawTextBlob接口进行自定义绘制。

   ```c++
   for (int i = 0; i < runsLength; i++) {
        OH_Drawing_Run *run = OH_Drawing_GetRunByIndex(runs, i);
        // 获取所有字形数据
        OH_Drawing_Array *glyphs = OH_Drawing_GetRunGlyphs(run, 0, 0);
        size_t glyphsLength = OH_Drawing_GetDrawingArraySize(glyphs);
        // 获取相同绘制单元字体
        OH_Drawing_Font *font = OH_Drawing_GetRunFont(run);
        OH_Drawing_Array *advances = OH_Drawing_GetRunGlyphAdvances(run, 0, 0);

        OH_Drawing_TextBlobBuilder *builder = OH_Drawing_TextBlobBuilderCreate();
        OH_Drawing_Rect *rect = OH_Drawing_RectCreate(0, 0, 20, 20);
        const OH_Drawing_RunBuffer *runBuffer =
            OH_Drawing_TextBlobBuilderAllocRunPos(builder, font, glyphsLength, rect);
        
        // 创建字形buffer，通过drawing接口进行字形独立绘制
        int x = 0, y = 0;
        for (int index = 0; index < glyphsLength; index++) {
            uint16_t glyph = OH_Drawing_GetRunGlyphsByIndex(glyphs, index);

            runBuffer->glyphs[index] = glyph;
            runBuffer->pos[index * 2] = x;
            runBuffer->pos[index * 2 + 1] = y;

            OH_Drawing_Point *advance = OH_Drawing_GetRunGlyphAdvanceByIndex(advances, index);
            float glyphX = 0;
            float glyphY = 0;
            OH_Drawing_PointGetX(advance, &glyphX);
            OH_Drawing_PointGetY(advance, &glyphY);
            x += glyphX + 10; // 每个字形间水平间隔10px
            y += glyphY + 30; // 每个字形间垂直间隔30px
        }
        
        // 自定义绘制一串具有相同属性的一系列连续字形
        OH_Drawing_TextBlob* textBlob = OH_Drawing_TextBlobBuilderMake(builder);
        OH_Drawing_CanvasDrawTextBlob(cCanvas_, textBlob, 20, 100);
        
        // 释放内存
        OH_Drawing_TextBlobDestroy(textBlob);
        OH_Drawing_FontDestroy(font);
        OH_Drawing_DestroyRunGlyphAdvances(advances);
        OH_Drawing_DestroyRunGlyphs(glyphs);
   }
   ```
   
7. 释放内存
   ```c++
   // 释放内存
   OH_Drawing_DestroyTypographyStyle(typoStyle);
   OH_Drawing_DestroyTextStyle(txtStyle);
   OH_Drawing_DestroyFontCollection(fc);
   OH_Drawing_DestroyTypographyHandler(handler);
   OH_Drawing_DestroyLineTypography(lineTypography);
   OH_Drawing_DestroyTextLine(textLine);
   OH_Drawing_DestroyRuns(runs);
   ```

### 完整示例

完整的独立塑形示例如下。
```c++
#include <native_drawing/drawing_font_collection.h>
#include <native_drawing/drawing_text_typography.h>
#include <native_drawing/drawing_text_blob.h>
#include <native_drawing/drawing_text_line.h>
#include <native_drawing/drawing_text_run.h>
#include <native_drawing/drawing_text_lineTypography.h>
#include <native_drawing/drawing_rect.h>
#include <native_drawing/drawing_point.h>

void SampleBitMap::drawIndependentShapingText() {
    // 创建一个 TypographyStyle，创建 TypographyCreate 时需要使用
    OH_Drawing_TypographyStyle *typoStyle = OH_Drawing_CreateTypographyStyle();
    // 设置文字颜色、大小、字重，不设置 TextStyle 会使用 TypographyStyle 中的默认 TextStyle
    OH_Drawing_TextStyle *txtStyle = OH_Drawing_CreateTextStyle();
    OH_Drawing_SetTextStyleFontSize(txtStyle, 100);

    // 创建 FontCollection，FontCollection 用于管理字体匹配逻辑
    OH_Drawing_FontCollection *fc = OH_Drawing_CreateSharedFontCollection();
    // 使用 FontCollection 和 之前创建的 TypographyStyle 创建 TypographyCreate。TypographyCreate 用于创建 Typography
    OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typoStyle, fc);
    // 设置文本内容，并将文本添加到 handler 中
    OH_Drawing_TypographyHandlerPushTextStyle(handler, txtStyle);
    const char *text = "Hello World";
    OH_Drawing_TypographyHandlerAddText(handler, text);

    // 通过 handler 创建一个 Typography
    OH_Drawing_LineTypography *lineTypography = OH_Drawing_CreateLineTypography(handler);
    OH_Drawing_TextLine *textLine = OH_Drawing_LineTypographyCreateLine(lineTypography, 0, 11);

    // 获取塑形结果
    OH_Drawing_Array *runs = OH_Drawing_TextLineGetGlyphRuns(textLine);
    size_t runsLength = OH_Drawing_GetDrawingArraySize(runs);
    for (int i = 0; i < runsLength; i++) {
        OH_Drawing_Run *run = OH_Drawing_GetRunByIndex(runs, i);
        // 获取所有字形数据
        OH_Drawing_Array *glyphs = OH_Drawing_GetRunGlyphs(run, 0, 0);
        size_t glyphsLength = OH_Drawing_GetDrawingArraySize(glyphs);
        // 获取相同绘制单元字体
        OH_Drawing_Font *font = OH_Drawing_GetRunFont(run);
        OH_Drawing_Array *advances = OH_Drawing_GetRunGlyphAdvances(run, 0, 0);

        OH_Drawing_TextBlobBuilder *builder = OH_Drawing_TextBlobBuilderCreate();
        OH_Drawing_Rect *rect = OH_Drawing_RectCreate(0, 0, 20, 20);
        const OH_Drawing_RunBuffer *runBuffer =
            OH_Drawing_TextBlobBuilderAllocRunPos(builder, font, glyphsLength, rect);
        
        // 创建字形buffer，通过drawing接口进行字形独立绘制
        int x = 0, y = 0;
        for (int index = 0; index < glyphsLength; index++) {
            uint16_t glyph = OH_Drawing_GetRunGlyphsByIndex(glyphs, index);

            runBuffer->glyphs[index] = glyph;
            runBuffer->pos[index * 2] = x;
            runBuffer->pos[index * 2 + 1] = y;

            OH_Drawing_Point *advance = OH_Drawing_GetRunGlyphAdvanceByIndex(advances, index);
            float glyphX = 0;
            float glyphY = 0;
            OH_Drawing_PointGetX(advance, &glyphX);
            OH_Drawing_PointGetY(advance, &glyphY);
            x += glyphX + 10; // 每个字形间水平间隔10px
            y += glyphY + 30; // 每个字形间垂直间隔30px
        }
        
        // 自定义绘制一串具有相同属性的一系列连续字形
        OH_Drawing_TextBlob* textBlob = OH_Drawing_TextBlobBuilderMake(builder);
        OH_Drawing_CanvasDrawTextBlob(cCanvas_, textBlob, 20, 100);
        
        // 释放内存
        OH_Drawing_TextBlobDestroy(textBlob);
        OH_Drawing_FontDestroy(font);
        OH_Drawing_DestroyRunGlyphAdvances(advances);
        OH_Drawing_DestroyRunGlyphs(glyphs);
    }

    // 释放内存
    OH_Drawing_DestroyTypographyStyle(typoStyle);
    OH_Drawing_DestroyTextStyle(txtStyle);
    OH_Drawing_DestroyFontCollection(fc);
    OH_Drawing_DestroyTypographyHandler(handler);
    OH_Drawing_DestroyLineTypography(lineTypography);
    OH_Drawing_DestroyTextLine(textLine);
    OH_Drawing_DestroyRuns(runs);
}
```

### 效果展示
![ndk_independent_shaping.png](figures/ndk_independent_shaping.png)