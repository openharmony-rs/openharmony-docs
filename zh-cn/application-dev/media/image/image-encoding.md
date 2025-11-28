# 使用ImagePacker完成图片编码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图片编码指将PixelMap压缩成不同格式的图片文件，用于保存和传输。

支持使用[PackToData](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13-1)和[PackToFile](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11-2)将PixelMap编码为JPEG、WebP、PNG和HEIC格式。

从API version 18开始，支持使用[PackToDataFromPixelmapSequence](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodatafrompixelmapsequence18)和[PackToFileFromPixelmapSequence](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofilefrompixelmapsequence18)将多个PixelMap编码为GIF格式。

## 开发步骤

图片编码相关API的详细介绍请参见：[图片编码接口说明](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md)。

### 图片编码进文件流

1. 导入相关模块包。

   <!-- @[encodingPixelMap_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/EncodingPixelMap.ets) -->   

2. 创建图像编码ImagePacker对象。

   <!-- @[create_packer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

3. 设置编码输出流和编码参数。

    - format为图像的编码格式；quality为图像质量，范围为[0, 100]，100为最佳质量。

      > **说明：**
      > 根据MIME标准，标准编码格式为image/jpeg。当使用image编码时，PackingOption.format设置为image/jpeg，image编码后的文件扩展名可设为.jpg或.jpeg，可在支持image/jpeg解码的平台上使用。

      <!-- @[create_packOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

    - 编码为HDR内容。
      
      <!-- @[packOpts_isHdr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

4. 进行图片编码，并保存编码后的图片。

   方法一：通过PixelMap进行编码。

   <!-- @[packToData_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   方法二：通过imageSource进行编码。
   
   <!-- @[packToData_imageSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  

### 图片编码进文件

在编码时，开发者可以传入对应的文件路径，编码后的内存数据将直接写入文件。

- 方法一：通过PixelMap编码进文件。

  <!-- @[packToFile_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

- 方法二：通过imageSource编码进文件。

  <!-- @[packToFile_imageSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   

### 图片编码保存进图库

可以将图片编码保存到应用沙箱，然后使用媒体文件管理相关接口[保存媒体库资源](../medialibrary/photoAccessHelper-savebutton.md)。

<!--RP1-->
<!--RP1End-->