# 如何处理HEIF图片
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## HEIF图片介绍

HEIF图片（High Efficiency Image File Format，HEIF，也称高效图像文件格式），是一个用于单张图像或图像序列的文件格式。它由动态影像专家小组（MPEG）开发，并在MPEG-H Part 12（ISO/IEC 23008-12）中定义。

目前主流的HEIF图片均使用HEVC(H.265)编码，这也是系统当前支持的HEIF图片。HEIF图片在压缩效率上具有明显优势，能够在保证图像质量的同时显著减小文件体积，通常比JPEG节省约50%的存储空间。

系统从API12开始支持HEIF图片的编解码与显示，如果应用基于系统Image Kit、ArkUI Image组件、ArkWeb等模块实现图片处理功能，则可以像处理JPEG、PNG等格式的图片一样，处理HEIF图片。

HEIF图片解码可参考：[图片解码指南（ArkTS）](../image-decoding.md)和[图片解码指南（C/C++）](../image-source-c.md)。

HEIF图片显示可参考：[ArkUI Image组件图片显示](../../../ui/arkts-graphics-display.md)。

HEIF图片编码可参考：[图片编码指南（ArkTS）](../image-encoding.md)和[图片编码指南（C/C++）](../image-packer-c.md)。

ArkWeb图片上传可参考：[使用Web组件上传文件](../../../web/web-file-upload.md)。

## 常见问题

### 上传HEIF图片时提示：“不支持的格式”

可以使用[ImageSource](../../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#属性)的supportedFormats属性和[ImagePacker](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#属性)的supportedFormats属性，来查看系统支持编解码的图片格式。只要查询到的结果中包含"image/heic"，即代表该设备支持HEIF图片编解码。

系统侧不会拦截HEIF图片上传，若HEIF图片上传不成功，可能的原因是：应用对后缀名为.heic、.heif、.HEIC、.HEIF的图片文件做了过滤限制。

对于使用系统图片处理能力的应用，只需要解除过滤限制，即可正常上传、显示HEIF图片。

如果应用不希望使用HEIF图片，可以借助[Image Kit](../image-overview.md)提供的图片编解码能力，自行[将HEIF图片转码为JPEG或PNG格式的图片](#担心使用heif格式图片存在兼容性问题需使用jpeg或png格式的图片如何操作)。

当应用没有使用系统提供的图片处理能力，且自身无法处理HEIF图片时，还可以选择使用[Media Library Kit](../../medialibrary/photoAccessHelper-overview.md)提供的媒体资源访问能力，这时系统会主动将HEIF图片转码为JPEG图片。

### 为什么选择的是HEIF图片，实际上获取到的却是JPEG图片？

当使用[媒体文件管理服务](../../medialibrary/photoAccessHelper-overview.md)或[URI（Uniform Resource Identifier）](../../../file-management/core-file-kit-intro.md#亮点特征)访问HEIF图片时，系统会自动将HEIF图片转码为兼容性相对更好的JPEG图片，且保证转码前后图片携带的元数据信息一致。

如果想直接获取最原始的HEIF图片，建议使用[文件基础服务](../../../file-management/core-file-kit-intro.md)获取HEIF图片的[文件描述符FD（File Descriptor）](../../../file-management/core-file-kit-intro.md#亮点特征)。

### 担心使用HEIF格式图片存在兼容性问题，需使用JPEG或PNG格式的图片，如何操作

可以借助Image Kit的图片编解码能力，将HEIF图片转码成JPEG或PNG格式的图片。

转码的本质是将HEIF图片解码后，把解码的结果重新编码为JPEG或PNG格式的图片。通过配置编码参数，开发者可以更加灵活地控制最终获取到的图片文件格式、图片质量以及图片属性。

示例代码如下：

<!-- @[transcoding_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/TranscodingUtility.ets) -->        

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { PromptAction } from '@kit.ArkUI';

const promptAction = new PromptAction();

export async function reEncoding(context : Context, fd : number) {
  // 首先获取图片文件的fd，创建ImageSource。
  const imageSource : image.ImageSource = image.createImageSource(fd);
  // 创建ImagePacker，以便调用图片编码接口。
  const imagePackerApi = image.createImagePacker();
  // 配置图片编码选项：
  // format应使用标准的mimetype格式，如："image/jpeg"、"image/png"、"image/heic"；
  // quality推荐设置为80，在保证较好的图片质量的同时，可以使编码后的图片文件体积更小；
  // needsPackProperties参数，用于控制编码时是否保存图片属性信息。默认值为false，即不保存。
  let packOpts : image.PackingOption = { format:'image/jpeg', quality:80, needsPackProperties:false };
  // 指定图片编码文件的存放路径。
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

如需使用CAPI进行图片转码，应首先创建ImageSource和ImagePacker实例，然后指定编码参数，调用图片编码接口完成转码。详细示例代码可参考[使用Image_NativeModule完成图片编码](../image-packer-c.md)。