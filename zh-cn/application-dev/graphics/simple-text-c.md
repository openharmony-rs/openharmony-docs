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

画布Canvas对象具体可见[画布的获取与绘制结果的显示](canvas-get-result-draw-c.md)。

<!-- @[ndk_drawing_simple_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->


## 效果展示

![zh-cn_image_0000002211443916](figures/zh-cn_image_0000002211443916.png)