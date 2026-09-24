# image_receiver_mdk.h

## Overview

Declares the APIs for obtaining image data from the native layer.

**Library**: libimage_receiver_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OhosImageReceiverInfo](capi-image-ohosimagereceiverinfo.md) | - | Defines the information about an image receiver. |
| [ImageReceiverNative_](capi-image-imagereceivernative-.md) | - | Defines an <b>ImageReceiver</b> object at the native layer. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_Image_Receiver_On_Callback)(void)](#oh_image_receiver_on_callback) | OH_Image_Receiver_On_Callback | Defines the callbacks for images at the native layer. |
| [int32_t OH_Image_Receiver_CreateImageReceiver(napi_env env, struct OhosImageReceiverInfo info, napi_value* res)](#oh_image_receiver_createimagereceiver) | - | Creates an <b>ImageReceiver</b> object at the application layer. |
| [ImageReceiverNative* OH_Image_Receiver_InitImageReceiverNative(napi_env env, napi_value source)](#oh_image_receiver_initimagereceivernative) | - | Initializes an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer through an <b>ImageReceiver</b> object at the application layer. |
| [int32_t OH_Image_Receiver_GetReceivingSurfaceId(const ImageReceiverNative* native, char* id, size_t len)](#oh_image_receiver_getreceivingsurfaceid) | - | Obtains the receiver ID through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_ReadLatestImage(const ImageReceiverNative* native, napi_value* image)](#oh_image_receiver_readlatestimage) | - | Obtains the latest image through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_ReadNextImage(const ImageReceiverNative* native, napi_value* image)](#oh_image_receiver_readnextimage) | - | Obtains the next image through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_On(const ImageReceiverNative* native, OH_Image_Receiver_On_Callback callback)](#oh_image_receiver_on) | - | Registers an [OH_Image_Receiver_On_Callback](capi-image-receiver-mdk-h.md#oh_image_receiver_on_callback) callback event.<br> This callback event is triggered whenever a new image is received. |
| [int32_t OH_Image_Receiver_GetSize(const ImageReceiverNative* native, struct OhosImageSize* size)](#oh_image_receiver_getsize) | - | Obtains the size of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_GetCapacity(const ImageReceiverNative* native, int32_t* capacity)](#oh_image_receiver_getcapacity) | - | Obtains the capacity of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_GetFormat(const ImageReceiverNative* native, int32_t* format)](#oh_image_receiver_getformat) | - | Obtains the format of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object. |
| [int32_t OH_Image_Receiver_Release(ImageReceiverNative* native)](#oh_image_receiver_release) | - | Releases an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer.<br> This API is not used to release an <b>ImageReceiver</b> object at the application layer. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_Image_Receiver_On_Callback)(void) | Defines the callbacks for images at the native layer.<br>**Since**: 10 |

## Function description

### OH_Image_Receiver_On_Callback()

```c
typedef void (*OH_Image_Receiver_On_Callback)(void)
```

**Description**

Defines the callbacks for images at the native layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

### OH_Image_Receiver_CreateImageReceiver()

```c
int32_t OH_Image_Receiver_CreateImageReceiver(napi_env env, struct OhosImageReceiverInfo info, napi_value* res)
```

**Description**

Creates an <b>ImageReceiver</b> object at the application layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| [struct OhosImageReceiverInfo](capi-image-ohosimagereceiverinfo.md) info | Indicates the options for setting the <b>ImageReceiver</b> object. |
| napi_value* res | Indicates the pointer to the <b>ImageReceiver</b> object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_SURFACE_FAILED - if create surface failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GRALLOC_BUFFER_FAILED - if surface gralloc buffer failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_SURFACE_FAILED - if get sufrace failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MEDIA_RTSP_SURFACE_UNSUPPORT - if media rtsp surface not support.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MEDIA_DATA_UNSUPPORT - if media type unsupported. |

**Reference**:

[OhosImageReceiverInfo](capi-image-ohosimagereceiverinfo.md)


### OH_Image_Receiver_InitImageReceiverNative()

```c
ImageReceiverNative* OH_Image_Receiver_InitImageReceiverNative(napi_env env, napi_value source)
```

**Description**

Initializes an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer through an <b>ImageReceiver</b> object at the application layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value source | Indicates an <b>ImageReceiver</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ImageReceiverNative*](capi-image-imagereceivernative-.md) | Returns the pointer to the [ImageReceiverNative](capi-image-imagereceivernative-.md) object obtained if the operation is successful;  returns a null pointer otherwise. |

**Reference**:

ImageReceiverNative, OH_Image_Receiver_Release


### OH_Image_Receiver_GetReceivingSurfaceId()

```c
int32_t OH_Image_Receiver_GetReceivingSurfaceId(const ImageReceiverNative* native, char* id, size_t len)
```

**Description**

Obtains the receiver ID through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| char* id | Indicates the pointer to the buffer that stores the ID string obtained. |
| size_t len | Indicates the size of the buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_SURFACE_FAILED - if get sufrace failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MEDIA_DATA_UNSUPPORT - if media type unsupported. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)


### OH_Image_Receiver_ReadLatestImage()

```c
int32_t OH_Image_Receiver_ReadLatestImage(const ImageReceiverNative* native, napi_value* image)
```

**Description**

Obtains the latest image through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| napi_value* image | Indicates the pointer to an <b>Image</b> object at the application layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_SURFACE_FAILED - if create surface failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GRALLOC_BUFFER_FAILED - if surface gralloc buffer failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_SURFACE_FAILED - if get sufrace failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MEDIA_RTSP_SURFACE_UNSUPPORT - if media rtsp surface not support.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_REQUEST_BUFFER_FAILED - if request Buffer failed. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)


### OH_Image_Receiver_ReadNextImage()

```c
int32_t OH_Image_Receiver_ReadNextImage(const ImageReceiverNative* native, napi_value* image)
```

**Description**

Obtains the next image through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| napi_value* image | Indicates the pointer to an <b>Image</b> object at the application layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GET_PARAMETER_FAILED - if Failed to obtain parameters for surface.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_SURFACE_FAILED - if create surface failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_GRALLOC_BUFFER_FAILED - if surface gralloc buffer failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_SURFACE_FAILED - if get sufrace failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MEDIA_RTSP_SURFACE_UNSUPPORT - if media rtsp surface not support.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SURFACE_REQUEST_BUFFER_FAILED - if request Buffer failed. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)


### OH_Image_Receiver_On()

```c
int32_t OH_Image_Receiver_On(const ImageReceiverNative* native, OH_Image_Receiver_On_Callback callback)
```

**Description**

Registers an [OH_Image_Receiver_On_Callback](capi-image-receiver-mdk-h.md#oh_image_receiver_on_callback) callback event.<br> This callback event is triggered whenever a new image is received.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| [OH_Image_Receiver_On_Callback](capi-image-receiver-mdk-h.md#oh_image_receiver_on_callback) callback | Indicates the [OH_Image_Receiver_On_Callback](capi-image-receiver-mdk-h.md#oh_image_receiver_on_callback) callback event to register. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_SURFACE_FAILED - if get sufrace failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_REGISTER_LISTENER_FAILED - if Failed to register listener.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_REGISTER_BUFFER_FAILED - if Failed to register buffer. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)


### OH_Image_Receiver_GetSize()

```c
int32_t OH_Image_Receiver_GetSize(const ImageReceiverNative* native, struct OhosImageSize* size)
```

**Description**

Obtains the size of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| struct OhosImageSize* size | Indicates the pointer to the [OhosImageSize](capi-image-ohosimagesize.md) object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported. |

**Reference**:

ImageReceiverNative, OH_Image_Receiver_On_Callback


### OH_Image_Receiver_GetCapacity()

```c
int32_t OH_Image_Receiver_GetCapacity(const ImageReceiverNative* native, int32_t* capacity)
```

**Description**

Obtains the capacity of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| int32_t* capacity | Indicates the pointer to the capacity obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported. |

**Reference**:

ImageReceiverNative, OhosImageSize


### OH_Image_Receiver_GetFormat()

```c
int32_t OH_Image_Receiver_GetFormat(const ImageReceiverNative* native, int32_t* format)
```

**Description**

Obtains the format of the image receiver through an [ImageReceiverNative](capi-image-imagereceivernative-.md) object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |
| int32_t* format | Indicates the pointer to the format obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image type unsupported. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)


### OH_Image_Receiver_Release()

```c
int32_t OH_Image_Receiver_Release(ImageReceiverNative* native)
```

**Description**

Releases an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer.<br> This API is not used to release an <b>ImageReceiver</b> object at the application layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImageReceiverNative](capi-image-imagereceivernative-.md)* native | Indicates the pointer to an [ImageReceiverNative](capi-image-imagereceivernative-.md) object at the native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[ImageReceiverNative](capi-image-imagereceivernative-.md)



