# Editing Exif Data
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image Kit provides the capabilities of reading and editing Exchangeable Image File Format (Exif) data.

Exif is a file format dedicated for photos taken by digital cameras and is used to record attributes and shooting data of the photos. Currently, JPEG, PNG, HEIF, and WEBP<sup>23+</sup> images that contain Exif data are supported.

Users may need to view or modify the Exif data of photos in the Gallery application. When the manual lens parameters of the camera are not automatically written as part of the Exif data or the shooting time is incorrect due to camera power-off, you can manually correct the Exif data.

Currently, OpenHarmony allows you to view and modify part of Exif data. For details, see [Exif](../../reference/apis-image-kit/arkts-apis-image-e.md#propertykey7).

## How to Develop

Read the [API reference](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#getimageproperty11) for APIs used to read and edit Exif data.

Obtain the image and create an ImageSource object. Read and edit Exif data. The code snippet is as follows:

1. Import the required modules.

   <!-- @[editExif_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/ExifUtility.ets) -->   
   
   ``` TypeScript
   // Import the required module.
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Obtain the Exif data of a specified key.

   <!-- @[get_exif](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/ExifUtility.ets) -->   
   
   ``` TypeScript
   // Example for obtaining Exif data of a specified key.
   async getExif(imageSourceApi: image.ImageSource | undefined, key: image.PropertyKey): Promise<string> {
     let info: string = '';
     if (imageSourceApi) {
       console.info('getExif: The imageSourceApi is not undefined.');
       // Obtain Exif data of a specified key.
       let options: image.ImagePropertyOptions = { index: 0, defaultValue: 'This key has no value!' };
       try {
         let data = await imageSourceApi.getImageProperty(key, options);
         info = `Succeeded in getting the ${key}'s value: ${data}.`;
         console.info(info);
         return info; // Return the key if it is obtained successfully.
       } catch (error) {
         info =
           `Failed to get the value of the ${key} with error: ${error}.`;
         console.error(info);
         return info; // Return an error message if the key fails to be obtained.
       }
     } else {
       info = 'getExif: The imageSourceApi is undefined.';
       console.info(info);
       return info; // Return the information if imageSourceApi is undefined.
     }
   }
   ```

3. Modify Exif data of a specified key.

   <!-- @[modify_exif](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/ExifUtility.ets) -->   
   
   ``` TypeScript
   // Example for modifying Exif data of a specified key.
   async modifyExif(imageSourceApi: image.ImageSource | undefined, key: image.PropertyKey, value: string)
     : Promise<string> {
     let info: string = '';
     if (imageSourceApi) {
       // Edit the Exif data.
       try {
         await imageSourceApi.modifyImageProperty(key, value);
         try {
           let modifyValue = await imageSourceApi.getImageProperty(key)
           info = `The ${key}'s value is modified to ${modifyValue}.`
           console.info(info);
           return info; // Return a success message if the key is obtained successfully.
         } catch (error) {
           console.error(`Failed to get the the ${key}'s value with ${error}`);
           console.error(info);
           return info; // Return an error message if the key fails to be obtained.
         }
       } catch (error) {
         info = `Failed to modify the ${key}'s value with ${error}`;
         console.error(info);
         return info; // Return an error message if the key fails to be modified.
       }
     } else {
       info = 'modifyExif: The imageSourceApi is undefined.';
       console.info(info);
       return info; // Return the information if imageSourceApi is undefined.
     }
   }
   ```
