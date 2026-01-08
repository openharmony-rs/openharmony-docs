# Using ImagePacker to Encode Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image encoding refers to the process of compressing a PixelMap into different image file formats for the purpose of saving and transferring.

You can use [PackToData](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13-1) and [PackToFile](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11-2) to encode a PixelMap into JPEG, WebP, PNG, and HEIF images.

Starting from API version 18, you can use [PackToDataFromPixelmapSequence](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodatafrompixelmapsequence18) and [PackToFileFromPixelmapSequence](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofilefrompixelmapsequence18) to encode multiple PixelMaps into the GIF format.

## How to Develop

Read the [API reference](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md) for APIs related to image encoding.

### Encoding Images into File Streams

1. Import the required modules.
   
   <!-- @[encodingPixelMap_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/EncodingPixelMap.ets) -->   
   
   ``` TypeScript
   // Import the required module.
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. Set the [encoding options](../../reference/apis-image-kit/arkts-apis-image-i.md#packingoption).
   
   2.1 The JPEG image encoding is used as an example. The target format of the encoding follows the MIME standard definition. Therefore, **PackingOption.format** should be set to **image/jpeg**, and the encoded file name extension can be set to **.jpg** or **.jpeg**.
   
   <!-- @[create_packOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
   ```
   
   2.2 If the image source is HDR and you want to encode it as an HDR image file, you need to configure **desiredDynamicRange** additionally.
   
   <!-- @[packOpts_isHdr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   // If the resource is HDR and the device supports HDR encoding, the content is encoded in HDR. (This requires the resource to be HDR and the device to support HDR encoding and JPEG format.)
   packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
   ```

3. Encapsulate a function that takes **imageSource** or **pixelMap** as input, then use the [packToData](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13) API to encode the data into an **ArrayBuffer**, or use the [packToFile](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11) API to encode it into a file.
   
   > **NOTE**
   >
   > Before encoding, you need to obtain **imageSource** or **pixelMap** first. For details, please refer to [Using ImageSource to Decode Images](./image-decoding.md).
   
   - Encode the pixelMap into an **ArrayBuffer**.
     <!-- @[packToData_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function packToDataFromPixelMap(pixelMap : image.PixelMap) {
       const imagePackerApi = image.createImagePacker();
       let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
       // If the resource is HDR and the device supports HDR encoding, the content is encoded in HDR. (This requires the resource to be HDR and the device to support HDR encoding and JPEG format.)
       packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
       try{
         let data = await imagePackerApi.packToData(pixelMap, packOpts);
         // data is the file stream obtained after encoding. You can write the file and save it to obtain an image.
         copyData = new ArrayBuffer(0);
         copyData = data;
       } catch (error) {
         console.error('Failed to pack the pixelMap to data. And the error is: ' + error);
       }
     }
     ```
   
   - Encode the **imageSource** into an **ArrayBuffer**.
     <!-- @[packToData_imageSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  
     
     ``` TypeScript
     async function packToDataFromImageSource(imageSource : image.ImageSource) {
       const imagePackerApi = image.createImagePacker();
       let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
       try {
         let data = await imagePackerApi.packToData(imageSource, packOpts);
         // data is the file stream obtained after encoding. You can write the file and save it to obtain an image.
         copyData = new ArrayBuffer(0);
         copyData = data;
       } catch (error) {
         console.error('Failed to pack the imageSource to data. And the error is: ' + error);
       }
     }
     ```
   
   - Encode the **pixelMap** into a file.
     <!-- @[packToFile_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function packToFileFromPixelMap(context : Context, pixelMap : image.PixelMap) {
       const imagePackerApi = image.createImagePacker();
       let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
       const path : string = context.cacheDir + '/pixel_map.jpg';
       let file = fs.openSync(path, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
       try {
         await imagePackerApi.packToFile(pixelMap, file.fd, packOpts);
       } catch (error) {
         console.error('Failed to pack the pixelMap to file. And the error is: ' + error);
       }
     }
     ```
   
   - Encode the **imageSource** into a file.
     <!-- @[packToFile_imageSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function packToFileFromImageSource(context : Context, imageSource : image.ImageSource) {
       const imagePackerApi = image.createImagePacker();
       let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
       const filePath : string = context.cacheDir + '/image_source.jpg';
       let file = fs.openSync(filePath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
       try {
         await imagePackerApi.packToFile(imageSource, file.fd, packOpts);
       } catch (error) {
         console.error('Failed to pack the imageSource to file. And the error is: ' + error);
       }
     }
     ```

4. Save an image to Gallery.
   
After an image is encoded to an **ArrayBuffer** or file, you can use the relevant APIs of the [Media Library Kit](../medialibrary/photoAccessHelper-overview.md) to [save the media assets](../medialibrary/photoAccessHelper-savebutton.md) to Gallery.

<!--RP1-->
<!--RP1End-->
