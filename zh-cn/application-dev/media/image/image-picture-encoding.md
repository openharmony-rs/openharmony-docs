# 使用ImagePacker完成多图对象编码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图片编码指将Picture对象编码成不同格式的图片文件（当前仅支持编码为JPEG 和 HEIF 格式），用于后续处理，如保存、传输等。

## 开发步骤

图片编码相关API的详细介绍请参见：[图片编码接口说明](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md)。

1. 导入相关模块包。

   <!-- @[encodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/EncodingPicture.ets) -->   
   
   ``` TypeScript
   // 导入相关模块包。
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. 创建图像编码ImagePacker对象。

   <!-- @[create_picturePacker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   const imagePackerApi = image.createImagePacker();
   ```

3. 设置编码输出流和编码参数。

   format为图像的编码格式；quality为图像质量，范围为[0, 100]，100为最佳质量。

   > **说明：**
   > 根据MIME标准，标准编码格式为image/jpeg。当使用image编码时，PackingOption.format设置为image/jpeg，image编码后的文件扩展名可设为.jpg或.jpeg，可在支持image/jpeg解码的平台上使用。

   <!-- @[create_picturePackOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   let packOpts: image.PackingOption = {
     format: 'image/jpeg',
     quality: 95,
     desiredDynamicRange: image.PackingDynamicRange.AUTO,
     needsPackProperties: true
   };
   ```
   
### 图片编码进文件流
进行图片编码，并保存编码后的data。在进行编码前，需要先通过解码获取picture，可参考[使用ImageSource完成多图对象解码](./image-picture-decoding.md)。

<!-- @[packToData_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

``` TypeScript
async function packing(picture: image.Picture, packOpts: image.PackingOption) {
  const imagePackerApi = image.createImagePacker();
  try {
    let data = await imagePackerApi.packing(picture, packOpts);
    copyData = data;
    console.info('Succeeded in packing the image.');
  } catch (error) {
    console.error('Failed to pack the picture to data. And the error is: ' + error);
  }
}
```

### 图片编码进文件

在进行编码前，开发者需要先通过解码获取picture，具体操作可参考[使用ImageSource完成多图对象解码](./image-picture-decoding.md)。

在编码时，开发者可以先定义对应的输出文件路径，然后将编码后的内存数据写入文件。

<!-- @[packToFile_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

``` TypeScript
async function packToFile(picture: image.Picture, packOpts: image.PackingOption, context: Context) {
  const path : string = context.cacheDir + '/picture.jpg';
  let file = fs.openSync(path, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
  const imagePackerApi = image.createImagePacker();
  try {
    await imagePackerApi.packToFile(picture, file.fd, packOpts);
  } catch (error) {
    console.error('Failed to pack the picture to file. And the error is: ' + error);
  }
}
```

