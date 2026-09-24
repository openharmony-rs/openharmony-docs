# @ohos.multimedia.image

The module provides capabilities for image decoding, encoding, editing, metadata processing, and image receiving. This module contains the following classes:

- [ImageSource](arkts-image-image-imagesource-i.md): provides the capabilities of obtaining [image information](arkts-image-image-imageinfo-i.md), decoding images to PixelMaps or Pictures, and reading and modifying [image properties](arkts-image-image-propertykey-e.md). [Supported image formats for decoding](arkts-image-image-imagesource-i.md#supportedformats) include png, jpeg, bmp, gif, webp, dng, and heic&lt;sup&gt;12+&lt;/sup&gt;.

- [ImagePacker](arkts-image-image-imagepacker-i.md): provides the capability of encoding images into  
compressed data streams or files. Encoding requires the ImageSource, PixelMap, or Picture of an image as the input. [Supported image formats for encoding](arkts-image-image-imagepacker-i.md#supportedformats) include jpeg, webp, png, heic&lt;sup&gt;12+&lt;/sup&gt;, and gif&lt;sup&gt;18+&lt;/sup&gt;.

- [PixelMap](arkts-image-image-pixelmap-i.md): contains pixel data and [image information](arkts-image-image-imageinfo-i.md). It can be used for reading/writing pixel data and performing operations such as cropping, scaling, translating, rotating, and mirroring. It can also be directly passed to the [Image component](arkts-image-image-image-i.md) for display. Additionally, it provides APIs for obtaining and setting the color gamut and HDR metadata of images.

- [Picture](arkts-image-image-picture-i.md): a multi-picture object composed of a main picture,  
auxiliary pictures, and metadata. The main picture contains the primary image information; auxiliary pictures store additional information related to the main picture; metadata stores other information related to the image. Picture provides methods for obtaining the main picture, compositing HDR images, obtaining and setting auxiliary pictures, and obtaining and setting metadata.

- [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md): used to display special information  
alongside the main picture, enriching the overall content of the image. The supported types of auxiliary pictures can be found in [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md).

- [Metadata](arkts-image-image-metadata-i.md): stores image metadata in key-value format. The supported  
metadata types can be found in [MetadataType](arkts-image-image-metadatatype-e.md), including Exif metadata, fragment map metadata, and HEIF sequence image metadata. For details about the keys of Exif metadata, fragment map metadata, and HEIF sequence image metadata, see [PropertyKey](arkts-image-image-propertykey-e.md), [FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md), and [HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md), respectively.

- [ExifMetadata](arkts-image-image-exifmetadata-c.md): stores Exif metadata of images in key-value format. For details about  
the keys of Exif metadata, see [PropertyKey](arkts-image-image-propertykey-e.md).

- [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md): stores photo metadata defined by Huawei cameras  
in key-value format. For details about keys of HUAWEI camera-defined photo metadata, see [PropertyKey](arkts-image-image-propertykey-e.md).

- [HeifsMetadata](arkts-image-image-makernotehuaweimetadata-c.md): stores HEIF sequence image metadata of images in key-value  
format. For details about keys of HEIF sequence image metadata, see [HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md).

- [WebPMetadata](arkts-image-image-webpmetadata-c.md): stores WebP image metadata in key-value format. For details about keys  
in WebP image metadata, see [WebPPropertyKey](arkts-image-image-webppropertykey-e.md).

- [GifMetadata](arkts-image-image-gifmetadata-c.md): stores GIF image metadata in key-value format. For details about keys in  
GIF image metadata, see [GifPropertyKey](arkts-image-image-gifpropertykey-e.md).

- [JfifMetadata](arkts-image-image-jfifmetadata-c.md): stores JFIF image metadata in key-value format. For details about keys  
in JFIF image metadata, see [JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md).

- [TiffMetadata](arkts-image-image-tiffmetadata-c.md): stores TIFF image metadata in key-value format. For details about keys  
in TIFF image metadata, see [TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md).

- [PngMetadata](arkts-image-image-pngmetadata-c.md): stores PNG image metadata in key-value format. For details about keys in  
PNG image metadata, see [PngPropertyKey](arkts-image-image-pngpropertykey-e.md).

- [AvisMetadata](arkts-image-image-avismetadata-c.md): stores AVIS image metadata in key-value format. For details about keys  
in AVIS image metadata, see [AvisPropertyKey](arkts-image-image-avispropertykey-e.md).

- [ImageReceiver](arkts-image-image-imagereceiver-i.md): acts as a consumer of images, used for receiving  
and reading images from a surface.

- [ImageCreator](arkts-image-image-imagecreator-i.md): acts as a producer of images, used for writing  
images into a surface.

- [Image](arkts-image-image-image-i.md): used by ImageReceiver and ImageCreator for transferring image  
objects, with the actual content determined by the producer. For example, the Image object provided by a camera preview stream contains YUV data, whereas the Image object provided by a camera photo contains a JPEG file.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAuxiliaryPicture](arkts-image-image-createauxiliarypicture-f.md) | Creates an AuxiliaryPicture instance based on the ArrayBuffer image data, auxiliary picture size, and auxiliary picture type. This API accepts only continuous pixel data in BGRA format and will create an auxiliary picture in RGBA format. |
| [createAuxiliaryPictureUsingAllocator](arkts-image-image-createauxiliarypictureusingallocator-f.md) | Create an &lt;b&gt;AuxiliaryPicture&lt;/b&gt; object, the memory type used by the AuxiliaryPicture can be specified by allocatorType IMAGE_ALLOCATOR_TYPE. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the AuxiliaryPicture returned by this interface, please always consider the impact of stride. The created auxiliary picture is initialized with the input pixels. |
| [createEmptyPixelMap](arkts-image-image-createemptypixelmap-f.md) | Creates an empty PixelMap. |
| [createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator) | Creates an ImageCreator instance by specifying the image width, height, format, and capacity. Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](arkts-image-image-imagecreator-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator-1) | Creates an ImageCreator instance by specifying the image size, format, and capacity. Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](arkts-image-image-imagecreator-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImagePacker](arkts-image-image-createimagepacker-f.md) | Creates an ImagePacker instance. |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver) | Creates an ImageReceiver instance by specifying the image width, height, format, and capacity. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-image-imagereceiver-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-1) | Creates an ImageReceiver instance by specifying the image size, format, and capacity. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-image-imagereceiver-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver-3) | Creates an ImageReceiver instance. |
| [createImageSource](arkts-image-image-createimagesource-f.md) | Creates an ImageSource instance based on a given URI. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-2) | Creates an ImageSource instance based on a given URI. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-4) | Creates an ImageSource instance based on a given file descriptor. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-6) | Creates an ImageSource instance based on a given file descriptor. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-8) | Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](arkts-image-image-imagesource-i.md#createpixelmapsync). Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-10) | Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](arkts-image-image-imagesource-i.md#createpixelmapsync). Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-12) | Creates an ImageSource instance based on the raw file descriptor of an image resource file. Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource) | Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information. |
| [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource-1) | Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information. |
| [createPicture](arkts-image-image-createpicture-f.md) | Creates a Picture object based on a main PixelMap. |
| [createPictureFromParcel](arkts-image-image-createpicturefromparcel-f.md) | Creates a Picture object from a MessageSequence object. |
| [createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap) | Create pixelmap by data buffer. |
| [createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) | Create pixelmap by data buffer. |
| [createPixelMapFromParcel](arkts-image-image-createpixelmapfromparcel-f.md) | Creates a PixelMap object based on MessageSequence parameter. |
| [createPixelMapFromPixels](arkts-image-image-createpixelmapfrompixels-f.md) | Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap. |
| [createPixelMapFromPixelsSync](arkts-image-image-createpixelmapfrompixelssync-f.md) | Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap. |
| [createPixelMapFromSurface](arkts-image-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurface](arkts-image-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface-1) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceSync](arkts-image-image-createpixelmapfromsurfacesync-f.md#createpixelmapfromsurfacesync) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceSync](arkts-image-image-createpixelmapfromsurfacesync-f.md#createpixelmapfromsurfacesync-1) | Creates a PixelMap object from surface id. |
| [createPixelMapFromSurfaceWithTransformation](arkts-image-image-createpixelmapfromsurfacewithtransformation-f.md) | Creates a PixelMap object based on the ID of a Surface with transformation. |
| [createPixelMapFromSurfaceWithTransformationSync](arkts-image-image-createpixelmapfromsurfacewithtransformationsync-f.md) | Creates a PixelMap object based on the ID of a Surface with transformation. |
| [createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync) | Create pixelmap by data buffer. |
| [createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync-1) | Create an empty pixelmap. |
| [createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md) | Create pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md#createpixelmapusingallocatorsync) | Create pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md#createpixelmapusingallocatorsync-1) | Create an empty pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride. |
| [createPremultipliedPixelMap](arkts-image-image-createpremultipliedpixelmap-f.md#createpremultipliedpixelmap) | Transforms pixelmap from unpremultiplied alpha format to premultiplied alpha format. |
| [createPremultipliedPixelMap](arkts-image-image-createpremultipliedpixelmap-f.md#createpremultipliedpixelmap-1) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [createUnpremultipliedPixelMap](arkts-image-image-createunpremultipliedpixelmap-f.md#createunpremultipliedpixelmap) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [createUnpremultipliedPixelMap](arkts-image-image-createunpremultipliedpixelmap-f.md#createunpremultipliedpixelmap-1) | Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format. |
| [getImagePackerSupportedFormats](arkts-image-image-getimagepackersupportedformats-f.md) | Obtains the supported encoding formats, represented by MIME types. |
| [getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md) | Obtains the supported decoding formats, represented by MIME types. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createPictureByHdrAndSdrPixelMap](arkts-image-image-createpicturebyhdrandsdrpixelmap-f-sys.md#createpicturebyhdrandsdrpixelmap) | Creates a Picture object based on an HDR PixelMap and an SDR PixelMap. The system uses the HDR PixelMap and SDR PixelMap to generate a gainmap. The returned Picture object contains the SDR PixelMap and the generated gainmap, both in RGBA8888 format. This API uses a promise to return the result. |
| [createPictureByHdrAndSdrPixelMap](arkts-image-image-createpicturebyhdrandsdrpixelmap-f-sys.md#createpicturebyhdrandsdrpixelmap-1) | Creates a Picture object by a HDR PixelMap and a SDR PixelMap with specified options. A gainmap will be generated using the HDR and SDR PixelMap, and the returned Picture will contain the SDR PixelMap and the generated gainmap. |
| [decomposeToPicture](arkts-image-image-decomposetopicture-f-sys.md) | Decomposes an HDR Pixelmap object to a Picture object which contains an SDR PixelMap and a gainmap. This API uses a promise to return the result. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [AvisMetadata](arkts-image-image-avismetadata-c.md) | Avis metadata. |
| [DngMetadata](arkts-image-image-dngmetadata-c.md) | DNG metadata. |
| [ExifMetadata](arkts-image-image-exifmetadata-c.md) | ExifMetadata implements Metadata |
| [GifMetadata](arkts-image-image-gifmetadata-c.md) | Gif metadata. |
| [HeifsMetadata](arkts-image-image-heifsmetadata-c.md) | HeifsMetadata implements Metadata |
| [JfifMetadata](arkts-image-image-jfifmetadata-c.md) | JFIF metadata. |
| [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) | MakerNoteHuaweiMetadata implements Metadata |
| [PngMetadata](arkts-image-image-pngmetadata-c.md) | Png metadata. |
| [TiffMetadata](arkts-image-image-tiffmetadata-c.md) | TIFF metadata. |
| [WebPMetadata](arkts-image-image-webpmetadata-c.md) | WebP metadata. |
| [XMPMetadata](arkts-image-image-xmpmetadata-c.md) | XMPMetadata instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | The **AuxiliaryPicture** class is used to read or write auxiliary picture data of an image and obtain auxiliary picture information of an image. The supported types of auxiliary pictures can be found in [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md). |
| [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | Describes the auxiliary picture information. |
| [BinaryBufferInfo](arkts-image-image-binarybufferinfo-i.md) | Describes binary buffer info. |
| [Component](arkts-image-image-component-i.md) | Describes the color components of an image. |
| [DecodingOptions](arkts-image-image-decodingoptions-i.md) | Describes the image decoding options. |
| [DecodingOptionsForPicture](arkts-image-image-decodingoptionsforpicture-i.md) | Describes the image decoding options. |
| [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | Describes thumbnail decoding parameters. |
| [GainmapChannel](arkts-image-image-gainmapchannel-i.md) | Describes the data content of a single channel of the gain map. For details, see ISO 21496-1. |
| [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | Describes the image properties. |
| [HdrComposeOptions](arkts-image-image-hdrcomposeoptions-i.md) | Describes compose parameters. |
| [HdrGainmapMetadata](arkts-image-image-hdrgainmapmetadata-i.md) | Describes the metadata keys used by a gain map, that is, the values available for **HDR_GAINMAP_METADATA** in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). For details, see ISO 21496-1. |
| [HdrStaticMetadata](arkts-image-image-hdrstaticmetadata-i.md) | Describes the static metadata keys, that is, the values available for **HDR_STATIC_METADATA** in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
| [Image](arkts-image-image-image-i.md) | The **Image** class is used to obtain image content. |
| [ImageBufferData](arkts-image-image-imagebufferdata-i.md) | Describes the image buffer data. |
| [ImageCreator](arkts-image-image-imagecreator-i.md) | The ImageCreator class provides APIs for applications to request an image data area and compile image data. |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | Describes image information. |
| [ImageMetadata](arkts-image-image-imagemetadata-i.md) | Metadata set of an image. |
| [ImagePacker](arkts-image-image-imagepacker-i.md) | The **ImagePacker** class provides APIs to compress and encode images. |
| [ImagePropertyOptions](arkts-image-image-imagepropertyoptions-i.md) | Describes the image properties. |
| [ImageRawData](arkts-image-image-imagerawdata-i.md) | Describes raw data in an image. |
| [ImageReceiver](arkts-image-image-imagereceiver-i.md) | The **ImageReceiver** class provides APIs to obtain the surface ID of a component, read the latest image, read the next image, and release the ImageReceiver instance. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Before calling any APIs in ImageReceiver, you must use [image.createImageReceiver](arkts-image-image-createimagereceiver-f.md) to create an ImageReceiver instance. Since API version 23, you are advised to use [image.createImageReceiver](arkts-image-image-createimagereceiver-f.md) to create an **ImageReceiver** instance based on the passed [ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-image-imagereceiver-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md) | Describes the initialization options for ImageReceiver. |
| [ImageSource](arkts-image-image-imagesource-i.md) | The **ImageSource** class provides APIs to obtain image information. |
| [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Defines PixelMap initialization options. |
| [Metadata](arkts-image-image-metadata-i.md) | The **Metadata** class provides APIs for storing image metadata. For details about the supported metadata types, see [MetadataType](arkts-image-image-metadatatype-e.md). |
| [PackingOption](arkts-image-image-packingoption-i.md) | Describes the options for image encoding. |
| [PackingOptionsForSequence](arkts-image-image-packingoptionsforsequence-i.md) | Defines the options for encoding animated images. |
| [PackingOptionsForTiff](arkts-image-image-packingoptionsfortiff-i.md) | Describes the options for tiff image packing. |
| [PackingSizeLimit](arkts-image-image-packingsizelimit-i.md) | Packing image size limit. |
| [Picture](arkts-image-image-picture-i.md) | An image that contains special information can be decoded into a picture object, which generally contains the main picture, auxiliary picture, and metadata. The main picture contains most information about the image and is mainly used to render the image. The auxiliary picture is used to store data related to but different from the main picture, revealing more comprehensive details. The metadata is generally used to store information about the image file. The picture object class is used to read or write picture objects. Before calling any API in Picture, you must use [image.createPicture](arkts-image-image-createpicture-f.md) to create a Picture object. |
| [PixelMap](arkts-image-image-pixelmap-i.md) | The **PixelMap** class provides APIs to read or write image data and obtain image information. Before calling any API in PixelMap, you must use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) to create a PixelMap object. Currently, the maximum size of a serialized PixelMap is 128 MB. A larger size will cause a display failure. The size is calculated as follows: Width x Height x [Bytes per pixel](arkts-image-image-pixelmapformat-e.md). Since API version 11, PixelMap supports cross-thread calls through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md). If a PixelMap object is invoked by another thread through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md), all APIs of the PixelMap object cannot be called in the original thread. Otherwise, error 501 is reported, indicating that the server cannot complete the request. Before calling any API in PixelMap, you can use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) to pass pixel data to create a PixelMap object, or use [ImageSource](arkts-image-multimedia-image.md) to decode an image to a PixelMap object. To develop an atomic service, use [ImageSource](arkts-image-multimedia-image.md) to create a PixelMap object. Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](arkts-image-image-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed. |
| [PositionArea](arkts-image-image-positionarea-i.md) | Describes area information in an image. |
| [Region](arkts-image-image-region-i.md) | Describes the region information. |
| [Size](arkts-image-image-size-i.md) | Describes the size of an image. |
| [SourceOptions](arkts-image-image-sourceoptions-i.md) | Defines image source initialization options. |
| [XMPEnumerateOptions](arkts-image-image-xmpenumerateoptions-i.md) | Describes XMP enumerate option parameters. |
| [XMPNamespace](arkts-image-image-xmpnamespace-i.md) | Describes XMP namespace parameters. |
| [XMPTag](arkts-image-image-xmptag-i.md) | Describes XMP Tag parameters. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DecodingOptions](arkts-image-image-decodingoptions-i-sys.md) | Describes the image decoding options. |
| [GainmapParams](arkts-image-image-gainmapparams-i-sys.md) | Describes gainmap generation parameters. |
| [HdrDecomposeOptions](arkts-image-image-hdrdecomposeoptions-i-sys.md) | Describes the options for decomposing an HDR Pixelmap to a Picture containing an SDR PixelMap and a gainmap. |
| [ImageSource](arkts-image-image-imagesource-i-sys.md) | The **ImageSource** class provides APIs to obtain image information. |
| [PackingOption](arkts-image-image-packingoption-i-sys.md) | Describes the options for image encoding. |
| [SourceOptions](arkts-image-image-sourceoptions-i-sys.md) | Defines image source initialization options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AllocatorType](arkts-image-image-allocatortype-e.md) | Enumerates the types of the memory used for image decoding. |
| [AlphaType](arkts-image-image-alphatype-e.md) | Enumerates the alpha types of images. |
| [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | Enumerates the anti-aliasing levels. |
| [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | Enumerates the auxiliary pictures types. |
| [AvisPropertyKey](arkts-image-image-avispropertykey-e.md) | Enumerates the properties available for the metadata of a Avis image. |
| [ComponentType](arkts-image-image-componenttype-e.md) | Enumerates the color component types of images. |
| [CropAndScaleStrategy](arkts-image-image-cropandscalestrategy-e.md) | Enumerates the order of cropping and scaling. |
| [DecodingDynamicRange](arkts-image-image-decodingdynamicrange-e.md) | Enumerates the desired dynamic range of an image during decoding. |
| [DngPropertyKey](arkts-image-image-dngpropertykey-e.md) | Enumerates the properties available for the metadata of a DNG image. |
| [FocusMode](arkts-image-image-focusmode-e.md) | Enumerates the focus modes. |
| [FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md) | Enumerates the fragment map information. |
| [GifPropertyKey](arkts-image-image-gifpropertykey-e.md) | Enumerates the GIF image information. |
| [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | Enumerates the keys of HDR metadata used by [pixelmap](arkts-image-image-pixelmap-i.md). |
| [HdrMetadataType](arkts-image-image-hdrmetadatatype-e.md) | Enumerates the values available for **HDR_METADATA_TYPE** in [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |
| [HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md) | Enumerates the properties available for the metadata of a HEIFS image. |
| [ImageFormat](arkts-image-image-imageformat-e.md) | Enumerates the image formats. |
| [JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md) | Enumerates the properties available for the metadata of a JFIF image. |
| [MetadataType](arkts-image-image-metadatatype-e.md) | Enumerates image metadata types. |
| [Orientation](arkts-image-image-orientation-e.md) | Enumerates image orientation. |
| [PackingDynamicRange](arkts-image-image-packingdynamicrange-e.md) | Enumerates the desired dynamic range of an image during encoding. |
| [PixelMapFormat](arkts-image-image-pixelmapformat-e.md) | Enumerates the pixel formats of images. |
| [PngPropertyKey](arkts-image-image-pngpropertykey-e.md) | Enumerates the properties available for the metadata of a PNG image. |
| [PropertyKey](arkts-image-image-propertykey-e.md) | Enumerates the types of Exchangeable Image File Format (Exif) data of an image. |
| [ScaleMode](arkts-image-image-scalemode-e.md) | Enumerates the scale modes of images. |
| [TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md) | Enumerates the properties available for the metadata of a TIFF image. |
| [WebPPropertyKey](arkts-image-image-webppropertykey-e.md) | Enumerates the properties available for the metadata of a WebP image. |
| [XmageColorMode](arkts-image-image-xmagecolormode-e.md) | Enumerates the XMAGE color modes. |
| [XMPTagType](arkts-image-image-xmptagtype-e.md) | Enumerates XMP tag type. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PropertyKey](arkts-image-image-propertykey-e-sys.md) | Enumerates the types of Exchangeable Image File Format (Exif) data of an image. |
| [ResolutionQuality](arkts-image-image-resolutionquality-e-sys.md) | Enumerates the image quality levels. |
| [SVGResourceLimitLevel](arkts-image-image-svgresourcelimitlevel-e-sys.md) | Enumerates SVG resource limit levels. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | Describes the HDR metadata values used by a PixelMap, which corresponds to the values available for [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md). |

### Constants

| Name | Description |
| --- | --- |
| [CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW](arkts-image-image-con.md#capture_mode_front_lens_night_view) | Capture mode: night view with front lens.The value is 7. |
| [CAPTURE_MODE_LIGHT_GRAFFITI](arkts-image-image-con.md#capture_mode_light_graffiti) | Capture mode: light graffiti.The value is 10. |
| [CAPTURE_MODE_MOVING_PHOTO](arkts-image-image-con.md#capture_mode_moving_photo) | Capture mode: moving photos.The value is 20. |
| [CAPTURE_MODE_PANORAMA](arkts-image-image-con.md#capture_mode_panorama) | Capture mode: panorama.The value is 8. |
| [CAPTURE_MODE_PORTRAIT](arkts-image-image-con.md#capture_mode_portrait) | Capture mode: portrait.The value is 23. |
| [CAPTURE_MODE_PROFESSIONAL](arkts-image-image-con.md#capture_mode_professional) | Capture mode: professional.The value is 2. |
| [CAPTURE_MODE_REAR_LENS_NIGHT_VIEW](arkts-image-image-con.md#capture_mode_rear_lens_night_view) | Capture mode: night view with rear lens.The value is 42. |
| [CAPTURE_MODE_SILKY_WATER](arkts-image-image-con.md#capture_mode_silky_water) | Capture mode: silky water.The value is 11. |
| [CAPTURE_MODE_SNAP_SHOT](arkts-image-image-con.md#capture_mode_snap_shot) | Capture mode: snap shot.The value is 62. |
| [CAPTURE_MODE_STAR_TRACK](arkts-image-image-con.md#capture_mode_star_track) | Capture mode: star track.The value is 12. |
| [CAPTURE_MODE_SUPER_MACRO](arkts-image-image-con.md#capture_mode_super_macro) | Capture mode: super macro.The value is 47. |
| [CAPTURE_MODE_TAIL_LIGHT](arkts-image-image-con.md#capture_mode_tail_light) | Capture mode: tail light.The value is 9. |
| [CAPTURE_MODE_WIDEAPERTURE](arkts-image-image-con.md#capture_mode_wideaperture) | Capture mode: wide aperture.The value is 19. |
| [DUBLIN_CORE](arkts-image-image-con.md#dublin_core) | XMP namespace: dublin core. Namespace uri: 'http://purl.org/dc/elements/1.1/', prefix: 'dc' |
| [EXIF](arkts-image-image-con.md#exif) | XMP namespace: exif. Namespace uri: 'http://ns.adobe.com/exif/1.0/', prefix: 'exif' |
| [TIFF](arkts-image-image-con.md#tiff) | XMP namespace: tiff. Namespace uri: 'http://ns.adobe.com/tiff/1.0/', prefix: 'tiff' |
| [XMAGE_WATERMARK_MODE_AT_THE_BOTTOM](arkts-image-image-con.md#xmage_watermark_mode_at_the_bottom) | The XMAGE watermark is at the bottom of the photo.The value is 9. |
| [XMAGE_WATERMARK_MODE_BORDER](arkts-image-image-con.md#xmage_watermark_mode_border) | The XMAGE watermark is around the edges of the photo.The value is 10. |
| [XMP_BASIC](arkts-image-image-con.md#xmp_basic) | XMP namespace: XMP basic. Namespace uri: 'http://ns.adobe.com/xap/1.0/', prefix: 'xmp' |
| [XMP_RIGHTS](arkts-image-image-con.md#xmp_rights) | XMP namespace: XMP rights. Namespace uri: 'http://ns.adobe.com/xap/1.0/rights/', prefix: 'xmpRights' |
