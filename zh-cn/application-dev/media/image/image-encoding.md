# 使用ImagePacker完成图片编码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

图片编码指将PixelMap编码成不同格式的图片文件，当前支持编码为JPEG、WebP、PNG和 HEIF（不同硬件设备支持情况不同）格式，用于后续处理，如保存、传输等。

## 开发步骤

图片编码相关API的详细介绍请参见：[图片编码接口说明](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md)。

### 图片编码进文件流

1. 创建图像编码ImagePacker对象。

   ```ts
   // 导入相关模块包。
   import { image } from '@kit.ImageKit';
   
   const imagePackerApi = image.createImagePacker();
   ```

2. 设置编码输出流和编码参数。

    - format为图像的编码格式；quality为图像质量，范围从0-100，100为最佳质量。

      > **说明：**
      > 根据MIME标准，标准编码格式为image/jpeg。当使用image编码时，PackingOption.format设置为image/jpeg，image编码后的文件扩展名可设为.jpg或.jpeg，可在支持image/jpeg解码的平台上使用。

      ```ts
      let packOpts : image.PackingOption = { format:"image/jpeg", quality:98 };
      ```

    - 编码为hdr内容(需要资源本身为hdr，支持jpeg格式)。
      ```ts
      packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
      ```

3. 创建PixelMap对象或创建ImageSource对象。
   ```ts
   import { common } from '@kit.AbilityKit';

   // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
   let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
   //此处'test.jpg'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
   const path: string = context.filesDir + "/test.jpg";
   const imageSource: image.ImageSource = image.createImageSource(path);
   let decodingOptions : image.DecodingOptions = { editable: true, desiredPixelFormat: image.PixelMapFormat.RGBA_8888 };
   let pixelmap = imageSource.createPixelMapSync(decodingOptions);
   ```

4. 进行图片编码，并保存编码后的图片。

   方法一：通过PixelMap进行编码。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   imagePackerApi.packToData(pixelMap, packOpts).then( (data : ArrayBuffer) => {
     // data 为编码获取到的文件流，写入文件保存即可得到一张图片。
   }).catch((error : BusinessError) => { 
     console.error('Failed to pack the image. And the error is: ' + error); 
   })
   ```

   方法二：通过imageSource进行编码。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   imagePackerApi.packToData(imageSource, packOpts).then( (data : ArrayBuffer) => {
       // data 为编码获取到的文件流，写入文件保存即可得到一张图片。
   }).catch((error : BusinessError) => { 
     console.error('Failed to pack the image. And the error is: ' + error); 
   })
   ```

### 图片编码进文件

在编码时，开发者可以传入对应的文件路径，编码后的内存数据将直接写入文件。

   方法一：通过PixelMap编码进文件。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   const path : string = context.cacheDir + "/pixel_map.jpg";
   let file = fs.openSync(path, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
   imagePackerApi.packToFile(pixelMap, file.fd, packOpts).then(() => {
       // 直接编码进文件。
   }).catch((error : BusinessError) => { 
     console.error('Failed to pack the image. And the error is: ' + error); 
   }).finally(()=>{
     fs.closeSync(file.fd);
   })
   ```

   方法二：通过imageSource编码进文件。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   const filePath : string = context.cacheDir + "/image_source.jpg";
   let file = fs.openSync(filePath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
   imagePackerApi.packToFile(imageSource, file.fd, packOpts).then(() => {
       // 直接编码进文件。
   }).catch((error : BusinessError) => { 
     console.error('Failed to pack the image. And the error is: ' + error); 
   }).finally(()=>{
     fs.closeSync(file.fd);
   })
   ```

### 图片编码保存进图库

可以将图片编码保存到应用沙箱，然后使用媒体文件管理相关接口[保存媒体库资源](../medialibrary/photoAccessHelper-savebutton.md)。

<!--RP1-->
<!--RP1End-->