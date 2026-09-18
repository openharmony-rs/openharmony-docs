# image_mdk.h

## Overview

Declares functions that access the image rectangle, size, format, and component data. Need link <b>libimagendk.z.so</b>

**Library**: libimage_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OhosImageRect](capi-image-ohosimagerect.md) | - | Defines the information about an image rectangle. |
| [OhosImageComponent](capi-image-ohosimagecomponent.md) | - | Defines the image composition information. |
| [ImageNative_](capi-image-imagenative-.md) | ImageNative | Defines an image object at the native layer for the image interface. |

### Enum

| Name | Description |
| -- | -- |
| [anonymous0](#anonymous0) | Enumerates the image formats. |
| [anonymous1](#anonymous1) | Enumerates the image components. |

### Function

| Name | Description |
| -- | -- |
| [ImageNative* OH_Image_InitImageNative(napi_env env, napi_value source)](#oh_image_initimagenative) | Parses an [ImageNative](capi-image-imagenative-.md) object at the native layer from a JavaScript native API <b>image </b> object. |
| [int32_t OH_Image_ClipRect(const ImageNative* native, struct OhosImageRect* rect)](#oh_image_cliprect) | Obtains [OhosImageRect](capi-image-ohosimagerect.md) of an [ImageNative](capi-image-imagenative-.md) at the native layer. |
| [int32_t OH_Image_Size(const ImageNative* native, struct OhosImageSize* size)](#oh_image_size) | Obtains {@link OhosImageSize} of an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| [int32_t OH_Image_Format(const ImageNative* native, int32_t* format)](#oh_image_format) | Obtains the image format of an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| [int32_t OH_Image_GetComponent(const ImageNative* native, int32_t componentType, struct OhosImageComponent* componentNative)](#oh_image_getcomponent) | Obtains [OhosImageComponent](capi-image-ohosimagecomponent.md) of an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| [int32_t OH_Image_Release(ImageNative* native)](#oh_image_release) | Releases an [ImageNative](capi-image-imagenative-.md) object at the native layer. Note: This API is not used to release a JavaScript native API <b>Image</b> object. It is used to release the object [ImageNative](capi-image-imagenative-.md) at the native layer parsed by calling [OH_Image_InitImageNative](capi-image-mdk-h.md#oh_image_initimagenative). |

## Enum type description

### anonymous0

```c
enum anonymous0
```

**Description**

Enumerates the image formats.

**Since**: 10

| Enum item | Description |
| -- | -- |
| OHOS_IMAGE_FORMAT_YCBCR_422_SP = 1000 | YCbCr422 semi-planar format. |
| OHOS_IMAGE_FORMAT_JPEG = 2000 | JPEG encoding format. |

### anonymous1

```c
enum anonymous1
```

**Description**

Enumerates the image components.

**Since**: 10

| Enum item | Description |
| -- | -- |
| OHOS_IMAGE_COMPONENT_FORMAT_YUV_Y = 1 | Luminance component. |
| OHOS_IMAGE_COMPONENT_FORMAT_YUV_U = 2 | Chrominance component - blue projection. |
| OHOS_IMAGE_COMPONENT_FORMAT_YUV_V = 3 | Chrominance component - red projection. |
| OHOS_IMAGE_COMPONENT_FORMAT_JPEG = 4 | JPEG format. |


## Function description

### OH_Image_InitImageNative()

```c
ImageNative* OH_Image_InitImageNative(napi_env env, napi_value source)
```

**Description**

Parses an [ImageNative](capi-image-imagenative-.md) object at the native layer from a JavaScript native API <b>image </b> object.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the pointer to the Java Native Interface (JNI) environment. |
| napi_value source | Indicates a JavaScript native API <b>image </b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ImageNative*](capi-image-imagenative-.md) | Returns an [ImageNative](capi-image-imagenative-.md) pointer object if the operation is successful  returns a null pointer otherwise. |

**Reference**:

ImageNative, OH_Image_Release


### OH_Image_ClipRect()

```c
int32_t OH_Image_ClipRect(const ImageNative* native, struct OhosImageRect* rect)
```

**Description**

Obtains [OhosImageRect](capi-image-ohosimagerect.md) of an [ImageNative](capi-image-imagenative-.md) at the native layer.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageNative](capi-image-imagenative-.md)* native | Indicates the pointer to an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| [struct OhosImageRect](capi-image-ohosimagerect.md)* rect | Indicates the pointer to the [OhosImageRect](capi-image-ohosimagerect.md) object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link IRNdkErrCode} IMAGE_RESULT_SUCCESS - if the operation is successful.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_BAD_PARAMETER - if bad parameter. |

**Reference**:

ImageNative, OhosImageRect


### OH_Image_Size()

```c
int32_t OH_Image_Size(const ImageNative* native, struct OhosImageSize* size)
```

**Description**

Obtains {@link OhosImageSize} of an [ImageNative](capi-image-imagenative-.md) object at the native layer.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageNative](capi-image-imagenative-.md)* native | Indicates the pointer to an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| struct OhosImageSize* size | Indicates the pointer to the {@link OhosImageSize} object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link IRNdkErrCode} IMAGE_RESULT_SUCCESS - if the operation is successful.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_BAD_PARAMETER - if bad parameter. |

**Reference**:

ImageNative, OhosImageSize


### OH_Image_Format()

```c
int32_t OH_Image_Format(const ImageNative* native, int32_t* format)
```

**Description**

Obtains the image format of an [ImageNative](capi-image-imagenative-.md) object at the native layer.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageNative](capi-image-imagenative-.md)* native | Indicates the pointer to an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| int32_t* format | Indicates the pointer to the image format obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link IRNdkErrCode} IMAGE_RESULT_SUCCESS - if the operation is successful.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_BAD_PARAMETER - if bad parameter. |

**Reference**:

[ImageNative](capi-image-imagenative-.md)


### OH_Image_GetComponent()

```c
int32_t OH_Image_GetComponent(const ImageNative* native, int32_t componentType, struct OhosImageComponent* componentNative)
```

**Description**

Obtains [OhosImageComponent](capi-image-ohosimagecomponent.md) of an [ImageNative](capi-image-imagenative-.md) object at the native layer.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageNative](capi-image-imagenative-.md)* native | Indicates the pointer to an [ImageNative](capi-image-imagenative-.md) object at the native layer. |
| int32_t componentType | Indicates the type of the required component. |
| [struct OhosImageComponent](capi-image-ohosimagecomponent.md)* componentNative | Indicates the pointer to the [OhosImageComponent](capi-image-ohosimagecomponent.md) object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link IRNdkErrCode} IMAGE_RESULT_SUCCESS - if the operation is successful.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_BAD_PARAMETER - if bad parameter. |

**Reference**:

ImageNative, OhosImageComponent


### OH_Image_Release()

```c
int32_t OH_Image_Release(ImageNative* native)
```

**Description**

Releases an [ImageNative](capi-image-imagenative-.md) object at the native layer. Note: This API is not used to release a JavaScript native API <b>Image</b> object. It is used to release the object [ImageNative](capi-image-imagenative-.md) at the native layer parsed by calling [OH_Image_InitImageNative](capi-image-mdk-h.md#oh_image_initimagenative).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImageNative](capi-image-imagenative-.md)* native | Indicates the pointer to an [ImageNative](capi-image-imagenative-.md) object at the native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link IRNdkErrCode} IMAGE_RESULT_SUCCESS - if the operation is successful.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.<br>returns {@link IRNdkErrCode} IMAGE_RESULT_BAD_PARAMETER - if bad parameter. |

**Reference**:

ImageNative, OH_Image_InitImageNative



