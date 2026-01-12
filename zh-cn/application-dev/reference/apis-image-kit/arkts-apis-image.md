# 模块描述
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

本模块提供图片的解码、编码、编辑、元数据处理和图片接收等能力。

本模块包含以下基础类：

- [ImageSource](arkts-apis-image-ImageSource.md)类，提供获取[图片信息](arkts-apis-image-i.md#imageinfo)、将图片解码为PixelMap或Picture、读取和修改[图片属性](arkts-apis-image-e.md#propertykey7)的能力。[支持解码的图片格式](arkts-apis-image-ImageSource.md#属性)包括png、jpeg、bmp、gif、webp、dng、heic<sup>12+</sup>、wbmp<sup>23+</sup>、heifs<sup>23+</sup>、tiff<sup>23+</sup>。

- [ImagePacker](arkts-apis-image-ImagePacker.md)类，提供将图片编码为压缩后的数据流或文件的能力。编码前需获取图片的ImageSource、PixelMap或Picture作为输入。[支持编码的图片格式](arkts-apis-image-ImagePacker.md#属性)包括jpeg、webp、png、heic<sup>12+</sup>、gif<sup>18+</sup>。

- [PixelMap](arkts-apis-image-PixelMap.md)类，位图对象，包含像素数据以及[图片信息](arkts-apis-image-i.md#imageinfo)。可用于读取或写入像素数据，进行裁剪、缩放、平移、旋转、镜像等操作，并可直接传给[Image组件](../apis-arkui/arkui-ts/ts-basic-components-image.md)用于显示。还提供了获取和设置图片色域、HDR元数据的方法。

- [Picture](arkts-apis-image-Picture.md)类，多图对象，由主图、辅助图和元数据组成。其中，主图包含了主要图像信息；辅助图用于存储与主图相关的附加信息；元数据用于存储与图片相关的其他信息。Picture提供获取主图、合成HDR图、获取辅助图、设置辅助图、获取元数据、设置元数据等方法。

- [AuxiliaryPicture](arkts-apis-image-AuxiliaryPicture.md)类，辅助图一般用于辅助主图进行特殊信息的展示，使图像包含更丰富的信息。目前支持的辅助图的类型可参考[AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13)。

- [Metadata](arkts-apis-image-Metadata.md)类，以Key-Value的形式存储图像的元数据。目前支持的元数据类型可参考[MetadataType](arkts-apis-image-e.md#metadatatype13)，包含Exif元数据、水印裁剪图元数据和HEIF序列图像元数据。Exif元数据的Key可参考[PropertyKey](arkts-apis-image-e.md#propertykey7)；水印裁剪图元数据的Key可参考[FragmentMapPropertyKey](arkts-apis-image-e.md#fragmentmappropertykey13)；HEIF序列图像元数据的Key可参考[HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23)。

- [ExifMetadata](arkts-apis-image-ExifMetadata.md)类，以Key-Value的形式存储图像的Exif元数据。Exif元数据的Key可参考[PropertyKey](arkts-apis-image-e.md#propertykey7)。

- [MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md)类，以Key-Value的形式存储图像Huawei相机定义的照片元数据。Huawei相机定义的照片元数据的Key可参考[PropertyKey](arkts-apis-image-e.md#propertykey7)。

- [HeifsMetadata](arkts-apis-image-HeifsMetadata.md)类，以Key-Value的形式存储图像的HEIF序列图像元数据。HEIF序列图像元数据的Key可参考[HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23)。

- [ImageReceiver](arkts-apis-image-ImageReceiver.md)类，作为图片的消费者，用于从Surface中接收、读取图片。

- [ImageCreator](arkts-apis-image-ImageCreator.md)类，作为图片的生产者，用于将图片写入到Surface中。

- [Image](arkts-apis-image-Image.md)类，供ImageReceiver和ImageCreator使用，用于传输图片对象，它的实际内容由生产者决定。如相机预览流提供的Image对象存储了YUV数据，相机拍照提供的Image对象存储了JPEG文件。

> **说明：**
>
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```
