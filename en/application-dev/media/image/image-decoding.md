# Using ImageSource to Decode Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=9a5d11ace507ae2a5f05e1e571b2d135f70c7b30 translatedAt=2026-10-30T11:38:03.943Z pushedAt=2026-10-30T11:38:03.943Z nl=1 -->

When your application needs to read or display an image, or perform operations such as scaling and cropping, use [ImageSource](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md) to decode the image. You can create an ImageSource instance from the image's path in the application sandbox, a file descriptor, or a buffer, and decode the image into a PixelMap.

The decoded PixelMap can be used for image display, processing, and editing. You can also set the image size, decoding region, and output pixel format during decoding to meet different application requirements.

## Supported Image Formats

The following image file formats are supported: JPEG, PNG, GIF, WebP, BMP, SVG, ICO, DNG, HEIC, TIFF<sup>23+</sup>, HEIFS<sup>23+</sup>, and WBMP<sup>23+</sup>.

Starting from API version 26.0.0, AVIF and AVIS are also supported.

Decoding support for some formats depends on the device hardware. Before decoding an image, you are advised to call [image.getImageSourceSupportedFormats](../../reference/apis-image-kit/arkts-apis-image-f.md#imagegetimagesourcesupportedformats20) to query the decoding capabilities of the current device.

Starting from API version 22, decoding is supported for embedded preview images (usually in JPEG format) in the CR2, CR3, ARW, NEF, RAF, NRW, ORF, RW2, PEF, and SRW formats captured by professional cameras. This decoding capability is not restricted by the type of device on which the application runs.

## Setting the Output Pixel Format

The output pixel format specifies how image data is stored in the decoded PixelMap. When decoding an image using [createPixelMap](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#createpixelmap7) or [createPixelMapUsingAllocator](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#createpixelmapusingallocator15), set **desiredPixelFormat** in [DecodingOptions](../../reference/apis-image-kit/arkts-apis-image-i.md#decodingoptions7) to the desired output format defined by [PixelMapFormat](../../reference/apis-image-kit/arkts-apis-image-e.md#pixelmapformat7).

Pixel formats differ in memory usage, transparency support, and suitability for subsequent image display and processing. Set **desiredPixelFormat** when your application needs to control the format of the decoded image data.

The supported combinations depend on the input image format, image characteristics, dynamic range, and device capabilities. After decoding, call [getImageInfoSync](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md#getimageinfosync12) to obtain **ImageInfo.pixelFormat** and verify the actual output pixel format.

The following table lists the target pixel formats (**desiredPixelFormat**) supported for each input image format.

| Input Image Format | Supported Target Pixel Formats |
| --- | --- |
| JPEG, BMP, DNG, HEIC, WBMP, HEIFS, AVIF, AVIS | RGB_565, RGBA_8888, BGRA_8888, NV21, NV12, ASTC_4x4 |
| PNG, GIF, WebP, ICO | RGB_565 (images without an alpha channel), RGBA_8888, BGRA_8888, NV21, NV12, ASTC_4x4 |
| TIFF, SVG | RGBA_8888, BGRA_8888, ASTC_4x4 |

> **NOTE**
>
> - If **desiredPixelFormat** is set to **UNKNOWN**, the output pixel format defaults to **RGBA_8888**.
>
> - For PNG, GIF, ICO, and WebP images, decoding to **RGB_565** is supported only for images without an alpha channel. Decoding fails for images with an alpha channel.
>
> - Decoding does not currently support the **ARGB_8888** or **RGBA_F16** pixel format. For JPEG, BMP, DNG, HEIC, WBMP, HEIFS, AVIF, AVIS, PNG, GIF, WebP, and ICO images, if **desiredPixelFormat** is set to **ARGB_8888** or **RGBA_F16**, the output pixel format is **RGBA_8888**.
> 
> - When both **desiredPixelFormat** and **desiredDynamicRange** are set, the former specifies the desired output pixel format and the latter specifies the dynamic range of the decoded image. To meet SDR or HDR decoding requirements, the actual output PixelMap format may differ from **desiredPixelFormat**. You are advised to call [getImageInfoSync](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md#getimageinfosync12) to obtain **ImageInfo.pixelFormat** and verify the actual output pixel format.

## How to Develop

For details about image decoding APIs, see [ImageSource](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md).

1. Import the image module.
   
   <!-- @[decodingPixelMap_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->   
   
   ``` TypeScript
   // Import the required modules.
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { fileIo } from '@kit.CoreFileKit';
   import { resourceManager } from '@kit.LocalizationKit';
   ```

2. (Optional) Query the device's decoding capabilities.

   Decoding support for some image formats depends on the device hardware. Before decoding, you can query the list of formats supported by the device:

   <!-- @[get_supportedFormats](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) --> 
   
   ``` TypeScript
   // Obtain the image formats supported for decoding on the current device.
   export function getSupportedFormats(): string[] {
     let formats = image.getImageSourceSupportedFormats();
     console.info('Supported formats: ' + formats);
     return formats;
   }
   
   // Check whether decoding is supported for the specified format.
   export function isFormatSupported(format: string): boolean {
     let formats = image.getImageSourceSupportedFormats();
     return formats.includes(format);
   }
   ```

3. Obtain an image.

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
   
4. Create an ImageSource instance.

   - Method 1: Create an ImageSource instance using the sandbox path. The sandbox path can be obtained by using method 1 in step 3.

     <!-- @[createImageSource_filePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // path indicates the obtained sandbox path.
     const imageSource : image.ImageSource = image.createImageSource(filePath);
     ```

   - Method 2: Create an ImageSource instance using the file descriptor. The file descriptor can be obtained by using method 2 in step 3.

     <!-- @[createImageSource_fd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     // fd is the obtained file descriptor.
     const imageSource: image.ImageSource = image.createImageSource(fd);
     ```

   - Method 3: Create an ImageSource instance using an array buffer. The array buffer can be obtained by using method 3 in step 3.

     <!-- @[createImageSource_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(buffer);
     ```

   - Method 4: Create an ImageSource instance using the raw file descriptor of the resource file. The raw file descriptor can be obtained by using method 4 in step 3.

     <!-- @[createImageSource_rawFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) -->   
     
     ``` TypeScript
     const imageSource: image.ImageSource = image.createImageSource(rawFileDescriptor);
     ```

5. Set **DecodingOptions** and decode the image to obtain a PixelMap.

   Configure the decoding options and decode the image:

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
       desiredDynamicRange: image.DecodingDynamicRange.AUTO,
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
         console.error('Create PixelMap failed.');
         return undefined;
       }
     } catch (error) {
       console.error(`Failed to create PixelMap: ${error}.`);
       return undefined;
     }
   }
   ```
      
   After the decoding is complete and the PixelMap is obtained, you can perform subsequent [image processing](image-transformation.md).
   
6. Release the PixelMap and ImageSource instances.

   Ensure that the asynchronous operations of the PixelMap and ImageSource instances have finished executing. After these variables are no longer needed, you can manually call the APIs below to release them.

   <!-- @[release_pixelMapDecoder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/pages/DecodingPixelMap.ets) -->    
   
   ``` TypeScript
   async release() {
     try {
       await this.pixelMap?.release();
     } catch (error) {
       console.error(`Failed to release PixelMap: ${error}.`);
     } finally {
       this.pixelMap = undefined;
     }
   
     try {
       await this.imageSource?.release();
     } catch (error) {
       console.error(`Failed to release ImageSource: ${error}.`);
     } finally {
       this.imageSource = undefined;
     }
   }
   ```
   
   > **NOTE**
   > 1. When to release the ImageSource instance: After successfully executing **createPixelMap** and obtaining the PixelMap instance, if you are certain that no other APIs of ImageSource will be used, you can manually release the ImageSource instance. Since the PixelMap instance obtained from decoding is independent, releasing the ImageSource instance will not make the PixelMap instance unusable.
   > 2. When to release the PixelMap instance: If you are using the [Image component](../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md) for displaying images, there is no need to manually release the PixelMap instance, as the Image component will automatically manage the PixelMap instance passed to it. If your application handles the PixelMap instance on its own, you are advised to manually release the PixelMap instance of the old page during page transitions or when the application switches to the background. In scenarios where memory resources are tight, you are advised to release the PixelMap instances of all invisible pages except the current one.

## Advanced Topics

- **Memory-optimized decoding**: Use DMA memory and YUV pixel formats to reduce memory usage and improve decoding performance. See [Allocating Memory for Image Decoding (ArkTS)](image-allocator-type.md).
- **Region decoding**: Decode a specified region of an image for scenarios such as viewing part of a large image or previewing a crop. See [Image Region Decoding and Downsampling (ArkTS)](image-region-and-downsampling.md).
- **Downsampling decoding**: Scale directly to the target size during decoding to avoid the performance overhead of scaling after decoding. This is useful for generating thumbnails. See [Image Region Decoding and Downsampling (ArkTS)](image-region-and-downsampling.md).
- **Multi-image object decoding**: Decode a Picture object containing a main image and auxiliary images for HDR image and professional HEIF format processing. See [Using ImageSource to Decode Pictures](image-picture-decoding.md).

## Samples

The following samples demonstrate image decoding:

- [Image Editing (ArkTS)](https://gitcode.com/openharmony/codelabs/tree/master/Media/ImageEdit)

- [Image Editing (JS)](https://gitcode.com/openharmony/codelabs/tree/master/Media/ImageEditorTemplate)

<!--RP1-->
<!--RP1End-->
