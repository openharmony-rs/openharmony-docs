# 图片绘制（ArkTS）

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

位图是一种用于在内存中存储和表示图像的数据结构，它是一个未经过压缩的像素集合，而JPEG或PNG等格式的图片是压缩格式的，两者并不相同。如果需要将JPEG或PNG绘制到屏幕上，需要先解码成位图格式，具体可参考[图片处理服务（Image Kit）](../media/image/image-overview.md)图片解码相关章节。


目前Drawing（ArkTS）中位图绘制需要依赖PixelMap，它可以用于读取或写入图像数据以及获取图像信息。详细的API介绍请参考[PixelMap](../reference/apis-image-kit/arkts-apis-image-PixelMap.md)。


1. 创建PixelMap。

   有多个API接口可以创建PixelMap，下文以createPixelMapSync()为例。更多创建方式和接口请见[@ohos.multimedia.image (图片处理)](../reference/apis-image-kit/arkts-apis-image.md)模块。

   <!-- @[arkts_graphics_draw_image](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/PixelMapDrawing.ets) -->

2. （可选）编辑PixelMap中的像素。如果没有编辑像素的需求，此步骤可以省略。

   有多个API接口可以编辑PixelMap中的像素，下文以writePixelsSync()为例。更多方式和接口的使用可见[PixelMap](../reference/apis-image-kit/arkts-apis-image-PixelMap.md)。

   <!-- @[arkts_graphics_draw_edit_pixel](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/PixelMapDrawing.ets) -->

3. 绘制PixelMap。

   绘制PixelMap时需要通过Canva相关接口绘制位图，下文以drawImage()为例。更多方式和接口的使用请见[drawing.Canvas](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md)。

   drawImage()函数接受4个参数，第一个就是上文中创建的PixelMap，第二个是绘制图片位置的左上角x轴坐标，第三个是左上角y轴坐标，第四个为采样选项对象，默认为不使用任何参数构造的原始采样选项对象。

   <!-- @[arkts_graphics_draw_image_pixel_map](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/PixelMapDrawing.ets) -->

   绘制效果如下：

   ![zh-cn_image_0000002158584414](figures/zh-cn_image_0000002158584414.png)

<!--RP1-->
## 相关实例

针对Drawing(ArkTS)的开发，有以下相关实例可供参考：

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->