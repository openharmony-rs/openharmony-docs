# 使用ImageSource完成多图对象解码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

将所支持格式的图片文件解码成[Picture](image-overview.md#基础概念)。当前支持的图片文件格式包括JPEG、HEIF。

## 开发步骤

图片解码相关API的详细介绍请参见：[图片解码接口说明](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md)。

1. 全局导入Image模块。

   <!-- @[decodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPicture.ets) -->   
   
   ``` TypeScript
   // 导入相关模块包。
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. 获取图片。
   - 方法一：通过沙箱路径直接获取。该方法仅适用于应用沙箱中的图片。更多细节请参考[获取应用文件路径](../../application-models/application-context-stage.md#获取应用文件路径)。应用沙箱的介绍及如何向应用沙箱推送文件，请参考[文件管理](../../file-management/app-sandbox-directory.md)。

     <!-- @[get_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

   - 方法二：通过沙箱路径获取图片的文件描述符。具体请参考[file.fs API参考文档](../../reference/apis-core-file-kit/js-apis-file-fs.md)。该方法需要导入\@kit.CoreFileKit模块。
   
     <!-- @[get_fileFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     function getFileFd(context: Context, fileName: string): number | undefined {
       const filePath: string = context.cacheDir + '/' + fileName;
       const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
       const fd: number = file?.fd;
       return fd;
     }
     ```
   
   - 方法三：通过资源管理器获取资源文件的ArrayBuffer。具体请参考[资源管理器API参考文档](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfilecontent9-1)。该方法需要导入\@kit.LocalizationKit模块。
   
     <!-- @[get_fileBuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   - 方法四：通过资源管理器获取资源文件的RawFileDescriptor。具体请参考[资源管理器API参考文档](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9-1)。该方法需要导入\@kit.LocalizationKit模块。
     
     <!-- @[get_RawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

3. 创建ImageSource实例。

   - 方法一：通过沙箱路径创建ImageSource。沙箱路径可以通过步骤2的方法一获取。

     <!-- @[createImageSource_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

   - 方法二：通过文件描述符fd创建ImageSource。文件描述符可以通过步骤2的方法二获取。

     <!-- @[createImageSource_fd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  

   - 方法三：通过缓冲区数组创建ImageSource。缓冲区数组可以通过步骤2的方法三获取。

     <!-- @[createImageSource_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  

   - 方法四：通过资源文件的RawFileDescriptor创建ImageSource。RawFileDescriptor可以通过步骤2的方法四获取。

     <!-- @[createImageSource_rawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

4. 设置解码参数DecodingOptions，解码获取picture多图对象。并对picture进行操作，如获取辅助图等。对于picture和辅助图的操作具体请参考[Image API参考文档](../../reference/apis-image-kit/arkts-apis-image-Picture.md)。

   配置解码选项参数进行解码：

   <!-- @[create_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

5. 释放picture。

   确认picture的异步方法已经执行完成，不再使用该变量后，可按需手动调用下面方法释放。
   
   <!-- @[release_pictureDecoder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
