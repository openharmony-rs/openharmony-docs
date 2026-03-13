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

2. Create an ImagePacker object.

   <!-- @[create_picturePacker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   const imagePackerApi = image.createImagePacker();
   ```

3. Set the encoding output stream and encoding parameters.

   **format** indicates the image encoding format, and **quality** indicates the image quality. The value range is [0, 100], and the value 100 indicates the optimal quality.

   > **NOTE**
   >
   > According to the MIME protocol, the standard encoding format is image/jpeg. When the APIs provided by the image module are used for encoding, **PackingOption.format** must be set to **image/jpeg**. The file name extension of the encoded image file can be .jpg or .jpeg, and the file can be used on platforms that support image/jpeg decoding.

   <!-- @[create_picturePackOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   let packOpts: image.PackingOption = {
     format: 'image/jpeg',
     quality: 95,
     desiredDynamicRange: image.PackingDynamicRange.AUTO,
     needsPackProperties: true
   };
   ```
   
### Encoding Images into File Streams

Encode the image and save the encoded data. Before encoding, you need to obtain a Picture object through decoding. For details, see [Using ImageSource to Decode Pictures](./image-picture-decoding.md).

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

### Encoding Images into Files

Before encoding, you need to obtain a Picture object through decoding. For details, see [Using ImageSource to Decode Pictures](./image-picture-decoding.md).

During encoding, you can define the output file path and write the encoded memory data to the file.

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
