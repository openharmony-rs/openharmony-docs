# image_packer_mdk.h

## Overview

Declares APIs for encoding image into data or file.<br> The packing image data module used to pack pixel data into a target.<br> The following steps are recommended for packing process: Create a image packer object by calling OH_ImagePacker_Create function. And then covert the image packer object to ImagePacker_Native by OH_ImagePacker_InitNative. Next using OH_ImagePacker_PackToData or OH_ImagePacker_PackToFile to pack source to target area with requird packing options. Finally, release the ImagePacker_Native by OH_ImagePacker_Release.

**Library**: libimage_packer_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ImagePacker_Opts_](capi-image-imagepacker-opts-.md) | ImagePacker_Opts | Defines the image packing options. |
| [ImagePacker_Native_](capi-image-imagepacker-native-.md) | ImagePacker_Native | Defines an image packer object at the native layer for the image packer interface. |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_ImagePacker_Create(napi_env env, napi_value *res)](#oh_imagepacker_create) | Creates an <b>ImagePacker</b> object at the JavaScript native layer. |
| [ImagePacker_Native* OH_ImagePacker_InitNative(napi_env env, napi_value packer)](#oh_imagepacker_initnative) | Parses an [ImagePacker_Native](capi-image-imagepacker-native-.md) object at the native layer from a JavaScript native API <b>ImagePacker</b> object. |
| [int32_t OH_ImagePacker_PackToData(ImagePacker_Native* native, napi_value source, ImagePacker_Opts* opts, uint8_t* outData, size_t* size)](#oh_imagepacker_packtodata) | Encoding an <b>ImageSource</b> or a <b>PixelMap</b> into the data with required format |
| [int32_t OH_ImagePacker_PackToFile(ImagePacker_Native* native, napi_value source, ImagePacker_Opts* opts, int fd)](#oh_imagepacker_packtofile) | Encoding an <b>ImageSource</b> or a <b>PixelMap</b> into the a file with fd with required format |
| [int32_t OH_ImagePacker_Release(ImagePacker_Native* native)](#oh_imagepacker_release) | Releases an [ImagePacker_Native](capi-image-imagepacker-native-.md) object at the native layer. Note: This API is not used to release a JavaScript native API <b>ImagePacker</b> object. It is used to release the object [ImagePacker_Native](capi-image-imagepacker-native-.md) at the native layer parsed by calling [OH_ImagePacker_InitNative](capi-image-packer-mdk-h.md#oh_imagepacker_initnative). |

## Function description

### OH_ImagePacker_Create()

```c
int32_t OH_ImagePacker_Create(napi_env env, napi_value *res)
```

**Description**

Creates an <b>ImagePacker</b> object at the JavaScript native layer.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the JavaScript Native Interface (JNI) environment. |
| napi_value *res | Indicates a pointer to the <b>ImagePacker</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

### OH_ImagePacker_InitNative()

```c
ImagePacker_Native* OH_ImagePacker_InitNative(napi_env env, napi_value packer)
```

**Description**

Parses an [ImagePacker_Native](capi-image-imagepacker-native-.md) object at the native layer from a JavaScript native API <b>ImagePacker</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the pointer to the JavaScript Native Interface (JNI) environment. |
| napi_value packer | Indicates a JavaScript native API <b>ImagePacker</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ImagePacker_Native*](capi-image-imagepacker-native-.md) | Returns an [ImagePacker_Native](capi-image-imagepacker-native-.md) pointer object if the operation is successful  returns a null pointer otherwise. |

**Reference**:

[OH_ImagePacker_Release](capi-image-packer-mdk-h.md#oh_imagepacker_release)


### OH_ImagePacker_PackToData()

```c
int32_t OH_ImagePacker_PackToData(ImagePacker_Native* native, napi_value source, ImagePacker_Opts* opts, uint8_t* outData, size_t* size)
```

**Description**

Encoding an <b>ImageSource</b> or a <b>PixelMap</b> into the data with required format

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImagePacker_Native](capi-image-imagepacker-native-.md)* native | Indicates the pointer to an {@link ImagePacker} object at the native layer. |
| napi_value source | Indicates an encoding source, a JS pixel map object or a JS image source object . |
| [ImagePacker_Opts](capi-image-imagepacker-opts-.md)* opts | Indicates the encoding [ImagePacker_Opts](capi-image-imagepacker-opts-.md) . |
| uint8_t* outData | Indicates the pointer to the encoded data. |
| size_t* size | Indicates the pointer to the [OhosImageComponent](capi-image-ohosimagecomponent.md) object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_DATA_ABNORMAL - if output target abnormal   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_MISMATCHED_FORMAT - if format mismatched   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_MALLOC_ABNORMAL - if malloc internal buffer error   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_DECODE_ABNORMAL - if init codec internal error   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_ENCODE_FAILED - if encoder occur error during encoding |

**Reference**:

[OH_ImagePacker_PackToFile](capi-image-packer-mdk-h.md#oh_imagepacker_packtofile)


### OH_ImagePacker_PackToFile()

```c
int32_t OH_ImagePacker_PackToFile(ImagePacker_Native* native, napi_value source, ImagePacker_Opts* opts, int fd)
```

**Description**

Encoding an <b>ImageSource</b> or a <b>PixelMap</b> into the a file with fd with required format

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImagePacker_Native](capi-image-imagepacker-native-.md)* native | Indicates the pointer to an {@link ImagePacker} object at the native layer. |
| napi_value source | Indicates an encoding source, a JS pixel map object or a JS image source object . |
| [ImagePacker_Opts](capi-image-imagepacker-opts-.md)* opts | Indicates the encoding [ImagePacker_Opts](capi-image-imagepacker-opts-.md) . |
| int fd | Indicates the a writable file descriptor. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_DATA_ABNORMAL - if output target abnormal   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_MISMATCHED_FORMAT - if format mismatched   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_MALLOC_ABNORMAL - if malloc internal buffer error   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_DECODE_ABNORMAL - if init codec internal error   returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) ERR_IMAGE_ENCODE_FAILED - if encoder occur error during encoding |

**Reference**:

[OH_ImagePacker_PackToData](capi-image-packer-mdk-h.md#oh_imagepacker_packtodata)


### OH_ImagePacker_Release()

```c
int32_t OH_ImagePacker_Release(ImagePacker_Native* native)
```

**Description**

Releases an [ImagePacker_Native](capi-image-imagepacker-native-.md) object at the native layer. Note: This API is not used to release a JavaScript native API <b>ImagePacker</b> object. It is used to release the object [ImagePacker_Native](capi-image-imagepacker-native-.md) at the native layer parsed by calling [OH_ImagePacker_InitNative](capi-image-packer-mdk-h.md#oh_imagepacker_initnative).

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImagePacker_Native](capi-image-imagepacker-native-.md)* native | Indicates the pointer to an [ImagePacker_Native](capi-image-imagepacker-native-.md) object at the native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful. |

**Reference**:

[OH_ImagePacker_InitNative](capi-image-packer-mdk-h.md#oh_imagepacker_initnative)



