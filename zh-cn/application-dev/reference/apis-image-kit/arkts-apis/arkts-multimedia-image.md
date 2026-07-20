# @ohos.multimedia.image

本模块提供图片的解码、编码、编辑、元数据处理和图片接收等能力。

本模块包含以下基础类：

- [ImageSource](arkts-image-image-imagesource-i.md)类，提供获取[图片信息](arkts-image-image-imageinfo-i.md)、将图片解码为PixelMap或Picture、读取和修改[图片属性](arkts-image-image-propertykey-e.md)的能力。[支持解码的图片格式](docroot://reference/apis-image-kit/arkts-apis-image-ImageSource.md#属性)包括png、jpeg、bmp、gif、webp、dng、heic<sup>12+</sup>、wbmp<sup>23+</sup>、heifs<sup>23+</sup>、tiff<sup>23+</sup>。  
- [ImagePacker](arkts-image-image-imagepacker-i.md)类，提供将图片编码为压缩后的数据流或文件的能力。编码前需获取图片的ImageSource、PixelMap或Picture作为输入。[支持编码的图片格式](docroot://reference/apis-image-kit/arkts-apis-image-ImagePacker.md#属性)包括jpeg、webp、png、heic<sup>12+</sup>、gif<sup>18+</sup>。  
- [PixelMap](arkts-image-image-pixelmap-i.md)类，位图对象，包含像素数据以及[图片信息](arkts-image-image-imageinfo-i.md)。可用于读取或写入像素数据，进行裁剪、缩放、平移、旋转、镜像等操作，并可直接传给[Image组件](../../apis-arkui/arkts-components/arkts-arkui-image-i)用于显示。还提供了获取和设置图片色域、HDR元数据的方法。  
- [Picture](arkts-image-image-picture-i.md)类，多图对象，由主图、辅助图和元数据组成。其中，主图包含了主要图像信息；辅助图用于存储与主图相关的附加信息；元数据用于存储与图片相关的其他信息。Picture提供获取主图、合成HDR图、获取辅助图、设置辅助图、获取元数据、设置元数据等方法。  
- [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md)类，辅助图一般用于辅助主图进行特殊信息的展示，使图像包含更丰富的信息。目前支持的辅助图的类型可参考[AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md)。  
- [Metadata](arkts-image-image-metadata-i.md)类，以Key-Value的形式存储图像的元数据。目前支持的元数据类型可参考[MetadataType](arkts-image-image-metadatatype-e.md)，包含Exif元数据、水印裁剪图元数据和HEIF序列图像元数据。Exif元数据的Key可参考[PropertyKey](arkts-image-image-propertykey-e.md)；水印裁剪图元数据的Key可参考[FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md)；HEIF序列图像元数据的Key可参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。  
- [ExifMetadata](arkts-image-image-exifmetadata-c.md)类，以Key-Value的形式存储图像的Exif元数据。Exif元数据的Key可参考[PropertyKey](arkts-image-image-propertykey-e.md)。  
- [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md)类，以Key-Value的形式存储图像Huawei相机定义的照片元数据。Huawei相机定义的照片元数据的Key可参考[PropertyKey](arkts-image-image-propertykey-e.md)。  
- [HeifsMetadata](arkts-image-image-heifsmetadata-c.md)类，以Key-Value的形式存储图像的HEIF序列图像元数据。HEIF序列图像元数据的Key可参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。  
- [WebPMetadata](docroot://reference/apis-image-kit/arkts-apis-image-WebPMetadata.md)类，以Key-Value的形式存储图像的WebP图像元数据。WebP图像元数据的Key可参考[WebPPropertyKey](arkts-image-image-webppropertykey-e.md)。  
- [GifMetadata](docroot://reference/apis-image-kit/arkts-apis-image-GifMetadata.md)类，以Key-Value的形式存储图像的GIF图像元数据。GIF图像元数据的Key可参考[GifPropertyKey](arkts-image-image-gifpropertykey-e.md)。  
- [JfifMetadata](docroot://reference/apis-image-kit/arkts-apis-image-JfifMetadata.md)类，以Key-Value的形式存储图像的JFIF图像元数据。JFIF图像元数据的Key可参考[JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md)。  
- [TiffMetadata](docroot://reference/apis-image-kit/arkts-apis-image-TiffMetadata.md)类，以Key-Value的形式存储图像的TIFF图像元数据。TIFF图像元数据的Key可参考[TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md)。  
- [PngMetadata](docroot://reference/apis-image-kit/arkts-apis-image-PngMetadata.md)类，以Key-Value的形式存储图像的PNG图像元数据。PNG图像元数据的Key可参考[PngPropertyKey](arkts-image-image-pngpropertykey-e.md)。  
- [AvisMetadata](docroot://reference/apis-image-kit/arkts-apis-image-AvisMetadata.md)类，以Key-Value的形式存储图像的AVIS图像元数据。AVIS图像元数据的Key可参考[AvisPropertyKey](arkts-image-image-avispropertykey-e.md)。  
- [ImageReceiver](arkts-image-image-imagereceiver-i.md)类，作为图片的消费者，用于从Surface中接收、读取图片。  
- [ImageCreator](arkts-image-image-imagecreator-i.md)类，作为图片的生产者，用于将图片写入到Surface中。  
- [Image](arkts-image-image-image-i.md)类，供ImageReceiver和ImageCreator使用，用于传输图片对象，其实际内容由生产者决定。如相机预览流提供的Image对象存储了YUV数据、相机拍照提供的Image对象存储了JPEG文件。

**起始版本：** 6

<!--Device-unnamed-declare namespace image--><!--Device-unnamed-declare namespace image-End-->

**系统能力：** 
- API版本11+：SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource) | 通过缓冲区以增量的方式创建ImageSource实例，IncrementalSource不支持读写Exif信息。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。  以增量方式创建的ImageSource实例，仅支持使用以下功能，同步、异步callback、异步Promise均支持。  - 获取图片信息：指定序号-[getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo-1)、直接获取-[getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo-1)  - 获取图片中给定索引处图像的指定属性键的值：[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)  - 批量获取图片中的指定属性键的值：[getImageProperties](arkts-image-image-imagesource-i.md#getimageproperties-1)  - 更新增量数据：[updateData](arkts-image-image-imagesource-i.md#updatedata-1)  - 创建PixelMap对象：通过图片解码参数创建-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)、通过默认参数创建-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) 、通过图片解码参数-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)  - 释放ImageSource实例：[release](arkts-image-image-imagesource-i.md#release-1) |
| [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource-1) | 通过缓冲区以增量的方式创建ImageSource实例，IncrementalSource不支持读写Exif信息。  此接口支持的功能与[CreateIncrementalSource(buf: ArrayBuffer): ImageSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource-1)所生成的实例支持的功能相同。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createAuxiliaryPicture](arkts-image-image-createauxiliarypicture-f.md#createauxiliarypicture) | 通过ArrayBuffer图片数据、辅助图尺寸、辅助图类型创建AuxiliaryPicture实例。该接口仅支持传入BGRA的连续像素数据，会创建出RGBA的辅助图。  由于图片占用内存较大，所以当AuxiliaryPicture实例使用完成后，应主动调用[release](arkts-image-image-auxiliarypicture-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createAuxiliaryPictureUsingAllocator](arkts-image-image-createauxiliarypictureusingallocator-f.md#createauxiliarypictureusingallocator) | 使用指定的内存类型，根据辅助图信息和像素数据创建辅助图对象。 |
| [createEmptyPixelMap](arkts-image-image-createemptypixelmap-f.md#createemptypixelmap) | Creates an empty PixelMap.  The following pixel format is not supported for PixelMap creation: ASTC_4x4. |
| [createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator) | 通过宽、高、图片格式、容量创建ImageCreator实例。  由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release](arkts-image-image-imagecreator-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator-1) | 通过图片大小、图片格式、容量创建ImageCreator实例。  由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release](arkts-image-image-imagecreator-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImagePacker](arkts-image-image-createimagepacker-f.md#createimagepacker) | 创建ImagePacker实例。  由于图片占用内存较大，所以当ImagePacker实例使用完成后，应主动调用[release](arkts-image-image-imagepacker-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver) | 通过宽、高、图片格式、容量创建ImageReceiver实例。ImageReceiver做为图片的接收方、消费者，它的参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方、生产者进行，如相机预览流[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))。  由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](arkts-image-image-imagereceiver-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-1) | 通过图片大小、图片格式、容量创建ImageReceiver实例。ImageReceiver作为图片的接收方、消费者，它的参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方、生产者进行，如相机预览流[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))。  由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](arkts-image-image-imagereceiver-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-2) | 通过ImageReceiverOptions创建ImageReceiver实例。ImageReceiver作为图片的接收方、消费者，其参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方、生产者进行，如相机预览流[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))。  由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](arkts-image-image-imagereceiver-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource) | 通过传入的uri创建ImageSource实例。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1) | 通过传入的uri创建ImageSource实例。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-2) | 通过传入文件描述符来创建ImageSource实例。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-3) | 通过传入文件描述符来创建ImageSource实例。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-4) | 通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync-1)这一类接口。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-5) | 通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync-1)这一类接口。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-6) | 通过图像资源文件的RawFileDescriptor创建ImageSource实例。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [createPicture](arkts-image-image-createpicture-f.md#createpicture) | 通过主图的PixelMap创建一个Picture对象。  由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release-1)方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 |
| [createPictureFromParcel](arkts-image-image-createpicturefromparcel-f.md#createpicturefromparcel) | 从MessageSequence中获取Picture。  由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release-1)方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 |
| [createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap) | Create pixelmap by data buffer.  Starting from API 26.0.0, it is recommended to use {@link createPixelMapFromPixels} instead for better exception handling capabilities. |
| [createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) | Create pixelmap by data buffer.  Starting from API 26.0.0, it is recommended to use {@link createPixelMapFromPixels} instead for better exception handling capabilities. |
| [createPixelMapFromParcel](arkts-image-image-createpixelmapfromparcel-f.md#createpixelmapfromparcel) | Creates a PixelMap object based on MessageSequence parameter. |
| [createPixelMapFromPixels](arkts-image-image-createpixelmapfrompixels-f.md#createpixelmapfrompixels) | Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap.  The following pixel formats are not supported for PixelMap creation:RGBA_1010102, YCBCR_P010, YCRCB_P010, ASTC_4x4. |
| [createPixelMapFromPixelsSync](arkts-image-image-createpixelmapfrompixelssync-f.md#createpixelmapfrompixelssync) | Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap.  The following pixel formats are not supported for PixelMap creation:RGBA_1010102, YCBCR_P010, YCRCB_P010, ASTC_4x4. |
| [createPixelMapFromSurface](arkts-image-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurface](arkts-image-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface-1) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceSync](arkts-image-image-createpixelmapfromsurfacesync-f.md#createpixelmapfromsurfacesync) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceSync](arkts-image-image-createpixelmapfromsurfacesync-f.md#createpixelmapfromsurfacesync-1) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceWithTransformation](arkts-image-image-createpixelmapfromsurfacewithtransformation-f.md#createpixelmapfromsurfacewithtransformation) | Creates a PixelMap object based on the ID of a Surface with transformation. |
| [createPixelMapFromSurfaceWithTransformationSync](arkts-image-image-createpixelmapfromsurfacewithtransformationsync-f.md#createpixelmapfromsurfacewithtransformationsync) | Creates a PixelMap object based on the ID of a Surface with transformation. |
| [createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync) | Create pixelmap by data buffer.  Starting from API 26.0.0, it is recommended to use {@link createPixelMapFromPixelsSync} instead for better exception handling capabilities. |
| [createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync-1) | Create an empty pixelmap.  Starting from API 26.0.0, it is recommended to use {@link createEmptyPixelMap} instead for better exception handling capabilities. |
| [createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md#createpixelmapusingallocator) | Create pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size,platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md#createpixelmapusingallocatorsync) | Create pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size,platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md#createpixelmapusingallocatorsync-1) | Create an empty pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size,platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPremultipliedPixelMap](arkts-image-image-createpremultipliedpixelmap-f.md#createpremultipliedpixelmap) | Transforms pixelmap from unpremultiplied alpha format to premultiplied alpha format. |
| [createPremultipliedPixelMap](arkts-image-image-createpremultipliedpixelmap-f.md#createpremultipliedpixelmap-1) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [createUnpremultipliedPixelMap](arkts-image-image-createunpremultipliedpixelmap-f.md#createunpremultipliedpixelmap) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [createUnpremultipliedPixelMap](arkts-image-image-createunpremultipliedpixelmap-f.md#createunpremultipliedpixelmap-1) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [getImagePackerSupportedFormats](arkts-image-image-getimagepackersupportedformats-f.md#getimagepackersupportedformats) | 获取支持编码的图片格式，图片格式以mime type表示。 |
| [getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getimagesourcesupportedformats) | 获取支持解码的图片格式，图片格式以mime type表示。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createPictureByHdrAndSdrPixelMap](arkts-image-image-createpicturebyhdrandsdrpixelmap-f-sys.md#createpicturebyhdrandsdrpixelmap) | 根据HDR PixelMap和SDR PixelMap创建Picture对象。系统将使用HDR和SDR PixelMap生成一个增益图（gainmap），返回的Picture对象将包含SDR PixelMap和生成的gainmap PixelMap，像素格式为RGBA8888。使用Promise异步回调。 |
| [createPictureByHdrAndSdrPixelMap](arkts-image-image-createpicturebyhdrandsdrpixelmap-f-sys.md#createpicturebyhdrandsdrpixelmap-1) | 根据HDR PixelMap和SDR PixelMap创建Picture对象。系统将使用HDR和SDR PixelMap生成一个Gainmap（增益图），返回的Picture对象将包含SDR PixelMap和生成的Gainmap PixelMap，像素格式为RGBA8888。Gainmap PixelMap的尺寸可以通过设置params进行选择。使用Promise异步回调。 |
| [decomposeToPicture](arkts-image-image-decomposetopicture-f-sys.md#decomposetopicture) | 将HDR PixelMap分解为包含SDR PixelMap和增益图（gainmap）的Picture对象。使用Promise异步回调。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [AvisMetadata](arkts-image-image-avismetadata-c.md) | Avis metadata. |
| [DngMetadata](arkts-image-image-dngmetadata-c.md) | Dng图像元数据类，用于存储图像的元数据。 |
| [ExifMetadata](arkts-image-image-exifmetadata-c.md) | ExifMetadata implements Metadata  Exif（Exchangeable image file format）元数据。 |
| [GifMetadata](arkts-image-image-gifmetadata-c.md) | Gif metadata. |
| [HeifsMetadata](arkts-image-image-heifsmetadata-c.md) | HeifsMetadata implements Metadata  HEIF序列图像元数据类，用于存储图像的元数据。 |
| [JfifMetadata](arkts-image-image-jfifmetadata-c.md) | JFIF metadata. |
| [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) | MakerNoteHuaweiMetadata implements Metadata  来自Huawei相机的照片元数据。 |
| [PngMetadata](arkts-image-image-pngmetadata-c.md) | Png metadata. |
| [TiffMetadata](arkts-image-image-tiffmetadata-c.md) | TIFF metadata. |
| [WebPMetadata](arkts-image-image-webpmetadata-c.md) | WebP metadata. |
| [XMPMetadata](arkts-image-image-xmpmetadata-c.md) | XMPMetadata instance. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | AuxiliaryPicture类，用于读取或写入图像的辅助图数据以及获取图像的辅助图信息。目前支持的辅助图类型可参考[AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md)。  在调用AuxiliaryPicture的方法前，需要通过[image.createAuxiliaryPicture](arkts-image-image-createauxiliarypicture-f.md#createauxiliarypicture-1)或Picture的[getAuxiliaryPicture](arkts-image-image-picture-i.md#getauxiliarypicture-1)创建一个AuxiliaryPicture实例。  由于图片占用内存较大，所以当AuxiliaryPicture对象使用完成后，应主动调用[release](arkts-image-image-auxiliarypicture-i.md#release-1)方法及时释放对象。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该对象。 |
| [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | 表示辅助图的图像信息。 |
| [BinaryBufferInfo](arkts-image-image-binarybufferinfo-i.md) | 描述二值图像缓冲区内的信息及数据。 |
| [Component](arkts-image-image-component-i.md) | 描述图像颜色分量。 |
| [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 图像解码设置选项。 |
| [DecodingOptionsForPicture](arkts-image-image-decodingoptionsforpicture-i.md) | 图像解码设置选项。 |
| [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | 缩略图解码参数选项。 |
| [GainmapChannel](arkts-image-image-gainmapchannel-i.md) | Gainmap图单个通道的数据内容，参考ISO 21496-1。 |
| [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | 表示查询图片属性的索引。 |
| [HdrComposeOptions](arkts-image-image-hdrcomposeoptions-i.md) | Picture合成HDR时可配置的参数选项。 |
| [HdrGainmapMetadata](arkts-image-image-hdrgainmapmetadata-i.md) | Gainmap使用的元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_GAINMAP_METADATA关键字对应的值，参考ISO 21496-1。 |
| [HdrStaticMetadata](arkts-image-image-hdrstaticmetadata-i.md) | 静态元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_STATIC_METADATA关键字对应的值。 |
| [Image](arkts-image-image-image-i.md) | Image类，供ImageReceiver和ImageCreator使用，用于传输图片对象，其实际内容由生产者决定。如相机预览流提供的Image对象存储了YUV数据、相机拍照提供的Image对象存储了JPEG文件。  调用[readNextImage](arkts-image-image-imagereceiver-i.md#readnextimage-1)和[readLatestImage](arkts-image-image-imagereceiver-i.md#readlatestimage-1)接口时会返回Image实例。  Image的属性仅支持在创建时初始化，后续无法再修改，且其属性不对图片内容产生实际影响，请以图片生产者写入的属性为准，即以向[ImageReceiver](arkts-image-image-imagereceiver-i.md)发送图片数据的发送方实际写入的内容为准。  由于图片占用内存较大，所以当Image实例使用完成后，应主动调用[release](arkts-image-image-image-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [ImageBufferData](arkts-image-image-imagebufferdata-i.md) | 保存图像缓冲区数据的指针、不同颜色分量的行间距与像素间距信息。 |
| [ImageCreator](arkts-image-image-imagecreator-i.md) | ImageCreator类，作为图片的生产者，用于将图片写入到Surface中。  在调用以下方法前需要先通过[image.createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator-1)创建ImageCreator实例，ImageCreator不支持多线程。  由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release](arkts-image-image-imagecreator-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | 表示图片信息。 |
| [ImageMetadata](arkts-image-image-imagemetadata-i.md) | 图像的元数据集。 |
| [ImagePacker](arkts-image-image-imagepacker-i.md) | ImagePacker类，用于图片压缩和编码。  在调用ImagePacker的方法前，需要先通过[image.createImagePacker](arkts-image-image-createimagepacker-f.md#createimagepacker-1)构建一个ImagePacker实例。  编码期间，请避免修改或释放作为输入的ImageSource/PixelMap/Picture对象，以免出现crash或其他未定义行为。  由于图片占用内存较大，所以当ImagePacker实例使用完成后，应主动调用[release](arkts-image-image-imagepacker-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。  当前支持的格式有：JPEG、WebP、PNG、HEIC<sup>12+</sup>、GIF<sup>18+</sup>、从API版本26.0.0开始支持TIFF格式（不同硬件设备支持情况不同，可通过ImagePacker的supportedFormats属性查看）。 |
| [ImagePropertyOptions](arkts-image-image-imagepropertyoptions-i.md) | 表示查询图片属性的索引。 |
| [ImageRawData](arkts-image-image-imagerawdata-i.md) | 图像的RAW数据。 |
| [ImageReceiver](arkts-image-image-imagereceiver-i.md) | ImageReceiver类，用于获取组件surface id、接收最新的图片和读取下一张图片以及释放ImageReceiver实例。ImageReceiver作为图片的接收方和消费者，其参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方和生产者上进行，如相机预览流[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))。  在调用以下方法前需要先通过[image.createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-1)创建ImageReceiver实例。  从API version 23开始，更推荐使用[image.createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-1)，通过传入[ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md)创建ImageReceiver实例。  由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](arkts-image-image-imagereceiver-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md) | ImageReceiver的初始化选项。 |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource类，用于获取图片相关信息。  在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1)构建一个ImageSource实例。  ImageSource的所有方法均不支持并发调用。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [InitializationOptions](arkts-image-image-initializationoptions-i.md) | PixelMap的初始化选项。 |
| [Metadata](arkts-image-image-metadata-i.md) | Metadata类，用于存储图像的元数据。目前支持的元数据类型可参考[MetadataType](arkts-image-image-metadatatype-e.md)。 |
| [PackingOption](arkts-image-image-packingoption-i.md) | 表示图片编码选项。 |
| [PackingOptionsForSequence](arkts-image-image-packingoptionsforsequence-i.md) | 描述动图编码参数的选项。 |
| [PackingOptionsForTiff](arkts-image-image-packingoptionsfortiff-i.md) | 描述TIFF图像编码参数的选项。 |
| [PackingSizeLimit](arkts-image-image-packingsizelimit-i.md) | 图片编码的大小限制。 |
| [Picture](arkts-image-image-picture-i.md) | Picture类，一些包含特殊信息的图片可以解码为Picture（也可以称为多图对象）。多图对象一般包含主图、辅助图和元数据。其中主图包含图像的大部分信息，主要用于显示图像内容；辅助图用于存储与主图相关但不同的数据，展示图像更丰富的信息；元数据一般用来存储关于图像文件的信息。多图对象类用于读取或写入多图对象。在调用Picture的方法前，需要先通过[image.createPicture](arkts-image-image-createpicture-f.md#createpicture-1)创建一个Picture实例。  由于图片占用内存较大，所以当Picture实例使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
| [PixelMap](arkts-image-image-pixelmap-i.md) | The **PixelMap** class provides APIs to read or write image data and obtain image information. Before calling any API in PixelMap, you must use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)to create a PixelMap object. Currently, the maximum size of a serialized PixelMap is 128 MB. A larger size will cause a display failure. The size is calculated as follows: Width x Height x [Bytes per pixel](arkts-image-image-pixelmapformat-e.md).Since API version 11, PixelMap supports cross-thread calls through [Worker](../../apis-arkts/arkts-apis/arkts-worker.md). If a PixelMap object is invoked by another thread through [Worker](../../apis-arkts/arkts-apis/arkts-worker.md), all APIs of the PixelMap object cannot be called in the original thread. Otherwise, error 501 is reported, indicating that the server cannot complete the request.Before calling any API in PixelMap, you can use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)to pass pixel data to create a PixelMap object, or use [ImageSource](arkts-multimedia-image.md) to decode an image to a PixelMap object.To develop an atomic service, use [ImageSource](arkts-multimedia-image.md) to create a PixelMap object.Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](arkts-image-image-pixelmap-i.md#release-1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [PositionArea](arkts-image-image-positionarea-i.md) | 表示图片指定区域内的数据。 |
| [Region](arkts-image-image-region-i.md) | 表示区域信息。 |
| [Size](arkts-image-image-size-i.md) | 表示图片尺寸。 |
| [SourceOptions](arkts-image-image-sourceoptions-i.md) | ImageSource的初始化选项。 |
| [XMPEnumerateOptions](arkts-image-image-xmpenumerateoptions-i.md) | 表示XMP枚举选项。 |
| [XMPNamespace](arkts-image-image-xmpnamespace-i.md) | 表示XMP命名空间。 |
| [XMPTag](arkts-image-image-xmptag-i.md) | 表示XMP标签信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DecodingOptions](arkts-image-image-decodingoptions-i-sys.md) | 图像解码设置选项。 |
| [GainmapParams](arkts-image-image-gainmapparams-i-sys.md) | Gainmap（增益图）参数设置选项。 |
| [HdrDecomposeOptions](arkts-image-image-hdrdecomposeoptions-i-sys.md) | HDR PixelMap分解为Picture的配置选项，分解后的Picture包含一张SDR主图和一张增益图（GainMap）。 |
| [ImageSource](arkts-image-image-imagesource-i-sys.md) | ImageSource类，用于获取图片相关信息。  在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1)构建一个ImageSource实例。  ImageSource的所有方法均不支持并发调用。  由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AllocatorType](arkts-image-image-allocatortype-e.md) | 表示用于图像解码的内存类型的枚举。开发者可根据场景选择合适的内存申请类型。 |
| [AlphaType](arkts-image-image-alphatype-e.md) | 表示图像的透明度类型的枚举。 |
| [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 缩放时的插值算法。可根据缩放质量和性能需求选择合适的级别。 |
| [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | 表示辅助图的图像类型的枚举。  辅助图不直接参与图片显示，且并非所有图片中都含有辅助图。  在获取和使用特定辅助图前，应首先调用Picture的[getAuxiliaryPicture](arkts-image-image-picture-i.md#getauxiliarypicture-1)方法尝试获取该辅助图。 |
| [AvisPropertyKey](arkts-image-image-avispropertykey-e.md) | 表示AVIS图片信息的枚举。 |
| [ComponentType](arkts-image-image-componenttype-e.md) | 表示图像的组件类型的枚举。 |
| [CropAndScaleStrategy](arkts-image-image-cropandscalestrategy-e.md) | 表示裁剪与缩放的先后策略的枚举。  如果在配置解码选项[DecodingOptions](arkts-image-image-decodingoptions-i.md)时，未填入参数cropAndScaleStrategy，并且同时设置了参数desiredRegion和desiredSize，由于系统对于不同图片格式采用的解码算法不同，最终解码效果将略有差异。  例如原始图片大小为200x200，传入desiredSize:{width: 150, height: 150}，desiredRegion:{x: 0, y: 0, width: 100, height: 100}，即预期解码原图左上角1/4区域，最终将pixelMap大小缩放至150x150返回。  对于jpeg、webp图片（部分dng图片解码时会优先解码图片中的jpeg预览图，在此场景下也会被视为jpeg图片格式）会先进行下采样，例如按照7/8下采样，再基于175x175的图片大小进行区域裁剪，因此最终的区域内容稍大于原图的左上角1/4区域。  对于svg图片，由于是矢量图，可以任意缩放不损失清晰度，在解码时会根据desiredSize与原图Size的比例选择缩放比例，再基于缩放后的图片大小进行区域裁剪，因此最终返回的解码区域会有所差异。  针对该场景，建议在解码选项同时设置了desiredRegion与desiredSize时，参数cropAndScaleStrategy应传入CROP_FIRST保证效果一致。 |
| [DecodingDynamicRange](arkts-image-image-decodingdynamicrange-e.md) | 描述解码时期望的图像动态范围。 |
| [DngPropertyKey](arkts-image-image-dngpropertykey-e.md) | 表示DNG图片信息的枚举。 |
| [FocusMode](arkts-image-image-focusmode-e.md) | 表示焦点模式类型的枚举。 |
| [FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md) | 表示水印裁剪图图片信息的枚举。 |
| [GifPropertyKey](arkts-image-image-gifpropertykey-e.md) | 表示GIF图片信息的枚举。 |
| [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 表示[PixelMap](arkts-image-image-pixelmap-i.md)使用的HDR相关元数据信息的关键字的枚举。 |
| [HdrMetadataType](arkts-image-image-hdrmetadatatype-e.md) | 表示[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_METADATA_TYPE关键字对应的值的枚举。 |
| [HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md) | 表示HEIF序列图片信息的枚举。 |
| [ImageFormat](arkts-image-image-imageformat-e.md) | 表示图片格式的枚举。 |
| [JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md) | 表示JFIF图片信息的枚举。 |
| [MetadataType](arkts-image-image-metadatatype-e.md) | 表示图片元数据类型的枚举。 |
| [Orientation](arkts-image-image-orientation-e.md) | 表示图像方向类型的枚举。 |
| [PackingDynamicRange](arkts-image-image-packingdynamicrange-e.md) | 描述编码时期望的图像动态范围。 |
| [PixelMapFormat](arkts-image-image-pixelmapformat-e.md) | 表示图片像素格式的枚举。 |
| [PngPropertyKey](arkts-image-image-pngpropertykey-e.md) | 表示PNG图片信息的枚举。 |
| [PropertyKey](arkts-image-image-propertykey-e.md) | 表示Exif（Exchangeable image file format）图像信息的枚举。  - 格式示例中的key为：image.PropertyKey.XXX（XXX为枚举的名称，如：image.PropertyKey.NEW_SUBFILE_TYPE） 。  - 格式示例仅用于说明修改传值和读取结果的格式。具体接口使用方法请参考：[modifyImageProperty](arkts-image-image-imagesource-i.md#modifyimageproperty-1)（修改单个Exif字段）、[modifyImageProperties](arkts-image-image-imagesource-i.md#modifyimageproperties-1)（修改多个Exif字段）、[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)（读取单个Exif字段）、[getImageProperties](arkts-image-image-imagesource-i.md#getimageproperties-1)（读取多个Exif字段）。 |
| [ScaleMode](arkts-image-image-scalemode-e.md) | 表示图像的缩放模式的枚举。 |
| [TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md) | 表示TIFF图片信息的枚举。 |
| [WebPPropertyKey](arkts-image-image-webppropertykey-e.md) | 表示WebP图片信息的枚举。 |
| [XMPTagType](arkts-image-image-xmptagtype-e.md) | 表示XMP标签类型的枚举。 |
| [XmageColorMode](arkts-image-image-xmagecolormode-e.md) | 表示XMAGE颜色模式类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PropertyKey](arkts-image-image-propertykey-e-sys.md) | 表示Exif（Exchangeable image file format）图像信息的枚举。  - 格式示例中的key为：image.PropertyKey.XXX（XXX为枚举的名称，如：image.PropertyKey.NEW_SUBFILE_TYPE） 。  - 格式示例仅用于说明修改传值和读取结果的格式。具体接口使用方法请参考：[modifyImageProperty](arkts-image-image-imagesource-i.md#modifyimageproperty-1)（修改单个Exif字段）、[modifyImageProperties](arkts-image-image-imagesource-i.md#modifyimageproperties-1)（修改多个Exif字段）、[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)（读取单个Exif字段）、[getImageProperties](arkts-image-image-imagesource-i.md#getimageproperties-1)（读取多个Exif字段）。 |
| [ResolutionQuality](arkts-image-image-resolutionquality-e-sys.md) | 枚举，画质效果等级类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | PixelMap使用的HDR元数据值类型，与[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)关键字对应。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW](arkts-image-image-con.md#capture_mode_front_lens_night_view) | 拍摄模式：前置摄像头夜景模式。 |
| [CAPTURE_MODE_LIGHT_GRAFFITI](arkts-image-image-con.md#capture_mode_light_graffiti) | 拍摄模式：轻涂鸦模式。 |
| [CAPTURE_MODE_MOVING_PHOTO](arkts-image-image-con.md#capture_mode_moving_photo) | 拍摄模式：动态照片模式。 |
| [CAPTURE_MODE_PANORAMA](arkts-image-image-con.md#capture_mode_panorama) | 拍摄模式：全景模式。 |
| [CAPTURE_MODE_PORTRAIT](arkts-image-image-con.md#capture_mode_portrait) | 拍摄模式：人像模式。 |
| [CAPTURE_MODE_PROFESSIONAL](arkts-image-image-con.md#capture_mode_professional) | 拍摄模式：专业模式。 |
| [CAPTURE_MODE_REAR_LENS_NIGHT_VIEW](arkts-image-image-con.md#capture_mode_rear_lens_night_view) | 拍摄模式：后镜头夜景模式。 |
| [CAPTURE_MODE_SILKY_WATER](arkts-image-image-con.md#capture_mode_silky_water) | 拍摄模式：缎面感水流模式。 |
| [CAPTURE_MODE_SNAP_SHOT](arkts-image-image-con.md#capture_mode_snap_shot) | 拍摄模式：抓拍模式。 |
| [CAPTURE_MODE_STAR_TRACK](arkts-image-image-con.md#capture_mode_star_track) | 拍摄模式：星轨模式。 |
| [CAPTURE_MODE_SUPER_MACRO](arkts-image-image-con.md#capture_mode_super_macro) | 拍摄模式：超微距模式。 |
| [CAPTURE_MODE_TAIL_LIGHT](arkts-image-image-con.md#capture_mode_tail_light) | 拍摄模式：尾灯模式。 |
| [CAPTURE_MODE_WIDEAPERTURE](arkts-image-image-con.md#capture_mode_wideaperture) | 拍摄模式：广角模式。 |
| [DUBLIN_CORE](arkts-image-image-con.md#dublin_core) | Dublin Core元数据命名空间。 |
| [EXIF](arkts-image-image-con.md#exif) | EXIF元数据命名空间。 |
| [TIFF](arkts-image-image-con.md#tiff) | TIFF图像格式参数命名空间。 |
| [XMAGE_WATERMARK_MODE_AT_THE_BOTTOM](arkts-image-image-con.md#xmage_watermark_mode_at_the_bottom) | XMAGE水印模式：XMAGE水印固定位于图像底部中央。 |
| [XMAGE_WATERMARK_MODE_BORDER](arkts-image-image-con.md#xmage_watermark_mode_border) | XMAGE水印模式：XMAGE水印会自动调整到边界位置，系统根据图像内容选择最适合的边界区域。 |
| [XMP_BASIC](arkts-image-image-con.md#xmp_basic) | XMP基础命名空间。 |
| [XMP_RIGHTS](arkts-image-image-con.md#xmp_rights) | XMP版权与权限命名空间。 |

