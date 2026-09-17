# native_buffer.h

## Overview

Defines the functions for obtaining and using a native buffer.

**Library**: libnative_buffer.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) | OH_NativeBuffer_Config | <b>OH_NativeBuffer</b> config. Used to allocating new <b>OH_NativeBuffer</b> and query parameters if existing ones. |
| [OH_NativeBuffer_Plane](capi-oh-nativebuffer-oh-nativebuffer-plane.md) | OH_NativeBuffer_Plane | Holds info for a single image plane. |
| [OH_NativeBuffer_Planes](capi-oh-nativebuffer-oh-nativebuffer-planes.md) | OH_NativeBuffer_Planes | Holds all image planes. |
| [OHIPCParcel](capi-oh-nativebuffer-ohipcparcel.md) | OHIPCParcel | Defines the ipc parcel. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeBuffer_Usage](#oh_nativebuffer_usage) | OH_NativeBuffer_Usage | Indicates the usage of a native buffer. |
| [OH_NativeBuffer_ColorGamut](#oh_nativebuffer_colorgamut) | OH_NativeBuffer_ColorGamut | Indicates the color gamut of a native buffer. |

### Function

| Name | Description |
| -- | -- |
| [OH_NativeBuffer* OH_NativeBuffer_Alloc(const OH_NativeBuffer_Config* config)](#oh_nativebuffer_alloc) | Alloc a <b>OH_NativeBuffer</b> that matches the passed BufferRequestConfig. A new <b>OH_NativeBuffer</b> instance is created each time this function is called. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_Reference(OH_NativeBuffer *buffer)](#oh_nativebuffer_reference) | Adds the reference count of a OH_NativeBuffer. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_Unreference(OH_NativeBuffer *buffer)](#oh_nativebuffer_unreference) | Decreases the reference count of a OH_NativeBuffer and, when the reference count reaches 0, destroys this OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [void OH_NativeBuffer_GetConfig(OH_NativeBuffer *buffer, OH_NativeBuffer_Config* config)](#oh_nativebuffer_getconfig) | Return a config of the OH_NativeBuffer in the passed OHNativeBufferConfig struct. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_Map(OH_NativeBuffer *buffer, void **virAddr)](#oh_nativebuffer_map) | Provide direct cpu access to the OH_NativeBuffer in the process's address space. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unmap</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_Unmap(OH_NativeBuffer *buffer)](#oh_nativebuffer_unmap) | Remove direct cpu access ability of the OH_NativeBuffer in the process's address space. This interface is a non-thread-safe type interface. |
| [uint32_t OH_NativeBuffer_GetSeqNum(OH_NativeBuffer *buffer)](#oh_nativebuffer_getseqnum) | Get the system wide unique sequence number of the OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_MapPlanes(OH_NativeBuffer *buffer, void **virAddr, OH_NativeBuffer_Planes *outPlanes)](#oh_nativebuffer_mapplanes) | Provide direct cpu access to the potentially multi-planar OH_NativeBuffer in the process's address space. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_FromNativeWindowBuffer(OHNativeWindowBuffer *nativeWindowBuffer, OH_NativeBuffer **buffer)](#oh_nativebuffer_fromnativewindowbuffer) | Converts an <b>OHNativeWindowBuffer</b> instance to an <b>OH_NativeBuffer</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_SetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace colorSpace)](#oh_nativebuffer_setcolorspace) | Set the color space of the OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_GetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace *colorSpace)](#oh_nativebuffer_getcolorspace) | Get the color space of the OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_SetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)](#oh_nativebuffer_setmetadatavalue) | Set the metadata type of the OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_GetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)](#oh_nativebuffer_getmetadatavalue) | Set the metadata type of the OH_NativeBuffer. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_MapWaitFence(OH_NativeBuffer *buffer, int32_t fenceFd, void **virAddr)](#oh_nativebuffer_mapwaitfence) | Provide direct cpu access to the OH_NativeBuffer in the process's address space and wait fence. If the interface returns OK, fenceFd does not need to be closed by the developer, Otherwise, the developer needs to close the fenceFd. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_WriteToParcel(OH_NativeBuffer* buffer, OHIPCParcel* parcel)](#oh_nativebuffer_writetoparcel) | Serialize <b>OH_NativeBuffer</b> object to the serialized <b>OHIPCParcel</b> object. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_ReadFromParcel(OHIPCParcel* parcel, OH_NativeBuffer** buffer)](#oh_nativebuffer_readfromparcel) | Deserialize data from the serialized <b>OHIPCParcel</b> object and rebuild <b>OH_NativeBuffer</b> object. This interface will cause an increase in the reference count of the <b>OH_NativeBuffer</b> instance. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_IsSupported(OH_NativeBuffer_Config config, bool* isSupported)](#oh_nativebuffer_issupported) | Check whether the system supports the <b>NativeBufferConfig</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_MapAndGetConfig(OH_NativeBuffer* buffer, void** virAddr, OH_NativeBuffer_Config* config)](#oh_nativebuffer_mapandgetconfig) | Provide direct cpu access to the <b>OH_NativeBuffer</b> in the process's address space, and return a <b>NativeBufferConfig<b> of the <b>OH_NativeBuffer</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeBuffer_SetDmaBufferName(OH_NativeBuffer *buffer, const char *name)](#oh_nativebuffer_setdmabuffername) | Set the dma buffer name of the OH_NativeBuffer. |

## Enum type description

### OH_NativeBuffer_Usage

```c
enum OH_NativeBuffer_Usage
```

**Description**

Indicates the usage of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 10

| Enum item | Description |
| -- | -- |
| NATIVEBUFFER_USAGE_CPU_READ = (1ULL << 0) | CPU read buffer |
| NATIVEBUFFER_USAGE_CPU_WRITE = (1ULL << 1) | CPU write memory |
| NATIVEBUFFER_USAGE_MEM_DMA = (1ULL << 3) | Direct memory access (DMA) buffer |
| NATIVEBUFFER_USAGE_MEM_MMZ_CACHE = (1ULL << 5) |  |
| NATIVEBUFFER_USAGE_HW_RENDER = (1ULL << 8) |  |
| NATIVEBUFFER_USAGE_HW_TEXTURE = (1ULL << 9) |  |
| NATIVEBUFFER_USAGE_CPU_READ_OFTEN = (1ULL << 16) |  |
| NATIVEBUFFER_USAGE_ALIGNMENT_512 = (1ULL << 18) |  |

### OH_NativeBuffer_ColorGamut

```c
enum OH_NativeBuffer_ColorGamut
```

**Description**

Indicates the color gamut of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum item | Description |
| -- | -- |
| NATIVEBUFFER_COLOR_GAMUT_NATIVE = 0 | Native or default |
| NATIVEBUFFER_COLOR_GAMUT_STANDARD_BT601 = 1 | Standard BT601 |
| NATIVEBUFFER_COLOR_GAMUT_STANDARD_BT709 = 2 | Standard BT709 |
| NATIVEBUFFER_COLOR_GAMUT_DCI_P3 = 3 | DCI P3 |
| NATIVEBUFFER_COLOR_GAMUT_SRGB = 4 | SRGB |
| NATIVEBUFFER_COLOR_GAMUT_ADOBE_RGB = 5 | Adobe RGB |
| NATIVEBUFFER_COLOR_GAMUT_DISPLAY_P3 = 6 | Display P3 |
| NATIVEBUFFER_COLOR_GAMUT_BT2020 = 7 | BT2020 |
| NATIVEBUFFER_COLOR_GAMUT_BT2100_PQ = 8 | BT2100 PQ |
| NATIVEBUFFER_COLOR_GAMUT_BT2100_HLG = 9 | BT2100 HLG |
| NATIVEBUFFER_COLOR_GAMUT_DISPLAY_BT2020 = 10 | Display BT2020 |


## Function description

### OH_NativeBuffer_Alloc()

```c
OH_NativeBuffer* OH_NativeBuffer_Alloc(const OH_NativeBuffer_Config* config)
```

**Description**

Alloc a <b>OH_NativeBuffer</b> that matches the passed BufferRequestConfig. A new <b>OH_NativeBuffer</b> instance is created each time this function is called. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Indicates the pointer to a <b>BufferRequestConfig</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeBuffer* | Returns the pointer to the <b>OH_NativeBuffer</b> instance created if the operation is successful, \n  returns <b>NULL</b> otherwise. |

### OH_NativeBuffer_Reference()

```c
int32_t OH_NativeBuffer_Reference(OH_NativeBuffer *buffer)
```

**Description**

Adds the reference count of a OH_NativeBuffer. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_Unreference()

```c
int32_t OH_NativeBuffer_Unreference(OH_NativeBuffer *buffer)
```

**Description**

Decreases the reference count of a OH_NativeBuffer and, when the reference count reaches 0, destroys this OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_GetConfig()

```c
void OH_NativeBuffer_GetConfig(OH_NativeBuffer *buffer, OH_NativeBuffer_Config* config)
```

**Description**

Return a config of the OH_NativeBuffer in the passed OHNativeBufferConfig struct. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Indicates the pointer to the <b>NativeBufferConfig</b> of the buffer. |

### OH_NativeBuffer_Map()

```c
int32_t OH_NativeBuffer_Map(OH_NativeBuffer *buffer, void **virAddr)
```

**Description**

Provide direct cpu access to the OH_NativeBuffer in the process's address space. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unmap</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| void **virAddr | Indicates the address of the <b>OH_NativeBuffer</b> in virtual memory. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_Unmap()

```c
int32_t OH_NativeBuffer_Unmap(OH_NativeBuffer *buffer)
```

**Description**

Remove direct cpu access ability of the OH_NativeBuffer in the process's address space. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_GetSeqNum()

```c
uint32_t OH_NativeBuffer_GetSeqNum(OH_NativeBuffer *buffer)
```

**Description**

Get the system wide unique sequence number of the OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the sequence number, which is unique for each OH_NativeBuffer. |

### OH_NativeBuffer_MapPlanes()

```c
int32_t OH_NativeBuffer_MapPlanes(OH_NativeBuffer *buffer, void **virAddr, OH_NativeBuffer_Planes *outPlanes)
```

**Description**

Provide direct cpu access to the potentially multi-planar OH_NativeBuffer in the process's address space. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| void **virAddr | Indicates the address of the <b>OH_NativeBuffer</b> in virtual memory. |
| [OH_NativeBuffer_Planes](capi-oh-nativebuffer-oh-nativebuffer-planes.md) *outPlanes | Indicates all image planes that contain the pixel data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_FromNativeWindowBuffer()

```c
int32_t OH_NativeBuffer_FromNativeWindowBuffer(OHNativeWindowBuffer *nativeWindowBuffer, OH_NativeBuffer **buffer)
```

**Description**

Converts an <b>OHNativeWindowBuffer</b> instance to an <b>OH_NativeBuffer</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OHNativeWindowBuffer *nativeWindowBuffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |
| OH_NativeBuffer **buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_SetColorSpace()

```c
int32_t OH_NativeBuffer_SetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace colorSpace)
```

**Description**

Set the color space of the OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| OH_NativeBuffer_ColorSpace colorSpace | Indicates the color space of native buffer, see <b>OH_NativeBuffer_ColorSpace</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeBuffer_GetColorSpace()

```c
int32_t OH_NativeBuffer_GetColorSpace(OH_NativeBuffer *buffer, OH_NativeBuffer_ColorSpace *colorSpace)
```

**Description**

Get the color space of the OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| OH_NativeBuffer_ColorSpace *colorSpace | Indicates the color space of native buffer, see <b>OH_NativeBuffer_ColorSpace</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect colorSpace state. |

### OH_NativeBuffer_SetMetadataValue()

```c
int32_t OH_NativeBuffer_SetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)
```

**Description**

Set the metadata type of the OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| OH_NativeBuffer_MetadataKey metadataKey | Indicates the metadata type of native buffer, see <b>OH_NativeBuffer_MetadataKey</b>. |
| int32_t size | Indicates the size of a uint8_t vector. |
| uint8_t *metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer or metadata is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect metadata state.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - Unsupported metadata key. |

### OH_NativeBuffer_GetMetadataValue()

```c
int32_t OH_NativeBuffer_GetMetadataValue(OH_NativeBuffer *buffer, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)
```

**Description**

Set the metadata type of the OH_NativeBuffer. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| OH_NativeBuffer_MetadataKey metadataKey | Indicates the metadata type of native buffer, see <b>OH_NativeBuffer_MetadataKey</b>. |
| int32_t *size | Indicates the size of a uint8_t vector. |
| uint8_t **metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer, metadata, or size is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect metadata state.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - Unsupported metadata key. |

### OH_NativeBuffer_MapWaitFence()

```c
int32_t OH_NativeBuffer_MapWaitFence(OH_NativeBuffer *buffer, int32_t fenceFd, void **virAddr)
```

**Description**

Provide direct cpu access to the OH_NativeBuffer in the process's address space and wait fence. If the interface returns OK, fenceFd does not need to be closed by the developer, Otherwise, the developer needs to close the fenceFd. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| int32_t fenceFd | Indicates the pointer to a file descriptor handle. |
| void **virAddr | Indicates the address of the <b>OH_NativeBuffer</b> in virtual memory. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>{@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer or virAddr is NULL or invalid fenceFd.<br>{@link NATIVE_ERROR_UNKNOWN} 50002000 - map failed. |

### OH_NativeBuffer_WriteToParcel()

```c
int32_t OH_NativeBuffer_WriteToParcel(OH_NativeBuffer* buffer, OHIPCParcel* parcel)
```

**Description**

Serialize <b>OH_NativeBuffer</b> object to the serialized <b>OHIPCParcel</b> object. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer* buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| [OHIPCParcel](capi-oh-nativebuffer-ohipcparcel.md)* parcel | Indicates the serialized <b>OHIPCParcel</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>{@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer or parcel is NULL.<br>{@link SURFACE_ERROR_BINDER_ERROR} 50401000 - ipc send failed. |

### OH_NativeBuffer_ReadFromParcel()

```c
int32_t OH_NativeBuffer_ReadFromParcel(OHIPCParcel* parcel, OH_NativeBuffer** buffer)
```

**Description**

Deserialize data from the serialized <b>OHIPCParcel</b> object and rebuild <b>OH_NativeBuffer</b> object. This interface will cause an increase in the reference count of the <b>OH_NativeBuffer</b> instance. This interface needs to be used in conjunction with <b>OH_NativeBuffer_Unreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-oh-nativebuffer-ohipcparcel.md)* parcel | Indicates the serialized <b>OHIPCParcel</b> object. |
| OH_NativeBuffer** buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>{@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - parcel or buffer is NULL.<br>{@link NATIVE_ERROR_UNKNOWN} 50002000 - deserialize failed. |

### OH_NativeBuffer_IsSupported()

```c
int32_t OH_NativeBuffer_IsSupported(OH_NativeBuffer_Config config, bool* isSupported)
```

**Description**

Check whether the system supports the <b>NativeBufferConfig</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md) config | Indicates the config of the <b>OH_NativeBuffer</b>. |
| bool* isSupported | Indicates whether the system supports the <b>NativeBufferConfig</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>{@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - isSupported is NULL. |

### OH_NativeBuffer_MapAndGetConfig()

```c
int32_t OH_NativeBuffer_MapAndGetConfig(OH_NativeBuffer* buffer, void** virAddr, OH_NativeBuffer_Config* config)
```

**Description**

Provide direct cpu access to the <b>OH_NativeBuffer</b> in the process's address space, and return a <b>NativeBufferConfig<b> of the <b>OH_NativeBuffer</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer* buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| void** virAddr | Indicates the address of the <b>OH_NativeBuffer</b> in virtual memory. |
| [OH_NativeBuffer_Config](capi-oh-nativebuffer-oh-nativebuffer-config.md)* config | Indicates the pointer to the <b>NativeBufferConfig</b> of the buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>{@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer or virAddr or config is NULL or invalid fenceFd.<br>{@link NATIVE_ERROR_UNKNOWN} 50002000 - map failed. |

### OH_NativeBuffer_SetDmaBufferName()

```c
int32_t OH_NativeBuffer_SetDmaBufferName(OH_NativeBuffer *buffer, const char *name)
```

**Description**

Set the dma buffer name of the OH_NativeBuffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeBuffer *buffer | Indicates the pointer to a <b>OH_NativeBuffer</b> instance. |
| const char *name | Indicates the dma buffer name string. The name must start with a letter, only contain letters or digits, and be no longer than 64 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - buffer is NULL or name invalid. |


