# native_buffer.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Flix-fangyang; @BruceXu; @ding-panyun-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the functions for obtaining and using **NativeBuffer**.

**File to include**: <native_buffer/native_buffer.h>

**Library**: libnative_buffer.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) | OH_NativeBuffer_Config | Describes the **OH_NativeBuffer** property configuration, which is used when you apply for a new **OH_NativeBuffer** instance or query the properties of an existing instance.|
| [OH_NativeBuffer_Plane](capi-oh-nativebuffer-oh-nativebuffer-plane.md) | OH_NativeBuffer_Plane | Describes the plane information of an image.|
| [OH_NativeBuffer_Planes](capi-oh-nativebuffer-oh-nativebuffer-planes.md) | OH_NativeBuffer_Planes | Describes the plane information of images in an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) | OH_NativeBuffer | Provides the declaration of an **OH_NativeBuffer** struct.|
| [OHIPCParcel](../apis-ipc-kit/capi-ohipcparcel-ohipcparcel.md) | OHIPCParcel | Provides the **OHIPCParcel** struct declaration for inter-process communication.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeBuffer_Usage](#oh_nativebuffer_usage) | OH_NativeBuffer_Usage | Defines an enum for the **OH_NativeBuffer** usages.|
| [OH_NativeBuffer_ColorGamut](#oh_nativebuffer_colorgamut) | OH_NativeBuffer_ColorGamut | Defines an enum for the color gamuts of an **OH_NativeBuffer** instance.|

### Functions

| Name| Description|
| -- | -- |
| [OH_NativeBuffer* OH_NativeBuffer_Alloc(const OH_NativeBuffer_Config* config)](#oh_nativebuffer_alloc) | Creates an **OH_NativeBuffer** instance based on an **OH_NativeBuffer_Config** struct. A new **OH_NativeBuffer** instance is created each time this function is called.<br>This API must be used in pair with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, memory leak occurs.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_Reference(OH_NativeBuffer *buffer)](#oh_nativebuffer_reference) | Increases the reference count of an **OH_NativeBuffer** instance by 1.<br>This API must be used in pair with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, memory leak occurs.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_Unreference(OH_NativeBuffer *buffer)](#oh_nativebuffer_unreference) | Decreases the reference count of an **OH_NativeBuffer** instance by 1 and, when the reference count reaches 0, destroys the instance.<br>This function is not thread-safe.|
| [void OH_NativeBuffer_GetConfig(OH_NativeBuffer *buffer, OH_NativeBuffer_Config* config)](#oh_nativebuffer_getconfig) | Obtains the properties of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_Map(OH_NativeBuffer *buffer, void **virAddr)](#oh_nativebuffer_map) | Maps the ION memory allocated to an **OH_NativeBuffer** instance to the process address space.<br>This API must be used in pair with [OH_NativeBuffer_Unmap](capi-native-buffer-h.md#oh_nativebuffer_unmap).<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_Unmap(OH_NativeBuffer *buffer)](#oh_nativebuffer_unmap) | Unmaps the ION memory allocated to an **OH_NativeBuffer** instance from the process address space.<br>This function is not thread-safe.|
| [uint32_t OH_NativeBuffer_GetSeqNum(OH_NativeBuffer *buffer)](#oh_nativebuffer_getseqnum) | Obtains the sequence number of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_SetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace colorSpace)](#oh_nativebuffer_setcolorspace) | Sets the color space for an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_MapPlanes(OH_NativeBuffer *buffer, void **virAddr, OH_NativeBuffer_Planes *outPlanes)](#oh_nativebuffer_mapplanes) | Maps the multi-channel ION memory corresponding to an **OH_NativeBuffer** instance to the process address space.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_FromNativeWindowBuffer(OHNativeWindowBuffer *nativeWindowBuffer, OH_NativeBuffer **buffer)](#oh_nativebuffer_fromnativewindowbuffer) | Converts an **OHNativeWindowBuffer** instance to an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_GetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace *colorSpace)](#oh_nativebuffer_getcolorspace) | Obtains the color space of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_SetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey,int32_t size, uint8_t *metadata)](#oh_nativebuffer_setmetadatavalue) | Sets a metadata value for an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_GetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey,int32_t *size, uint8_t **metadata)](#oh_nativebuffer_getmetadatavalue) | Obtains the metadata value of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_MapWaitFence(OH_NativeBuffer *buffer, int32_t fenceFd, void **virAddr)](#oh_nativebuffer_mapwaitfence) | Maps the ION memory corresponding to [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) to the process space, and permanently blocks the input **fenceFd**.<br>If **OK** is returned, the system closes **fenceFd**. For other return values, you need to close **fenceFd** by yourself.<br> This API must be used in pair with [OH_NativeBuffer_Unmap](capi-native-buffer-h.md#oh_nativebuffer_unmap).<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_WriteToParcel(OH_NativeBuffer* buffer, OHIPCParcel* parcel)](#oh_nativebuffer_writetoparcel) | Writes an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object to an IPC serialization object.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_ReadFromParcel(OHIPCParcel* parcel, OH_NativeBuffer** buffer)](#oh_nativebuffer_readfromparcel) | Reads an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object from an IPC serialization object.<br>Creates an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object. When it is no longer used, you need to use this API together with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, a memory leak may occur.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_IsSupported(OH_NativeBuffer_Config config, bool* isSupported)](#oh_nativebuffer_issupported) | Checks whether the system supports the input [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) configuration information.<br>This function is not thread-safe.|
| [int32_t OH_NativeBuffer_MapAndGetConfig(OH_NativeBuffer* buffer, void** virAddr, OH_NativeBuffer_Config* config)](#oh_nativebuffer_mapandgetconfig) | Maps the multi-channel ION memory corresponding to the [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) to the process space and obtains the [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) corresponding to [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md).<br>This function is not thread-safe.|


## Enum Description

### OH_NativeBuffer_Usage

```c
enum OH_NativeBuffer_Usage
```

**Description**

Defines an enum for the **OH_NativeBuffer** usages.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 10

| Enum| Description|
| -- | -- |
| NATIVEBUFFER_USAGE_CPU_READ = (1ULL << 0) | CPU readable.|
| NATIVEBUFFER_USAGE_CPU_WRITE = (1ULL << 1) | CPU writable.|
| NATIVEBUFFER_USAGE_MEM_DMA = (1ULL << 3) | Direct memory access to the buffer.|
| NATIVEBUFFER_USAGE_MEM_MMZ_CACHE = (1ULL << 5) | Buffer of the media memory area.<br>**Since**: 20|
| NATIVEBUFFER_USAGE_HW_RENDER = (1ULL << 8) |  GPU writable.<br>**Since**: 12|
| NATIVEBUFFER_USAGE_HW_TEXTURE = (1ULL << 9) | GPU readable.<br>**Since**: 12|
| NATIVEBUFFER_USAGE_CPU_READ_OFTEN = (1ULL << 16) | Direct mapping of CPU.<br>**Since**: 12|
| NATIVEBUFFER_USAGE_ALIGNMENT_512 = (1ULL << 18) | 512-byte alignment.<br>**Since**: 12|

### OH_NativeBuffer_ColorGamut

```c
enum OH_NativeBuffer_ColorGamut
```

**Description**

Defines an enum for the color gamuts of an **OH_NativeBuffer** instance.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum| Description|
| -- | -- |
| NATIVEBUFFER_COLOR_GAMUT_NATIVE = 0 | Default gamut.|
| NATIVEBUFFER_COLOR_GAMUT_STANDARD_BT601 = 1 | Standard BT.601 color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_STANDARD_BT709 = 2 | Standard BT.709 color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_DCI_P3 = 3 | DCI P3 color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_SRGB = 4 | SRGB color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_ADOBE_RGB = 5 | Adobe RGB color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_DISPLAY_P3 = 6 | Display P3 color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_BT2020 = 7 | BT.2020 color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_BT2100_PQ = 8 | BT.2100 PQ color gamut.|
| NATIVEBUFFER_COLOR_GAMUT_BT2100_HLG = 9 | BT.2100 HLG color gamut format|
| NATIVEBUFFER_COLOR_GAMUT_DISPLAY_BT2020 = 10 | Display BT.2020 color gamut.|


## Function Description

### OH_NativeBuffer_Alloc()

```c
OH_NativeBuffer* OH_NativeBuffer_Alloc(const OH_NativeBuffer_Config* config)
```

**Description**

Creates an **OH_NativeBuffer** instance based on an **OH_NativeBuffer_Config** struct. A new **OH_NativeBuffer** instance is created each time this function is called.<br>This API must be used in pair with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, memory leak occurs.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Pointer to an **OH_NativeBuffer_Config** instance.|

**Returns**

| Type| Description|
| -- | -- |
| OH_NativeBuffer* | Returns the pointer to the **OH_NativeBuffer** instance created if the operation is successful; returns **NULL** otherwise.|

### OH_NativeBuffer_Reference()

```c
int32_t OH_NativeBuffer_Reference(OH_NativeBuffer *buffer)
```

**Description**

Increases the reference count of an **OH_NativeBuffer** instance by 1.<br>This API must be used in pair with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, memory leak occurs.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_Unreference()

```c
int32_t OH_NativeBuffer_Unreference(OH_NativeBuffer *buffer)
```

**Description**

Decreases the reference count of an **OH_NativeBuffer** instance by 1 and, when the reference count reaches 0, destroys the instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_GetConfig()

```c
void OH_NativeBuffer_GetConfig(OH_NativeBuffer *buffer, OH_NativeBuffer_Config* config)
```

**Description**

Obtains the properties of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Pointer to an **OH_NativeBuffer_Config** instance, which is used to receive the properties of **OH_NativeBuffer**.|

### OH_NativeBuffer_Map()

```c
int32_t OH_NativeBuffer_Map(OH_NativeBuffer *buffer, void **virAddr)
```

**Description**

Maps the ION memory allocated to an **OH_NativeBuffer** instance to the process address space.<br>This API must be used in pair with [OH_NativeBuffer_Unmap](capi-native-buffer-h.md#oh_nativebuffer_unmap).<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| void **virAddr | Double pointer to the address of the virtual memory.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_Unmap()

```c
int32_t OH_NativeBuffer_Unmap(OH_NativeBuffer *buffer)
```

**Description**

Unmaps the ION memory allocated to an **OH_NativeBuffer** instance from the process address space.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_GetSeqNum()

```c
uint32_t OH_NativeBuffer_GetSeqNum(OH_NativeBuffer *buffer)
```

**Description**

Obtains the sequence number of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns the unique sequence number of the **OH_NativeBuffer** instance.|

### OH_NativeBuffer_SetColorSpace()

```c
int32_t OH_NativeBuffer_SetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace colorSpace)
```

**Description**

Sets the color space for an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace) colorSpace | Pointer to the color space. For details about the available options, see [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_MapPlanes()

```c
int32_t OH_NativeBuffer_MapPlanes(OH_NativeBuffer *buffer, void **virAddr, OH_NativeBuffer_Planes *outPlanes)
```

**Description**

Maps the multi-channel ION memory corresponding to an **OH_NativeBuffer** instance to the process address space.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| void **virAddr | Double pointer to the address of the virtual memory.|
| [OH_NativeBuffer_Planes](capi-oh-nativebuffer-oh-nativebuffer-planes.md) *outPlanes | Pointer to the plane information of all images.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_FromNativeWindowBuffer()

```c
int32_t OH_NativeBuffer_FromNativeWindowBuffer(OHNativeWindowBuffer *nativeWindowBuffer, OH_NativeBuffer **buffer)
```

**Description**

Converts an **OHNativeWindowBuffer** instance to an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *nativeWindowBuffer | Pointer to an [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) instance.|
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) **buffer | Pointer to an **OH_NativeBuffer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_GetColorSpace()

```c
int32_t OH_NativeBuffer_GetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace *colorSpace)
```

**Description**

Obtains the color space of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace) *colorSpace | Pointer to the color space. For details about the available options, see [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_SetMetadataValue()

```c
int32_t OH_NativeBuffer_SetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey,int32_t size, uint8_t *metadata)
```

**Description**

Sets a metadata value for an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey) metadataKey | Metadata type of [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md). For details about the available options, see [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey).|
| int32_t size | Size of the uint8_t vector. For details about the value range, see [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey).|
| uint8_t *metadata |  Pointer to the uint8_t vector.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_GetMetadataValue()

```c
int32_t OH_NativeBuffer_GetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey,int32_t *size, uint8_t **metadata)
```

**Description**

Obtains the metadata value of an **OH_NativeBuffer** instance.<br>This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey) metadataKey | Metadata type of [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md). For details about the available options, see [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey).|
| int32_t *size | Size of the uint8_t vector. For details about the value range, see [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey).|
| uint8_t **metadata |  Double pointer to the uint8_t vector.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise.|

### OH_NativeBuffer_MapWaitFence()

```c
int32_t OH_NativeBuffer_MapWaitFence(OH_NativeBuffer *buffer, int32_t fenceFd, void **virAddr)
```

**Description**

Maps the ION memory corresponding to [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) to the process space, and permanently blocks the input **fenceFd**.

If **OK** is returned, the system closes **fenceFd**. For other return values, you need to close **fenceFd** by yourself.

This API must be used in pair with [OH_NativeBuffer_Unmap](capi-native-buffer-h.md#oh_nativebuffer_unmap).

This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) *buffer | Pointer to an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) instance.|
| int32_t fenceFd | File descriptor handle, which is used for concurrent synchronization control.|
| void **virAddr | Double pointer to the address of the virtual memory.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **NATIVE_ERROR_OK** if the operation is successful.<br>Returns **NATIVE_ERROR_INVALID_ARGUMENTS** if **buffer** or **virAddr** is a null pointer, or **fenceFd** is less than 0.<br>Returns **NATIVE_ERROR_UNKNOWN** if the mapping fails.|

### OH_NativeBuffer_WriteToParcel()

```c
int32_t OH_NativeBuffer_WriteToParcel(OH_NativeBuffer* buffer, OHIPCParcel* parcel)
```

**Description**

Writes an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object to an IPC serialization object.

This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md)* buffer | Pointer to an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) instance.|
| [OHIPCParcel](../apis-ipc-kit/capi-ohipcparcel-ohipcparcel.md)* parcel | Pointer to an [OHIPCParcel](../apis-ipc-kit/capi-ohipcparcel-ohipcparcel.md) struct instance, which is used as the output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **NATIVE_ERROR_OK** if the operation is successful.<br>Returns **NATIVE_ERROR_INVALID_ARGUMENTS** if **buffer** or **parcel** is a null pointer.<br>Returns **NATIVE_ERROR_BINDER_ERROR** if IPC sending fails.|

### OH_NativeBuffer_ReadFromParcel()

```c
int32_t OH_NativeBuffer_ReadFromParcel(OHIPCParcel* parcel, OH_NativeBuffer** buffer)
```

**Description**

Reads an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object from an IPC serialization object.

Creates an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) object. When it is no longer used, you need to use this API together with [OH_NativeBuffer_Unreference](capi-native-buffer-h.md#oh_nativebuffer_unreference). Otherwise, a memory leak may occur.

This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OHIPCParcel](../apis-ipc-kit/capi-ohipcparcel-ohipcparcel.md)* parcel | Pointer to an [OHIPCParcel](../apis-ipc-kit/capi-ohipcparcel-ohipcparcel.md) struct instance.|
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md)** buffer | Level-2 pointer to an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) struct instance, which is used as the output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **NATIVE_ERROR_OK** if the operation is successful.<br>Returns **NATIVE_ERROR_INVALID_ARGUMENTS** if **parcel** or **buffer** is a null pointer.<br>Returns **NATIVE_ERROR_UNKNOWN** if the parcel fails to be deserialized.|

