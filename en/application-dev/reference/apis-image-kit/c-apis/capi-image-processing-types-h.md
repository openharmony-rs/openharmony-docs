# image_processing_types.h

## Overview

Type definitions for image processing.

**Library**: libimage_processing.so

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 13

**Related module**: [ImageProcessing](capi-imageprocessing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ImageProcessing_ColorSpaceInfo](capi-imageprocessing-imageprocessing-colorspaceinfo.md) | ImageProcessing_ColorSpaceInfo | The color space information is used for color space conversion capability query. |
| [OH_ImageProcessing](capi-imageprocessing-oh-imageprocessing.md) | OH_ImageProcessing | Define the object for image processing.<br> Define a null pointer of OH_ImageProcessing and call {@link OH_ImageProcessing_Create} to create an image processing instance. The pointer should be null before creating instance. User can create multiple image processing instances for different processing types. |
| [OH_PixelmapNative](capi-imageprocessing-oh-pixelmapnative.md) | OH_PixelmapNative | Forward declaration of OH_PixelmapNative. |
| [OH_AVFormat](capi-imageprocessing-oh-avformat.md) | OH_AVFormat | Forward declaration of OH_AVFormat. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ImageDetailEnhancer_QualityLevel](#imagedetailenhancer_qualitylevel) | ImageDetailEnhancer_QualityLevel | The quality level is used for detail enhancement.<br> It is the value of the key parameter [IMAGE_DETAIL_ENHANCER_PARAMETER_KEY_QUALITY_LEVEL](capi-image-processing-types-h.md#变量). |
| [ImageProcessing_ErrorCode](#imageprocessing_errorcode) | ImageProcessing_ErrorCode | Image processing error code. |

### Variable

| Name | Description |
| -- | -- |
| const int32_t IMAGE_PROCESSING_TYPE_COLOR_SPACE_CONVERSION | Used to create an image processing instance for color space conversion.<br> Color space conversion includes the conversion of single-layer HDR images to SDR images, as well as the color space conversion of SDR images, and the conversion of SDR images to single-layer HDR images. Some capabilities are supported by vendor. Use {@link OH_ImageProcessing_IsColorSpaceConversionSupported} to query if the conversion is supported between single-layer images.<br>**Since**: 13 |
| const int32_t IMAGE_PROCESSING_TYPE_COMPOSITION | Used to create an image processing instance for HDR image composition.<br> HDR image compose includes the conversion from dual-layer HDR images to single-layer HDR images. Some capabilities are supported by vendor. Use {@link OH_ImageProcessing_IsCompositionSupported} to query if the composition is supported from dual-layer HDR image to single-layer HDR image.<br>**Since**: 13 |
| const int32_t IMAGE_PROCESSING_TYPE_DECOMPOSITION | Used to create an image processing instance for HDR image decomposition.<br> HDR image decompose includes the conversion from single-layer HDR images to dual-layer HDR images. Some capabilities are supported by vendor. Use {@link OH_ImageProcessing_IsDecompositionSupported} to query if the decomposition is supported from single-layer image to dual-layer HDR image.<br>**Since**: 13 |
| const int32_t IMAGE_PROCESSING_TYPE_METADATA_GENERATION | Used to create an image processing instance for metadata generation.<br> Generate HDR Vivid metadata for single-layer image. The capability is supported by vendor. If the capability is not supported, {@link OH_ImageProcessing_Create} returns [IMAGE_PROCESSING_ERROR_UNSUPPORTED_PROCESSING](capi-image-processing-types-h.md#imageprocessing_errorcode).<br>**Since**: 13 |
| const int32_t IMAGE_PROCESSING_TYPE_DETAIL_ENHANCER | Used to create an image processing instance for detail enhancement.<br> Scale or resize images with the specified quality or just enhance details for rendering an image without changing its resolution.<br>**Since**: 13 |
| const char *IMAGE_DETAIL_ENHANCER_PARAMETER_KEY_QUALITY_LEVEL | The key is used to specify the quality level for image detail enhancement.<br> See [ImageDetailEnhancer_QualityLevel](capi-image-processing-types-h.md#imagedetailenhancer_qualitylevel) for its value.<br>Use {@link OH_ImageProcessing_SetParameter} to set the quality level.<br>Use {@link OH_ImageProcessing_GetParameter} to get the current quality level.<br>**Since**: 13 |

## Enum type description

### ImageDetailEnhancer_QualityLevel

```c
enum ImageDetailEnhancer_QualityLevel
```

**Description**

The quality level is used for detail enhancement.<br> It is the value of the key parameter [IMAGE_DETAIL_ENHANCER_PARAMETER_KEY_QUALITY_LEVEL](capi-image-processing-types-h.md#变量).

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 13

| Enum item | Description |
| -- | -- |
| IMAGE_DETAIL_ENHANCER_QUALITY_LEVEL_NONE | No detail enhancement |
| IMAGE_DETAIL_ENHANCER_QUALITY_LEVEL_LOW | A low level of detail enhancement quality but with a fast speed. It's the default level |
| IMAGE_DETAIL_ENHANCER_QUALITY_LEVEL_MEDIUM | A medium level of detail enhancement quality. Its speed is between the low setting and high setting |
| IMAGE_DETAIL_ENHANCER_QUALITY_LEVEL_HIGH | A high level of detail enhancement quality but with a relatively slow speed |

**Reference**:

OH_ImageProcessing_SetParameter
OH_ImageProcessing_GetParameter


### ImageProcessing_ErrorCode

```c
enum ImageProcessing_ErrorCode
```

**Description**

Image processing error code.

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 13

| Enum item | Description |
| -- | -- |
| IMAGE_PROCESSING_SUCCESS | @error Operation is successful. |
| IMAGE_PROCESSING_ERROR_INVALID_PARAMETER = 401 | Input parameter is invalid. This error is returned for all of the following error conditions: 1 - Invalid input or output image buffer - The image buffer is null. 2 - Invalid parameter - The parameter is null. 3 - Invalid type - The type passed in the create function does not exist. |
| IMAGE_PROCESSING_ERROR_UNKNOWN = 29200001 | @error Some unknown error occurred, such as GPU calculation failure or memcpy failure. |
| IMAGE_PROCESSING_ERROR_INITIALIZE_FAILED | The global environment initialization for image processing failed, such as failure to initialize the GPU environment. |
| IMAGE_PROCESSING_ERROR_CREATE_FAILED | Failed to create image processing instance. For example, the number of instances exceeds the upper limit. |
| IMAGE_PROCESSING_ERROR_PROCESS_FAILED | @error Failed to process image buffer. For example, the processing times out. |
| IMAGE_PROCESSING_ERROR_UNSUPPORTED_PROCESSING | The processing is not supported. You may call OH_ImageProcessing_IsXXXSupported to check whether the capability is supported. |
| IMAGE_PROCESSING_ERROR_OPERATION_NOT_PERMITTED | @error The operation is not permitted. This may be caused by incorrect status. |
| IMAGE_PROCESSING_ERROR_NO_MEMORY | @error Out of memory. |
| IMAGE_PROCESSING_ERROR_INVALID_INSTANCE | @error The image processing instance is invalid. This may be caused by null instance. |
| IMAGE_PROCESSING_ERROR_INVALID_VALUE | Input value is invalid. This error is returned for all of the following error conditions: 1 - Invalid input or output image buffer - The image buffer width(height) is too large or colorspace is incorrect. 2 - Invalid parameter - The parameter does not contain valid information, such as detail enhancer level is incorrect. |


