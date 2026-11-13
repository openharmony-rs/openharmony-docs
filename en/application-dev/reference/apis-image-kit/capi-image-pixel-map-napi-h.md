# image_pixel_map_napi.h
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yaozhupeng-->
<!--Designer: @yaozhupeng-->
<!--Tester: @yhl0101-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=ba1b6704bf7552d9b6a8a06ca0cf38b43a773032 translatedAt=2026-11-06T02:10:37.145Z pushedAt=2026-11-12T07:50:18.611Z nl=1 -->

## Overview

The file declares the APIs used to lock, access, and unlock a pixel map.

**Library**: libpixelmap_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.Core

**File to include**: <multimedia/image_framework/image_pixel_map_napi.h>

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) | - | Describes the information about a pixel map.|

### Enums

| Name| Description|
| -- | -- |
| [Error Codes Returned by Functions](#error-codes-returned-by-functions)| Enumerates the error codes returned by the functions.|
| [Pixel Formats](#pixel-formats)| Enumerates the pixel formats.|
| [anonymous enum](#pixelmap-scale-modes)| Enumerates the pixel map scale modes.|

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_GetImageInfo(napi_env env, napi_value value, OhosPixelMapInfo *info)](#oh_getimageinfo) | Obtains the information of a pixel map and records it in an [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) struct. |
| [int32_t OH_AccessPixels(napi_env env, napi_value value, void** addrPtr)](#oh_accesspixels) | Obtains the memory address of a pixel map object and locks the memory.<br>**\*addrPtr** is the memory address obtained. After finishing the access, you must use [OH_UnAccessPixels](#oh_unaccesspixels) to unlock the memory. Otherwise, resources cannot be released. After the unlocking, the memory cannot be accessed or operated.|
| [int32_t OH_UnAccessPixels(napi_env env, napi_value value)](#oh_unaccesspixels) | Unlocks the memory of a pixel map object. This function is used with [OH_AccessPixels](#oh_accesspixels) in pairs.|

## Enum Description

### Error Codes Returned by Functions

```c
enum anonymous enum
```

**Description**

Enumerates the error codes returned by the functions.

**Since**: 8

**Deprecated from**: 10

| Enum Item| Description|
| -- | -- |
| OHOS_IMAGE_RESULT_SUCCESS = 0 | Operation success.|
| OHOS_IMAGE_RESULT_BAD_PARAMETER = -1 | Invalid value.|

### Pixel Formats

```c
enum anonymous enum
```

**Description**

Enumerates the pixel formats.

**Since**: 8

**Deprecated from**: 10

| Enum Item| Description|
| -- | -- |
| OHOS_PIXEL_MAP_FORMAT_NONE = 0 | Unknown format.|
| OHOS_PIXEL_MAP_FORMAT_RGBA_8888 = 3 | RGBA_8888 format.|
| OHOS_PIXEL_MAP_FORMAT_RGB_565 = 2 | RGB_565 format.|

### PixelMap Scale Modes

```c
enum anonymous enum
```

**Description**

Enumerates the pixel map scale modes.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OHOS_PIXEL_MAP_SCALE_MODE_FIT_TARGET_SIZE = 0 | Scaling mode that fits the target image size.
| OHOS_PIXEL_MAP_SCALE_MODE_CENTER_CROP = 1 | Scaling mode from the center.|


## Function Description

### OH_GetImageInfo()

```c
int32_t OH_GetImageInfo(napi_env env, napi_value value, OhosPixelMapInfo *info)
```

**Description**

Obtains the information of a pixel map and records the information in an [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) struct.

**Since**: 8

**Deprecated from**: 10


**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the NAPI environment.|
| napi_value value | Pixel map object at the application layer.|
| [OhosPixelMapInfo](capi-image-ohospixelmapinfo.md) *info | Pointer to the object that stores the information obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | One of the following [error codes](#error-codes-returned-by-functions):<br>**OHOS_IMAGE_RESULT_SUCCESS**: The operation is successful.<br>**OHOS_IMAGE_RESULT_BAD_PARAMETER**: The operation fails.|

### OH_AccessPixels()

```c
int32_t OH_AccessPixels(napi_env env, napi_value value, void** addrPtr)
```

**Description**

Obtains the memory address of a pixel map object and locks the memory.

**\*addrPtr** is the memory address obtained. After finishing the access, you must use [OH_UnAccessPixels](#oh_unaccesspixels) to unlock the memory. Otherwise, resources cannot be released. After the unlocking, the memory cannot be accessed or operated.

**Since**: 8

**Deprecated from**: 10


**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the NAPI environment.|
| napi_value value | Pixel map object at the application layer.|
| void** addrPtr | Double pointer to the memory address.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | One of the following [error codes](#error-codes-returned-by-functions):<br>**OHOS_IMAGE_RESULT_SUCCESS**: The operation is successful.<br>**OHOS_IMAGE_RESULT_BAD_PARAMETER**: The operation fails.|

### OH_UnAccessPixels()

```c
int32_t OH_UnAccessPixels(napi_env env, napi_value value)
```

**Description**

Unlocks the memory of a pixel map object. This function is used with [OH_AccessPixels](#oh_accesspixels) in pairs.

**Since**: 8

**Deprecated from**: 10


**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Pointer to the NAPI environment.|
| napi_value value | Pixel map object at the application layer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | One of the following [error codes](#error-codes-returned-by-functions):<br>**OHOS_IMAGE_RESULT_SUCCESS**: The operation is successful.<br>**OHOS_IMAGE_RESULT_BAD_PARAMETER**: The operation fails.|



