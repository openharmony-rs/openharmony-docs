# Handling HEIF Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Introduction to HEIF Images

High Efficiency Image File Format (HEIF) is a file format for individual images or image sequences. It is developed by the Moving Picture Experts Group (MPEG) and defined in MPEG-H Part 12 (ISO/IEC 23008-12).

Most mainstream HEIF images currently use HEVC (H.265) encoding, which is also the HEIF image format supported by the system. HEIF images offer significant advantages in compression efficiency, reducing file size by about 50% compared to JPEG while maintaining image quality.

The system has supported HEIF image encoding, decoding, and display since API version 12. If your application uses system modules such as Image Kit, ArkUI **Image** component, or ArkWeb to implement image processing, you can handle HEIF images in the same way as JPEG, PNG, and other formats.

For details about how to decode HEIF images, see [Using ImageSource to Decode Images](../image-decoding.md) and [Using Image_NativeModule to Decode Images](../image-source-c.md).

For details about how to display HEIF images, see [Image Display (Image)](../../../ui/arkts-graphics-display.md).

For details about how to encode HEIF images, see [Image Encoding Guide (ArkTS)](../image-encoding.md) and [Image Encoding Guide (C/C++)](../image-packer-c.md).

For details about how to upload HEIF images using ArkWeb, see [Uploading a File Using a Web Component](../../../web/web-file-upload.md).

## FAQs

### What should I do when a message is displayed indicating unsupported format when uploading HEIF images

You can use the **supportedFormats** property of [ImageSource](../../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#properties) and [ImagePacker](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#properties) to view the image formats supported for encoding and decoding. If the query result contains **image/heic**, the device supports HEIF image encoding and decoding.

The system does not block the upload of HEIF images. If HEIF image upload fails, it might be because the application has filtering restrictions on image files with the extensions .heic, .heif, .HEIC, or .HEIF.

For applications using the image processing capabilities of the system, simply remove the filtering restrictions for normal uploading and displaying of HEIF images.

If an application prefers not to use HEIF images, it can leverage the image encoding and decoding capabilities provided by [Image Kit](../image-overview.md) to [transcode HEIF images into JPEG or PNG format](#how-do-i-use-jpeg-or-png-images-to-avoid-compatibility-issues-with-heif-images).

If an application does not use the system's image processing capabilities and cannot handle HEIF images itself, it can opt to use the media resource access capabilities provided by [Media Library Kit](../../medialibrary/photoAccessHelper-overview.md). In this case, the system automatically transcodes HEIF images into JPEG images.

### Why is a JPEG image obtained instead of the selected HEIF image

When accessing HEIF images using [Media Library Kit](../../medialibrary/photoAccessHelper-overview.md) or a [Uniform Resource Identifier (URI)](../../../file-management/core-file-kit-intro.md#features), the system automatically transcodes HEIF images into JPEG images, which have better compatibility, while ensuring that the metadata carried by the images remains consistent before and after transcoding.

If you want to directly obtain the original HEIF image, use [Core File Kit](../../../file-management/core-file-kit-intro.md) to obtain the [File Descriptor (FD)](../../../file-management/core-file-kit-intro.md#features) of the HEIF image.

### How do I use JPEG or PNG images to avoid compatibility issues with HEIF images

You can use the image encoding and decoding capabilities provided by Image Kit to transcode HEIF images into JPEG or PNG format.

Transcoding essentially involves decoding the HEIF image and then re-encoding the decoded result into a JPEG or PNG image. By configuring encoding options, you can more flexibly control the final image file format, image quality, and image properties.

The sample code is as follows:

<!-- @[transcoding_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/TranscodingUtility.ets) -->        

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { promptAction } from '@kit.ArkUI';

export async function reEncoding(context : Context, fd : number) {
  // Obtain the FD of the image file and create an ImageSource.
  const imageSource : image.ImageSource = image.createImageSource(fd);
  // Create an ImagePacker to call the image encoding API.
  const imagePackerApi = image.createImagePacker();
  // Configure image encoding options.
  // Use the standard mimetype format, for example, "image/jpeg," "image/png," and "image/heic."
  // You are advised to set quality to 80 to ensure good image quality and reduce the size of the encoded image file.
  // The needsPackProperties parameter is used to determine whether to save image properties during encoding. The default value is false, indicating that the configuration is not saved.
  let packOpts : image.PackingOption = { format:'image/jpeg', quality:80, needsPackProperties:false };
  // Specify the path for storing the encoded image file.
  const filePath : string = context.cacheDir + '/result.jpg';
  let file = fs.openSync(filePath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
  imagePackerApi.packToFile(imageSource, file.fd, packOpts).then(() => {
    promptAction.showToast({ message: `Succeed to pack the image.`});
    console.info('Succeed to pack the image.');
  }).catch((error : BusinessError) => {
    promptAction.showToast({ message: 'Failed to pack the image. And the error is: ' + error});
    console.error('Failed to pack the image. And the error is: ' + error);
  }).finally(()=>{
    fs.closeSync(file.fd);
  })
}
```

To use C APIs for image transcoding, you should first create instances of ImageSource and ImagePacker, specify the encoding options, and call the image encoding interface to complete the transcoding. For details about the sample code, see [Using Image_NativeModule to Encode Images](../image-packer-c.md).
