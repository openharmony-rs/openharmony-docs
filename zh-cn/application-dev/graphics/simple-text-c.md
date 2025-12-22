# 简单文本绘制与显示（C/C++）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## 场景介绍

在一个简单的用户界面中，可能只需要展示几行静态文本，例如标签、按钮上的文字、菜单项或状态栏中的提示信息。此时，开发者只需要选择合适的字体、大小和颜色即可完成渲染。

## 接口说明

| 接口定义 | 描述 | 
| -------- | -------- |
| OH_Drawing_TextStyle\* OH_Drawing_CreateTextStyle(void) | 创建指向OH_Drawing_TextStyle对象的指针。 | 
| void OH_Drawing_SetTextStyleFontSize(OH_Drawing_TextStyle\* style, double fontSize) | 设置字号。 | 
| void OH_Drawing_SetTextStyleFontWeight(OH_Drawing_TextStyle\* style, int fontWeight) | 设置字重。目前只有系统默认字体支持字重的调节，其他字体设置字重值小于semi-bold时字体粗细无变化，当设置字重值大于等于semi-bold时可能会触发伪加粗效果。 | 

## 开发步骤

1. 创建Canvas画布对象，画布Canvas对象创建方法具体可见[画布的获取与绘制结果的显示](canvas-get-result-draw-c.md)。

2. 初始化段落样式，设置文本对齐方式为居中对齐。

   <!-- @[drawing_simple_text_c_create_typographyStyle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   // 创建一个 TypographyStyle 创建 Typography 时需要使用
   OH_Drawing_TypographyStyle *typoStyle = OH_Drawing_CreateTypographyStyle();
   // 设置文本对齐方式为居中
   OH_Drawing_SetTypographyTextAlign(typoStyle, TEXT_ALIGN_CENTER);
   ```

3. 初始化文本样式，此处设置字体颜色为纯黑色，字体大小为60，字重为400。

   <!-- @[drawing_simple_text_c_create_textStyle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

4. 初始化段落对象，并添加文本。

   <!-- @[drawing_simple_text_c_create_typography](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

5. 排版段落并进行文本绘制。

   <!-- @[drawing_simple_text_c_layout_and_paint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

6. 释放内存

   <!-- @[drawing_simple_text_c_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

## 效果展示

![zh-cn_image_0000002211443916](figures/zh-cn_image_0000002211443916.png)
