# image_receiver_native.h

## Overview

The file declares the APIs used to obtain image data from the native layer.

**Library**: libimage_receiver.so

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md) | - | The OH_ImageReceiverNative struct describes the image receiver, which is encapsulated at the native layer. The struct cannot be directly operated. Instead, functions must be called to create and release the struct and operate the fields in the struct. |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md) | - | The struct describes the data type name of the image receiver options. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver)](#oh_imagereceiver_oncallback) | OH_ImageReceiver_OnCallback | Defines the callbacks for the image receiver at the native layer. |
| [typedef void (\*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData)](#oh_imagereceiver_imagearrivecallback) | OH_ImageReceiver_ImageArriveCallback | Defines the callback for the ImageArrive event. |
| [Image_ErrorCode OH_ImageReceiverOptions_Create(OH_ImageReceiverOptions **options)](#oh_imagereceiveroptions_create) | - | Creates an OH_ImageReceiverOptions object at the application layer. |
| [Image_ErrorCode OH_ImageReceiverOptions_GetSize(OH_ImageReceiverOptions* options, Image_Size* size)](#oh_imagereceiveroptions_getsize) | - | Obtains the image size of an OH_ImageReceiverOptions object. |
| [Image_ErrorCode OH_ImageReceiverOptions_SetSize(OH_ImageReceiverOptions* options, Image_Size size)](#oh_imagereceiveroptions_setsize) | - | Sets the image size of an OH_ImageReceiverOptions object. |
| [Image_ErrorCode OH_ImageReceiverOptions_GetCapacity(OH_ImageReceiverOptions* options, int32_t* capacity)](#oh_imagereceiveroptions_getcapacity) | - | Obtains the image cache capacity of an OH_ImageReceiverOptions object. |
| [Image_ErrorCode OH_ImageReceiverOptions_SetCapacity(OH_ImageReceiverOptions* options, int32_t capacity)](#oh_imagereceiveroptions_setcapacity) | - | Sets the image cache capacity of an OH_ImageReceiverOptions object. |
| [Image_ErrorCode OH_ImageReceiverOptions_Release(OH_ImageReceiverOptions* options)](#oh_imagereceiveroptions_release) | - | Releases an OH_ImageReceiverOptions object. |
| [Image_ErrorCode OH_ImageReceiverNative_Create(OH_ImageReceiverOptions* options, OH_ImageReceiverNative** receiver)](#oh_imagereceivernative_create) | - | Creates an OH_ImageReceiverNative object at the application layer. |
| [Image_ErrorCode OH_ImageReceiverNative_GetReceivingSurfaceId(OH_ImageReceiverNative* receiver, uint64_t* surfaceId)](#oh_imagereceivernative_getreceivingsurfaceid) | - | Obtains the surface ID through an OH_ImageReceiverNative object. |
| [Image_ErrorCode OH_ImageReceiverNative_ReadLatestImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)](#oh_imagereceivernative_readlatestimage) | - | Obtains the latest image through an OH_ImageReceiverNative object. |
| [Image_ErrorCode OH_ImageReceiverNative_ReadNextImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)](#oh_imagereceivernative_readnextimage) | - | Obtains the next image through an OH_ImageReceiverNative object. |
| [Image_ErrorCode OH_ImageReceiverNative_On(OH_ImageReceiverNative* receiver, OH_ImageReceiver_OnCallback callback)](#oh_imagereceivernative_on) | - | Registers the [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback. |
| [Image_ErrorCode OH_ImageReceiverNative_Off(OH_ImageReceiverNative* receiver)](#oh_imagereceivernative_off) | - | Unregisters the [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback. |
| [Image_ErrorCode OH_ImageReceiverNative_GetSize(OH_ImageReceiverNative* receiver, Image_Size* size)](#oh_imagereceivernative_getsize) | - | Obtains the size of an **ImageReceiver** using **OH_ImageReceiverNative**. |
| [Image_ErrorCode OH_ImageReceiverNative_GetCapacity(OH_ImageReceiverNative* receiver, int32_t* capacity)](#oh_imagereceivernative_getcapacity) | - | Obtains the capacity of an **OH_ImageReceiverNative**. |
| [Image_ErrorCode OH_ImageReceiverNative_Release(OH_ImageReceiverNative* receiver)](#oh_imagereceivernative_release) | - | Releases an OH_ImageReceiverNative object. |
| [Image_ErrorCode OH_ImageReceiverNative_OnImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback, void *userData)](#oh_imagereceivernative_onimagearrive) | - |  |
| [Image_ErrorCode OH_ImageReceiverNative_OffImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback)](#oh_imagereceivernative_offimagearrive) | - |  |
| [Image_ErrorCode OH_ImageReceiverNative_SetMemoryName(const OH_ImageReceiverNative* receiver, const char *name, uint32_t size)](#oh_imagereceivernative_setmemoryname) | - | Sets the memory name for an OH_ImageReceiverNative object.<br> Only visible ASCII characters are supported. Spaces, newlines, tabs, and other control characters will be filtered out. If the filtered result consists entirely of digits, a prefix "ImageReceiver:" will be automatically prepended. The filtered size must not exceed 256 bytes (including the null terminator). |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver) | Defines the callbacks for the image receiver at the native layer.<br>**Since**: 12 |
| void (*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData) | Defines the callback for the ImageArrive event.<br>**Since**: 20 |

## Function description

### OH_ImageReceiver_OnCallback()

```c
typedef void (*OH_ImageReceiver_OnCallback)(OH_ImageReceiverNative *receiver)
```

**Description**

Defines the callbacks for the image receiver at the native layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

### OH_ImageReceiver_ImageArriveCallback()

```c
typedef void (*OH_ImageReceiver_ImageArriveCallback)(OH_ImageReceiverNative *receiver, void *userData)
```

**Description**

Defines the callback for the ImageArrive event.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 20

### OH_ImageReceiverOptions_Create()

```c
Image_ErrorCode OH_ImageReceiverOptions_Create(OH_ImageReceiverOptions **options)
```

**Description**

Creates an OH_ImageReceiverOptions object at the application layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md) **options | Double pointer to the OH_ImageReceiverOptions object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if alloc failed. |

### OH_ImageReceiverOptions_GetSize()

```c
Image_ErrorCode OH_ImageReceiverOptions_GetSize(OH_ImageReceiverOptions* options, Image_Size* size)
```

**Description**

Obtains the image size of an OH_ImageReceiverOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |
| Image_Size* size | Pointer to the Image_Size object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

### OH_ImageReceiverOptions_SetSize()

```c
Image_ErrorCode OH_ImageReceiverOptions_SetSize(OH_ImageReceiverOptions* options, Image_Size size)
```

**Description**

Sets the image size of an OH_ImageReceiverOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |
| Image_Size size | Image_Size object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

### OH_ImageReceiverOptions_GetCapacity()

```c
Image_ErrorCode OH_ImageReceiverOptions_GetCapacity(OH_ImageReceiverOptions* options, int32_t* capacity)
```

**Description**

Obtains the image cache capacity of an OH_ImageReceiverOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |
| int32_t* capacity | Pointer to the capacity obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

### OH_ImageReceiverOptions_SetCapacity()

```c
Image_ErrorCode OH_ImageReceiverOptions_SetCapacity(OH_ImageReceiverOptions* options, int32_t capacity)
```

**Description**

Sets the image cache capacity of an OH_ImageReceiverOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |
| int32_t capacity | Capacity. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

### OH_ImageReceiverOptions_Release()

```c
Image_ErrorCode OH_ImageReceiverOptions_Release(OH_ImageReceiverOptions* options)
```

**Description**

Releases an OH_ImageReceiverOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

[OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)


### OH_ImageReceiverNative_Create()

```c
Image_ErrorCode OH_ImageReceiverNative_Create(OH_ImageReceiverOptions* options, OH_ImageReceiverNative** receiver)
```

**Description**

Creates an OH_ImageReceiverNative object at the application layer.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverOptions](capi-image-nativemodule-oh-imagereceiveroptions.md)* options | Pointer to an OH_ImageReceiverOptions object. |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)** receiver | Double pointer to the OH_ImageReceiverNative object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if alloc failed. |

### OH_ImageReceiverNative_GetReceivingSurfaceId()

```c
Image_ErrorCode OH_ImageReceiverNative_GetReceivingSurfaceId(OH_ImageReceiverNative* receiver, uint64_t* surfaceId)
```

**Description**

Obtains the surface ID through an OH_ImageReceiverNative object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| uint64_t* surfaceId | Pointer to the surface ID obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error. |

**Reference**:

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_ReadLatestImage()

```c
Image_ErrorCode OH_ImageReceiverNative_ReadLatestImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)
```

**Description**

Obtains the latest image through an OH_ImageReceiverNative object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| OH_ImageNative** image | Double pointer to the image obtained, which is an OH_ImageNative object at the application layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if alloc failed. |

**Reference**:

OH_ImageReceiverNative, OH_ImageNative


### OH_ImageReceiverNative_ReadNextImage()

```c
Image_ErrorCode OH_ImageReceiverNative_ReadNextImage(OH_ImageReceiverNative* receiver, OH_ImageNative** image)
```

**Description**

Obtains the next image through an OH_ImageReceiverNative object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| OH_ImageNative** image | Double pointer to the image obtained, which is an OH_ImageNative object at the application layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if alloc failed. |

**Reference**:

OH_ImageReceiverNative, OH_ImageNative


### OH_ImageReceiverNative_On()

```c
Image_ErrorCode OH_ImageReceiverNative_On(OH_ImageReceiverNative* receiver, OH_ImageReceiver_OnCallback callback)
```

**Description**

Registers the [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback | Callback to register. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

OH_ImageReceiverNative, OH_ImageReceiver_OnCallback


### OH_ImageReceiverNative_Off()

```c
Image_ErrorCode OH_ImageReceiverNative_Off(OH_ImageReceiverNative* receiver)
```

**Description**

Unregisters the [OH_ImageReceiver_OnCallback](capi-image-receiver-native-h.md#oh_imagereceiver_oncallback) callback.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

OH_ImageReceiverNative, OH_ImageReceiverNative_On


### OH_ImageReceiverNative_GetSize()

```c
Image_ErrorCode OH_ImageReceiverNative_GetSize(OH_ImageReceiverNative* receiver, Image_Size* size)
```

**Description**

Obtains the size of an **ImageReceiver** using **OH_ImageReceiverNative**.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| Image_Size* size | Pointer to the Image_Size object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

OH_ImageReceiverNative, Image_Size


### OH_ImageReceiverNative_GetCapacity()

```c
Image_ErrorCode OH_ImageReceiverNative_GetCapacity(OH_ImageReceiverNative* receiver, int32_t* capacity)
```

**Description**

Obtains the capacity of an **OH_ImageReceiverNative**.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |
| int32_t* capacity | Pointer to the capacity obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_Release()

```c
Image_ErrorCode OH_ImageReceiverNative_Release(OH_ImageReceiverNative* receiver)
```

**Description**

Releases an OH_ImageReceiverNative object.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if bad parameter. |

**Reference**:

[OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)


### OH_ImageReceiverNative_OnImageArrive()

```c
Image_ErrorCode OH_ImageReceiverNative_OnImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback, void *userData)
```

**Description**

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object that processes the callback. |
| [OH_ImageReceiver_ImageArriveCallback](capi-image-receiver-native-h.md#oh_imagereceiver_imagearrivecallback) callback | Callback to register. |
| void *userData | Pointer to user data. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS is returned if the operation is successful.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_RECEIVER_INVALID_PARAMETER is returned if receiver or callback is null. |

### OH_ImageReceiverNative_OffImageArrive()

```c
Image_ErrorCode OH_ImageReceiverNative_OffImageArrive(OH_ImageReceiverNative* receiver, OH_ImageReceiver_ImageArriveCallback callback)
```

**Description**

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | Pointer to an OH_ImageReceiverNative object that processes the callback. |
| [OH_ImageReceiver_ImageArriveCallback](capi-image-receiver-native-h.md#oh_imagereceiver_imagearrivecallback) callback | Callback to unregister. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - Operation succeeded.      <br>[Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_RECEIVER_INVALID_PARAMETER - <b>receiver</b> is empty or <b>callback</b> is not registered. |

### OH_ImageReceiverNative_SetMemoryName()

```c
Image_ErrorCode OH_ImageReceiverNative_SetMemoryName(const OH_ImageReceiverNative* receiver, const char *name, uint32_t size)
```

**Description**

Sets the memory name for an OH_ImageReceiverNative object.<br> Only visible ASCII characters are supported. Spaces, newlines, tabs, and other control characters will be filtered out. If the filtered result consists entirely of digits, a prefix "ImageReceiver:" will be automatically prepended. The filtered size must not exceed 256 bytes (including the null terminator).

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ImageReceiverNative](capi-image-nativemodule-oh-imagereceivernative.md)* receiver | [in] Pointer to an OH_ImageReceiverNative object. It must not be NULL. |
| const char *name | [in] Pointer to the memory name string to set. It must not be NULL. The string must be null-terminated. |
| uint32_t size | [in] The size of the name string in bytes, including the null terminator. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>           <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the operation is successful.</li>          <li>[IMAGE_RECEIVER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if receiver or name is NULL, or size is 0,              or name contains no visible characters after filtering, or filtered size exceeds 256 bytes.</li>          </ul> |


