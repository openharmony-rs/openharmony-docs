# Using ImagePacker to Encode Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image encoding refers to the process of compressing a PixelMap into different image file formats for the purpose of saving and transferring.

You can use [PackToData](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13-1) and [PackToFile](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11-2) to encode a PixelMap into JPEG, WebP, PNG, and HEIC images.

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

2. Create an ImagePacker object.

   <!-- @[create_packer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   const imagePackerApi = image.createImagePacker();
   ```

3. Set the encoding output stream and encoding parameters.

   - **format** indicates the image encoding format, and **quality** indicates the image quality. The value range is [0, 100], and the value 100 indicates the optimal quality.

     > **NOTE**
     >
     > According to the MIME protocol, the standard encoding format is image/jpeg. When the APIs provided by the image module are used for encoding, **PackingOption.format** must be set to **image/jpeg**. The file name extension of the encoded image file can be .jpg or .jpeg, and the file can be used on platforms that support image/jpeg decoding.

     <!-- @[create_packOpts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     let packOpts : image.PackingOption = { format: 'image/jpeg', quality: 95 };
     ```

   - Encode HDR content.
      
     <!-- @[packOpts_isHdr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // If the resource is HDR and the device supports HDR encoding, the content is encoded in HDR. (This requires the resource to be HDR and the device to support HDR encoding and JPEG format.)
     packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
     ```

4. Encode the image and save the encoded image.

   Method 1: Use **PixelMap** for encoding.

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
   
   Method 2: Use **ImageSource** for encoding.
   
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

### Encoding Images into Files

During encoding, you can pass in a file path so that the encoded memory data is directly written to the file.

- Method 1: Use **PixelMap** to encode the image and pack it into a file.

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

- Method 2: Use **ImageSource** to encode the image and pack it into a file.

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

### Saving Encoded Images to Gallery

You can save the encoded image to the application sandbox, and use the media file management APIs to [save media library resources](../medialibrary/photoAccessHelper-savebutton.md).

<!--RP1-->
<!--RP1End-->
