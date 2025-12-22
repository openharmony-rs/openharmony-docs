# Using ImageSource to Decode Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image decoding refers to the process of decoding an image in a supported format into a [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) for image display or processing. Currently, the following image formats are supported: JPEG, PNG, GIF, WebP, BMP, SVG, ICO, DNG, HEIC, and WBMP (supported since API version 23). The supported formats may vary depending on the hardware.

Starting from API version 22, thumbnail decoding is provided for images in various professional camera formats. The formats supported are CR2, CR3, ARW, NEF, RAF, NRW, ORF, RW2, PEF, and SRW.

## How to Develop

Read the [API reference](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md) for APIs related to image decoding.

1. Import the image module.
   
   <!-- @[decodingPixelMap_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->   
   
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

4. Set **DecodingOptions** and decode the image to obtain a PixelMap.
   Carry out decoding after the setting.

   <!-- @[create_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
   
   ``` TypeScript
   async createPixelMap(imageSource: image.ImageSource | undefined): Promise<image.PixelMap | undefined> {
     if (!imageSource) {
       console.error('imageSource is undefined.');
       return undefined;
     }
     // Set the decoding options.
     let decodingOptions: image.DecodingOptions = {
       editable: true,
       desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
       // If AUTO is passed in, decoding is performed based on the image format and device capabilities. If the image is an HDR resource and the device supports HDR decoding, an HDR PixelMap is obtained after decoding.
       desiredDynamicRange: image.DecodingDynamicRange.HDR,
     };
   
     try {
       // Generate a PixelMap and return it.
       const pixelMap = await imageSource.createPixelMap(decodingOptions);
       if (pixelMap) {
         console.info('Create PixelMap successfully.');
         // Check whether the PixelMap is the HDR content.
         let imageInfo = await pixelMap.getImageInfo();
         console.info(`Create PixelMap successfully with imageInfo.isHdr: ${imageInfo.isHdr}.`);
         return pixelMap;
       } else {
         console.info('Create PixelMap failed.');
         return undefined;
       }
     } catch (error) {
       console.error(`Failed to create PixelMap: ${error}.`);
       return undefined;
     }
   }
   ```
      
   After the decoding is complete and the PixelMap is obtained, you can perform subsequent [image processing](image-transformation.md).
   
5. Release the PixelMap and ImageSource instances.

   Ensure that the asynchronous operations of the PixelMap and ImageSource instances have finished executing. After these variables are no longer needed, you can manually call the APIs below to release them.

   <!-- @[release_pixelMapDecoder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->   
   
   ``` TypeScript
   async release(pixelMap: image.PixelMap | undefined, imageSource: image.ImageSource | undefined) {
     pixelMap?.release();
     pixelMap = undefined;
     imageSource?.release();
     imageSource = undefined;
   }
   ```
   
   > **NOTE**
   > 1. When to release the ImageSource instance: After successfully executing **createPixelMap** and obtaining the PixelMap instance, if you are certain that no other APIs of ImageSource will be used, you can manually release the ImageSource instance. Since the PixelMap instance obtained from decoding is independent, releasing the ImageSource instance will not make the PixelMap instance unusable.
   > 2. When to release the PixelMap instance: If you are using the [**Image** component](../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md) for displaying images, there is no need to manually release the PixelMap instance, as the Image component will automatically manage the PixelMap instance passed to it. If your application handles the PixelMap instance on its own, you are advised to manually release the PixelMap instance of the old page during page transitions or when the application switches to the background. In scenarios where memory resources are tight, you are advised to release the PixelMap instances of all invisible pages except the current one.

<!--RP1-->
<!--RP1End-->
