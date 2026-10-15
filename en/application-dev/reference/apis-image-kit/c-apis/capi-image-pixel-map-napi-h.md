# image_pixel_map_napi.h

## Overview

Declares the APIs that can lock, access, and unlock a pixel map. Need link <b>libpixelmap_ndk.z.so</b>

**Library**: libpixelmap_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) | Defines the pixel map information. |

### Enum

| Name | Description |
| -- | -- |
| [anonymous0](#anonymous0) | Enumerates the error codes returned by the functions.(Deprecated in API10) |
| [anonymous1](#anonymous1) | Enumerates the pixel formats.(Deprecated in API10) |
| [anonymous2](#anonymous2) | Enumerates the pixel map scale modes. |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_GetImageInfo(napi_env env, napi_value value, OhosPixelMapInfo *info)](#oh_getimageinfo) | Obtains the information about a <b>PixelMap</b> object and stores the information to the [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) struct.(Deprecated in API10) |
| [int32_t OH_AccessPixels(napi_env env, napi_value value, void** addrPtr)](#oh_accesspixels) | Obtains the memory address of a <b>PixelMap</b> object and locks the memory.<br> After the function is executed successfully, <b>*addrPtr</b> is the memory address to be accessed. After the access operation is complete, you must use [OH_UnAccessPixels](capi-image-pixel-map-napi-h.md#oh_unaccesspixels) to unlock the memory. Otherwise, the resources in the memory cannot be released. After the memory is unlocked, its address cannot be accessed or operated.(Deprecated in API10) |
| [int32_t OH_UnAccessPixels(napi_env env, napi_value value)](#oh_unaccesspixels) | Unlocks the memory of a <b>PixelMap</b> object. This function is used with [OH_AccessPixels](capi-image-pixel-map-napi-h.md#oh_accesspixels) in pairs.(Deprecated in API10) |

## Enum type description

### anonymous0

```c
enum anonymous0
```

**Description**

Enumerates the error codes returned by the functions.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Deprecated**: 10

| Enum item | Description |
| -- | -- |
| OHOS_IMAGE_RESULT_SUCCESS = 0 | Operation success. |
| OHOS_IMAGE_RESULT_BAD_PARAMETER = -1 | Invalid value. |

### anonymous1

```c
enum anonymous1
```

**Description**

Enumerates the pixel formats.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Deprecated**: 10

| Enum item | Description |
| -- | -- |
| OHOS_PIXEL_MAP_FORMAT_NONE = 0 | Unknown format. |
| OHOS_PIXEL_MAP_FORMAT_RGBA_8888 = 3 | 32-bit RGBA, with 8 bits each for R (red), G (green), B (blue), and A (alpha). The data is stored from the most significant bit to the least significant bit. |
| OHOS_PIXEL_MAP_FORMAT_RGB_565 = 2 | 16-bit RGB, with 5, 6, and 5 bits for R, G, and B, respectively. The data is stored from the most significant bit to the least significant bit. |

### anonymous2

```c
enum anonymous2
```

**Description**

Enumerates the pixel map scale modes.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| OHOS_PIXEL_MAP_SCALE_MODE_FIT_TARGET_SIZE = 0 | Adaptation to the target image size. |
| OHOS_PIXEL_MAP_SCALE_MODE_CENTER_CROP = 1 | Cropping the center portion of an image to the target size. |


## Function description

### OH_GetImageInfo()

```c
int32_t OH_GetImageInfo(napi_env env, napi_value value, OhosPixelMapInfo *info)
```

**Description**

Obtains the information about a <b>PixelMap</b> object and stores the information to the [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>PixelMap</b> object at the application layer. |
| [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) *info | Indicates the pointer to the object that stores the information obtained. For details, see [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if the information is obtained and stored successfully; returns an error code otherwise. |

**Reference**:

[OhosPixelMapInfo](capi-image-ohospixelmapinfo.md)


### OH_AccessPixels()

```c
int32_t OH_AccessPixels(napi_env env, napi_value value, void** addrPtr)
```

**Description**

Obtains the memory address of a <b>PixelMap</b> object and locks the memory.<br> After the function is executed successfully, <b>*addrPtr</b> is the memory address to be accessed. After the access operation is complete, you must use [OH_UnAccessPixels](capi-image-pixel-map-napi-h.md#oh_unaccesspixels) to unlock the memory. Otherwise, the resources in the memory cannot be released. After the memory is unlocked, its address cannot be accessed or operated.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>PixelMap</b> object at the application layer. |
| void** addrPtr | Indicates the double pointer to the memory address. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [OHOS_IMAGE_RESULT_SUCCESS](capi-image-pixel-map-napi-h.md#anonymous0) if the operation is successful; returns an error code otherwise. |

**Reference**:

UnAccessPixels


### OH_UnAccessPixels()

```c
int32_t OH_UnAccessPixels(napi_env env, napi_value value)
```

**Description**

Unlocks the memory of a <b>PixelMap</b> object. This function is used with [OH_AccessPixels](capi-image-pixel-map-napi-h.md#oh_accesspixels) in pairs.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 8

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value value | Indicates the <b>PixelMap</b> object at the application layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [OHOS_IMAGE_RESULT_SUCCESS](capi-image-pixel-map-napi-h.md#anonymous0) if the operation is successful; returns an error code otherwise. |

**Reference**:

AccessPixels