### OH_NativeBuffer_IsSupported()

```c
int32_t OH_NativeBuffer_IsSupported(OH_NativeBuffer_Config config, bool* isSupported)
```

**Description**

Checks whether the system supports the input [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) configuration information.

This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) config | [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) struct instance.|
| bool* isSupported | If the value is **true**, the system supports the input [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) configuration information. If the value is **false**, the system does not support the input **OH_NativeBuffer_Config** configuration information. This parameter is used as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **NATIVE_ERROR_OK** if the operation is successful.<br>Returns **NATIVE_ERROR_INVALID_ARGUMENTS** if **isSupported** is a null pointer.|

### OH_NativeBuffer_MapAndGetConfig()

```c
int32_t OH_NativeBuffer_MapAndGetConfig(OH_NativeBuffer* buffer, void** virAddr, OH_NativeBuffer_Config* config)
```

**Description**

Maps the multi-channel ION memory corresponding to the [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) to the process space and obtains the [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) corresponding to [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md).

This function is not thread-safe.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md)* buffer | Level-2 pointer to an [OH_NativeBuffer](capi-oh-nativebuffer-oh-nativebuffer.md) struct instance.|
| void** virAddr | Level-2 pointer to the address of the virtual memory mapped to the current process, which is used as the output parameter.|
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Pointer to an [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) struct instance, which is used as the output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **NATIVE_ERROR_OK** if the operation is successful.<br>Returns **NATIVE_ERROR_INVALID_ARGUMENTS** if **buffer**, **virAddr**, or **config** is a null pointer.<br>Returns **NATIVE_ERROR_UNKNOWN** if the mapping fails.|
