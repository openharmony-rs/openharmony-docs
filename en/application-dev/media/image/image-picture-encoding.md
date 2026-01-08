# Using ImagePacker to Encode Pictures
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image encoding refers to the process of encoding a picture into an image in different formats (only in JPEG and HEIF currently) for subsequent processing, such as storage and transmission.

## How to Develop

Read the [API reference](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md) for APIs related to image encoding.

1. Import the required modules.
   
   <!-- @[encodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/EncodingPicture.ets) -->   
   
   ``` TypeScript
   // Import the required modules.
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. Set the [encoding options](../../reference/apis-image-kit/arkts-apis-image-i.md#packingoption).
   
   > **NOTE**
   >
   > The JPEG image encoding is used as an example. The target format of the encoding follows the MIME standard definition. Therefore, **PackingOption.format** should be set to **image/jpeg**, and the encoded file name extension can be set to **.jpg** or **.jpeg**.
   
   <!-- @[create_picturePackOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   let packOpts: image.PackingOption = {
     format: 'image/jpeg',
     quality: 95,
     desiredDynamicRange: image.PackingDynamicRange.AUTO,
     needsPackProperties: true
   };
   ```

3. Encapsulate a function that takes **picture** as input, then use the [packing](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packing13) API to encode the data into an **ArrayBuffer**, or use the [packToFile](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11-2) API to encode it into a file.
   
   > **NOTE**
   >
   > Before encoding, you need to obtain a Picture object through decoding. For details, see [Using ImageSource to Decode Pictures](./image-picture-decoding.md).
   
   - Encode the **picture** object into an **ArrayBuffer**.
   
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
   
   - Encode the **picture** object into a file.
   
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
