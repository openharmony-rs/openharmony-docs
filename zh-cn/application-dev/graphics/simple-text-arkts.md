# 简单文本绘制与显示（ArkTS）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## 场景介绍

在一个简单的用户界面中，可能只需要展示几行静态文本，例如标签、按钮上的文字、菜单项或状态栏中的提示信息。此时，开发者只需要选择合适的字体、大小和颜色即可完成渲染。

## 相关属性

此场景示例，涉及到的文本样式属性如下，具体及更多文本样式可参考[TextStyle](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#textstyle)。

- color：字体颜色，默认为白色。请注意与画布颜色进行区分，以保证文本的正常显示。

- fontSize：字体大小，浮点数，默认为14.0，单位为物理像素px。


## 开发步骤

1. 通过context获取到Canvas画布对象。

   ```ts
   let canvas = context.canvas;
   ```

2. 初始化文本样式，此处设置字体颜色为红色，字体大小为50。

   ```ts
   let myTextStyle: text.TextStyle = {
     // 文本颜色
     color: {
       alpha: 255,
       red: 255,
       green: 0,
       blue: 0
     },
     // 文本大小
     fontSize: 100
   };
   ```

3. 初始化段落样式。

   ```ts
   // 设置段落样式
   let myParagraphStyle: text.ParagraphStyle = {
     textStyle: myTextStyle,
   };
   ```

4. 初始化段落对象，并添加文本。

   ```ts
   let fontCollection = text.FontCollection.getGlobalInstance();
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   // 更新文本样式
   paragraphBuilder.pushStyle(myTextStyle);
   // 添加文本
   paragraphBuilder.addText('Hello World');
   ```

5. 排版段落并进行文本绘制。

   ```ts
   // 生成段落
   let paragraph = paragraphBuilder.build();
   // 布局
   paragraph.layoutSync(1250);
   // 绘制文本
   paragraph.paint(canvas, 10, 0);
   ```


## 完整示例

<!-- @[arkts_drawing_simple_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/SimpleTextDrawing/entry/src/main/ets/pages/Index.ets) -->

## 效果展示

![zh-cn_image_0000002246603717](figures/simpleText.PNG)
