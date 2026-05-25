# 使用PixelMap完成图像变换

图片处理指对PixelMap进行相关的操作，如获取图片信息、裁剪、缩放、偏移、旋转、翻转、设置透明度、读写像素数据等。图片处理主要包括图像变换、[位图操作](image-pixelmap-operation.md)，本文介绍图像变换。

## 开发步骤

图像变换相关API的详细介绍请参见API参考[Interface (PixelMap)](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)。

1. 完成[图片解码](image-decoding.md)，获取PixelMap对象。

2. 获取图片信息。

   ArkTS-Dyn示例：

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';

   // 获取图片大小。
   pixelMap.getImageInfo().then((info: image.ImageInfo) => {
     console.info('info.width = ' + info.size.width);
     console.info('info.height = ' + info.size.height);
   }).catch((err: BusinessError) => {
     console.error("Failed to obtain the image pixel map information. And the error is: " + err);
   });
   ```

   ArkTS-Sta示例：

   <!-- @[pixelmap_get_image_info](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取图片大小。
   await this.pixelMap!.getImageInfo().then((info: image.ImageInfo) => {
     this.imageInfo = info;
     Logger.info('Image width: ', info.size.width.toString());
     Logger.info('Image height: ', info.size.height.toString());
   }).catch((err) => {
     Logger.error('Failed to obtain the image information. The error is: ', String(err));
   });
   ```

3. 进行图像变换操作。

   原图：

   ![Original drawing](figures/original-drawing.jpeg)

   - 裁剪

     ArkTS-Dyn示例：

     ```ts
     // x：裁剪起始点横坐标0。
     // y：裁剪起始点纵坐标0。
     // height：裁剪高度400，方向为从上往下（裁剪后的图片高度为400）。
     // width：裁剪宽度400，方向为从左到右（裁剪后的图片宽度为400）。
     pixelMap.crop({ x: 0, y: 0, size: { height: 400, width: 400 } });
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_crop_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // x：裁剪起始点横坐标0。
     // y：裁剪起始点纵坐标0。
     // height：裁剪高度400，方向为从上往下（裁剪后的图片高度为400）。
     // width：裁剪宽度400，方向为从左到右（裁剪后的图片宽度为400）。
     this.pixelMap!.crop({ x: 0, y: 0, size: { height: 400, width: 400 } }).then(() => {
       // ...
     });
     ```

     ![cropping](figures/cropping.jpeg)

   - 缩放

     ArkTS-Dyn示例：

     ```ts
     // 宽为原来的0.5。
     // 高为原来的0.5。
     pixelMap.scale(0.5, 0.5);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_scale_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 宽为原来的0.5倍。
     // 高为原来的0.5倍。
     this.pixelMap!.scale(0.5, 0.5).then(() => {
       // ...
     });
     ```

     ![zoom](figures/zoom.jpeg)

   - 平移

     ArkTS-Dyn示例：

     ```ts
     // 向下平移100。
     // 向右平移100。
     pixelMap.translate(100, 100);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_translate_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 向下平移100。
     // 向右平移100。
     this.pixelMap!.translate(100, 100).then(() => {
       // ...
     });
     ```

     ![offsets](figures/offsets.jpeg)

   - 旋转

     ArkTS-Dyn示例：

     ```ts
     // 顺时针旋转90°。
     pixelMap.rotate(90);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_rotate_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 顺时针旋转90°。
     this.pixelMap!.rotate(90).then(() => {
       // ...
     });
     ```

     ![rotate](figures/rotate.jpeg)

   - 翻转

     ArkTS-Dyn示例：

     ```ts
     // 垂直翻转。
     pixelMap.flip(false, true);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_vertical_flip_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 垂直翻转。
     this.pixelMap!.flip(false, true).then(() => {
       // ...
     });
     ```

     ![Vertical Flip](figures/vertical-flip.jpeg)

     ArkTS-Dyn示例：

     ```ts
     // 水平翻转。
     pixelMap.flip(true, false);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_horizontal_flip_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 水平翻转。
     this.pixelMap!.flip(true, false).then(() => {
       // ...
     });
     ```

     ![Horizontal Flip](figures/horizontal-flip.jpeg)

   - 透明度

     ArkTS-Dyn示例：

     ```ts
     // 透明度0.5。
     pixelMap.opacity(0.5);
     ```

     ArkTS-Sta示例：

     <!-- @[pixelmap_change_opacity_image](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Image/PixelMap_Static/entry/src/main/ets/pages/Index.ets) -->
     
     ``` TypeScript
     // 所有像素的透明度改为0.5。
     this.pixelMap!.opacity(0.5).then(() => {
       // ...
     });
     ```

     ![Transparency](figures/transparency.png)

<!--RP1-->
<!--RP1End-->