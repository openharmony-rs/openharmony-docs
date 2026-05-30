# Using ImageSource to Decode Pictures
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image decoding refers to the process of decoding an image in a supported format (JPEG and HEIF currently) into a [picture](image-overview.md#basic-concepts).  

## How to Develop

Read the [API reference](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md) for APIs related to image decoding.

1. Import the image module.

   <!-- @[decodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPicture.ets) -->   
   
   ``` TypeScript
   // Import the required modules.
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. Obtain an image.
   - Method 1: Directly obtain the image through the sandbox path. This method applies only to images in the application sandbox path. For details about how to obtain the sandbox path, see [Obtaining Application File Paths](../../application-models/application-context-stage.md#obtaining-application-file-paths). For details about the application sandbox and how to push files to the application sandbox directory, see [File Management](../../file-management/app-sandbox-directory.md).

     <!-- @[get_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     function getFilePath(context: Context, fileName: string): string {
       const filePath: string = context.cacheDir + '/' + fileName;
       return filePath;
     }
     ```

   - Method 2: Obtain the file descriptor of the image through the sandbox path. For details, see [file.fs API Reference](../../reference/apis-core-file-kit/js-apis-file-fs.md). To use this method, you must import the \@kit.CoreFileKit module first.
   
     <!-- @[get_fileFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     function getFileFd(context: Context, fileName: string): number | undefined {
       const filePath: string = context.cacheDir + '/' + fileName;
       const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
       const fd: number = file?.fd;
       return fd;
     }
     ```
   
   - Method 3: Obtain the array buffer of the resource file through the resource manager. For details, see [ResourceManager API Reference](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfilecontent9-1). To use this method, you must import the \@kit.LocalizationKit module first.
   
     <!-- @[get_fileBuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     async function getFileBuffer(context: Context, fileName: string): Promise<ArrayBuffer | undefined> {
       try {
         const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
         // Obtain the resource file content. The Uint8Array is returned.
         const fileData: Uint8Array = await resourceMgr.getRawFileContent(fileName);
         console.info('Successfully get the RawFileContent.');
         // Convert the array to an ArrayBuffer and return the ArrayBuffer.
         const buffer: ArrayBuffer = fileData.buffer.slice(0);
         return buffer;
       } catch (error) {
         console.error(`Failed to get the RawFileContent with error: ${error}.`);
         return undefined;
       }
     }
     ```
   
   - Method 4: Obtain the raw file descriptor of the resource file through the resource manager. For details, see [ResourceManager API Reference](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9-1). To use this method, you must import the \@kit.LocalizationKit module first.
     
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

3. Create an ImageSource instance.

   - Method 1: Create an ImageSource instance using the sandbox path. The sandbox path can be obtained by using method 1 in step 2.

     <!-- @[createImageSource_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // path indicates the obtained sandbox path.
     const imageSource : image.ImageSource = image.createImageSource(filePath);
     ```

   - Method 2: Create an ImageSource instance using the file descriptor. The file descriptor can be obtained by using method 2 in step 2.

     <!-- @[createImageSource_fd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  
     
     ``` TypeScript
     // fd is the obtained file descriptor.
     const imageSource: image.ImageSource = image.createImageSource(fd);
     ```

   - Method 3: Create an ImageSource instance using an array buffer. The array buffer can be obtained by using method 3 in step 2.

     <!-- @[createImageSource_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->  
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(buffer);
     ```

   - Method 4: Create an ImageSource instance using the raw file descriptor of the resource file. The raw file descriptor can be obtained by using method 4 in step 2.

     <!-- @[createImageSource_rawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(rawFileDescriptor);
     ```

4. Set **DecodingOptions** and decode the image to obtain a picture. Manipulate the picture, for example, obtaining an auxiliary picture. For details about how to manipulate a picture and auxiliary picture, see [Image API](../../reference/apis-image-kit/arkts-apis-image-Picture.md).

   Carry out decoding after the setting.

   <!-- @[create_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   async createPicture(imageSource : image.ImageSource | undefined, isReturnAux: Boolean)
     : Promise<image.PixelMap | undefined | image.Picture> {
     // Set the decoding options.
     let options: image.DecodingOptionsForPicture = {
       desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP] // GAINMAP indicates the type of the auxiliary picture to be decoded.
     };
     let returnPixelMap: image.PixelMap | undefined = undefined;
     // Create a Picture instance.
     try {
       let picture = await imageSource?.createPicture(options);
       if (picture) {
         // Return the auxiliary picture obtained after decoding.
         if (isReturnAux) {
           // type is the type of the auxiliary picture contained in the decoding options.
           let type: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
           let auxPicture: image.AuxiliaryPicture | null = picture.getAuxiliaryPicture(type);
           // Obtain the information of the auxiliary picture.
           if (auxPicture != null) {
             let auxInfo: image.AuxiliaryPictureInfo = auxPicture.getAuxiliaryPictureInfo();
             console.info('GetAuxiliaryPictureInfo type: ' + auxInfo.auxiliaryPictureType +
               ' height: ' + auxInfo.size.height + ' width: ' + auxInfo.size.width +
               ' rowStride: ' + auxInfo.rowStride + ' pixelFormat: ' + auxInfo.pixelFormat +
               ' colorSpace: ' + auxInfo.colorSpace);
             // Read data of the auxiliary picture and write the data to an ArrayBuffer.
             try {
               let pixelsBuffer = await auxPicture.readPixelsToBuffer();
               let opts: image.InitializationOptions = { size: auxInfo.size };
               try {
                 returnPixelMap = image.createPixelMapSync(pixelsBuffer, opts) as image.PixelMap;
                 console.info(`Create PixelMap with buffer successfully.`);
               } catch (error) {
                 console.error(`Create PixelMap failed with ${error}.`);
               }
             } catch (error) {
               console.error(`Read pixels to buffer failed, error.code: ${error.code},
                 error.message: ${error.message}`);
             }
             auxPicture.release();
           }
           return returnPixelMap;
         } else {
           return picture; // Return the decoded Picture instance.
         }
       }
       return returnPixelMap;
     } catch (error) {
       console.error(`Create picture failed: ${error}.`);
     }
     return returnPixelMap;
   }
   ```

5. Release the Picture instance.

   Ensure that the asynchronous operations of the Picture instance have finished executing. After these variables are no longer needed, you can manually call the APIs below to release it.
   
   <!-- @[release_pictureDecoder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   async release(picture: image.Picture) {
     picture?.release();
   }
   ```
