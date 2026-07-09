# 使用PixelMap完成图像变换
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yaozhupeng-->
<!--Designer: @yaozhupeng-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @w_Machine_cc-->

图片处理指对PixelMap进行相关的操作，如获取图片信息、裁剪、缩放、偏移、旋转、翻转、设置透明度、读写像素数据等。图片处理主要包括图像变换、[位图操作](image-pixelmap-operation.md)，本文介绍图像变换。

## 开发步骤

图像变换相关API的详细介绍请参见[Interface (PixelMap)](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)。

1. 完成[图片解码](image-decoding.md)，获取PixelMap对象。

2. 获取图片信息。

   <!-- @[pixelmap_get_image_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取图片大小。
   await this.pixelMap.getImageInfo().then((info: image.ImageInfo) => {
     this.imageInfo = info;
     Logger.info('Image width: ', info.size.width.toString());
     Logger.info('Image height: ', info.size.height.toString());
   }).catch((err: BusinessError) => {
     Logger.error('Failed to obtain the image pixel map information. The error is: ', String(err));
   });
   ```

3. 进行图像变换操作。

   原图：

   ![Original drawing](figures/original-drawing.jpeg)

   - 裁剪

     <!-- @[pixelmap_crop_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     const imageInfo = this.pixelMap.getImageInfoSync();
     const cropWidth = Math.min(400, imageInfo.size.width); // 原图宽度小于400时防止裁剪区域超出范围。
     const cropHeight = Math.min(400, imageInfo.size.height); // 原图高度小于400时防止裁剪区域超出范围。
     // x：裁剪起始点横坐标0。
     // y：裁剪起始点纵坐标0。
     // width：原图宽度不小于400时，裁剪宽度400，方向为从左到右（裁剪后的图片宽度为400）。
     // height：原图高度不小于400时，裁剪高度400，方向为从上往下（裁剪后的图片高度为400）。
     this.pixelMap.crop({ x: 0, y: 0, size: { width: cropWidth, height: cropHeight } }).then(() => {
       // ...
     });
     ```

     ![cropping](figures/cropping.jpeg)

   - 缩放

     <!-- @[pixelmap_scale_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 宽为原来的0.5倍。
     // 高为原来的0.5倍。
     this.pixelMap.scale(0.5, 0.5).then(() => {
       // ...
     });
     ```

     ![zoom](figures/zoom.jpeg)

   - 平移

     <!-- @[pixelmap_translate_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 向下平移100。
     // 向右平移100。
     this.pixelMap.translate(100, 100).then(() => {
       // ...
     });
     ```

     ![offsets](figures/offsets.jpeg)

   - 旋转

     <!-- @[pixelmap_rotate_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 顺时针旋转90°。
     this.pixelMap.rotate(90).then(() => {
       // ...
     });
     ```

     ![rotate](figures/rotate.jpeg)

   - 翻转

     <!-- @[pixelmap_vertical_flip_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 垂直翻转。
     this.pixelMap.flip(false, true).then(() => {
       // ...
     });
     ```

     ![Vertical Flip](figures/vertical-flip.jpeg)

     <!-- @[pixelmap_horizontal_flip_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 水平翻转。
     this.pixelMap.flip(true, false).then(() => {
       // ...
     });
     ```

     ![Horizontal Flip](figures/horizontal-flip.jpeg)

   - 透明度

     <!-- @[pixelmap_change_opacity_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/PixelMap/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 将所有像素的透明度改为0.5。
     this.pixelMap.opacity(0.5).then(() => {
       // ...
     });
     ```

     ![Transparency](figures/transparency.png)

<!--RP1-->
<!--RP1End-->