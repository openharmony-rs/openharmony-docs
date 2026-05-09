# 使用ImageSource获取RAW数据

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图像的 RAW 数据是直接从图像传感器获取的原始数据，完整保留了所有传感器信息且无任何压缩损失。通过使用RAW数据，开发者可以获得最高质量的图像信息，并根据具体需求自定义图像处理算法，实现更灵活的图像处理和优化效果。

从API version 24开始，支持将符合格式的图片文件解码为[ImageRawData](../../reference/apis-image-kit/arkts-apis-image-i.md#imagerawdata24)，以便在应用或系统中获取RAW数据。RAW数据包含图像缓冲区和像素位数。

当前支持的图片文件格式为DNG。

## 开发步骤

获取图片RAW数据相关API的详细介绍请参见：[createImageRawData](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#createimagerawdata24)。

1. 全局导入Image模块，根据实际需求导入对应的Kit模块。
   
   <!-- @[decodingPixelMap_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->   
   
   ``` TypeScript
   // 导入相关模块。
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. 获取图片。
   - 方法一：通过沙箱路径直接获取，此方法**仅适用**于应用沙箱中的图片。获取方式请参考[获取应用文件路径](../../application-models/application-context-stage.md#获取应用文件路径)。
     
     <!-- @[get_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     function getFilePath(context: Context, fileName: string): string {
       const filePath: string = context.cacheDir + '/' + fileName;
       return filePath;
     }
     ```

   - 方法二：通过沙箱路径获取图片的文件描述符。具体请参考[@ohos.file.fs (文件管理)](../../reference/apis-core-file-kit/js-apis-file-fs.md)文档。该方法需要导入\@kit.CoreFileKit模块。
   
     <!-- @[get_fileFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     function getFileFd(context: Context, fileName: string): number | undefined {
       try {
         const filePath: string = context.cacheDir + '/' + fileName;
         const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_ONLY);
         const fd: number = file?.fd;
         return fd;
       } catch (err) {
         console.error(`Failed to get the fileFd with error: ${err}.`);
         return undefined;
       }
     }
     ```
      
   - 方法三：通过资源管理器获取资源文件的ArrayBuffer。具体请参考[getRawFileContent](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfilecontent9-1)接口。该方法需要导入\@kit.LocalizationKit模块。

     <!-- @[get_fileBuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function getFileBuffer(context: Context, fileName: string): Promise<ArrayBuffer | undefined> {
       try {
         const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
         // 获取资源文件内容，返回Uint8Array。
         const fileData: Uint8Array = await resourceMgr.getRawFileContent(fileName);
         console.info('Successfully get the RawFileContent.');
         // 转为ArrayBuffer并返回。
         const buffer: ArrayBuffer = fileData.buffer.slice(0);
         return buffer;
       } catch (error) {
         console.error(`Failed to get the RawFileContent with error: ${error}.`);
         return undefined;
       }
     }
     ```
      
   - 方法四：通过资源管理器获取资源文件的RawFileDescriptor。具体请参考[getRawFd](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9-1)接口。该方法需要导入\@kit.LocalizationKit模块。
   
     <!-- @[get_RawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function getRawFd(context: Context, fileName: string): Promise<resourceManager.RawFileDescriptor | undefined> {
       try {
         const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
         const rawFileDescriptor: resourceManager.RawFileDescriptor = await resourceMgr.getRawFd(fileName);
         console.info('Successfully get the RawFileDescriptor.');
         return rawFileDescriptor;
       } catch (error) {
         console.error(`Failed to get the RawFileDescriptor with error: ${error}.`);
         return undefined;
       }
     }
     ```
   
3. 创建ImageSource实例。

   - 方法一：通过沙箱路径创建ImageSource。沙箱路径可以通过步骤2的方法一获取。

     <!-- @[createImageSource_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // path为已获得的沙箱路径。
     const imageSource : image.ImageSource = image.createImageSource(filePath);
     ```

   - 方法二：通过文件描述符fd创建ImageSource。文件描述符可以通过步骤2的方法二获取。

     <!-- @[createImageSource_fd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // fd为已获得的文件描述符。
     const imageSource: image.ImageSource = image.createImageSource(fd);
     ```

   - 方法三：通过缓冲区数组创建ImageSource。缓冲区数组可以通过步骤2的方法三获取。

     <!-- @[createImageSource_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(buffer);
     ```

   - 方法四：通过资源文件的RawFileDescriptor创建ImageSource。RawFileDescriptor可以通过步骤2的方法四获取。

     <!-- @[createImageSource_rawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(rawFileDescriptor);
     ```

4. 获取ImageRawData图片对象并打印像素值。

   <!-- @[createImageRawData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   async  createImageRawData(imageSource: image.ImageSource | undefined) : Promise<image.ImageRawData | undefined> {
     if (!imageSource) {
       console.error('imageSource is undefined.');
       return undefined;
     }
     await imageSource.createImageRawData().then((data: image.ImageRawData) => {
       let array: Uint16Array = new Uint16Array();
       if (data.bitsPerPixel == 16 && data.buffer) {
         array = new Uint16Array(data.buffer);
       }
       let length = array.byteLength.valueOf();
       console.info(`uint16Array length: ${length}`);
       let value: string = '';
       for (let i = 0; i < array.length && i < 10; i++) {
         value += array[i] + ', ';
       }
       console.info(`get dng rawdata is:${value}.`);
       return data
     }).catch((err: BusinessError) => {
       console.error(`get dng rawdata failed.err: ${JSON.stringify(err)}`);
       return undefined;
     })
     return undefined;
   }
   ```
   
5. 释放imageSource。

   确认imageSource的异步方法已经执行完成，不再使用该变量后，可按需手动调用下面方法释放。

   <!-- @[release_pixelMapDecoder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->   
   
   ``` TypeScript
   async release(pixelMap: image.PixelMap | undefined, imageSource: image.ImageSource | undefined) {
     pixelMap?.release();
     pixelMap = undefined;
     imageSource?.release();
     imageSource = undefined;
   }
   ```