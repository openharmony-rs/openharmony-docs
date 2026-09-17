# native_avsource.h

## Overview

The file declares the APIs for parsing audio and video media data.

**Library**: libnative_media_avsource.so

**System capability**: SystemCapability.Multimedia.Media.Spliter

**Since**: 10

**Related module**: [AVSource](capi-avsource.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVSource](capi-avsource-oh-avsource.md) | OH_AVSource | The struct describes a native object for the media resource interface. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVSource *OH_AVSource_CreateWithDataSource(OH_AVDataSource *dataSource)](#oh_avsource_createwithdatasource) | Creates an OH_AVSource instance with a user-defined data source. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> The lifecycle of **dataSource** must be the same as that of the returned OH_AVSource * pointer. |
| [OH_AVSource *OH_AVSource_CreateWithDataSourceExt(OH_AVDataSourceExt *dataSource, void *userData)](#oh_avsource_createwithdatasourceext) | Creates an OH_AVSource instance with a user-defined data source. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> User-defined data can be passed to its callback functions through the **userData** parameter.<br> The lifecycle of **dataSource** must be the same as that of the returned OH_AVSource * pointer. |
| [OH_AVSource *OH_AVSource_CreateWithURI(char *uri)](#oh_avsource_createwithuri) | Creates an OH_AVSource instance based on a URI. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy). This function supports only HTTP progressive streaming media, but not HLS/DASH streaming media. For HLS/DASH streaming media playback, use the AVPlayer for development. |
| [OH_AVSource *OH_AVSource_CreateWithFD(int32_t fd, int64_t offset, int64_t size)](#oh_avsource_createwithfd) | Creates an OH_AVSource instance based on an FD. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> If **offset** is not the start position of the file or **size** is not the file size, undefined errors such as creation failure and demultiplexing failure may occur due to incomplete data obtained. |
| [OH_AVErrCode OH_AVSource_Destroy(OH_AVSource *source)](#oh_avsource_destroy) | Destroys an OH_AVSource instance and clears internal resources.<br> An instance can be destroyed only once. The destroyed instance cannot be used until it is re-created. You are advised to set the pointer to NULL after the instance is destroyed. |
| [OH_AVFormat *OH_AVSource_GetSourceFormat(OH_AVSource *source)](#oh_avsource_getsourceformat) | Obtains the basic information about a media resource file.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends. |
| [OH_AVFormat *OH_AVSource_GetTrackFormat(OH_AVSource *source, uint32_t trackIndex)](#oh_avsource_gettrackformat) | Obtains the basic information about a track.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends. |
| [OH_AVFormat *OH_AVSource_GetCustomMetadataFormat(OH_AVSource *source)](#oh_avsource_getcustommetadataformat) | Obtains the basic information about custom metadata.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends. |

## Function description

### OH_AVSource_CreateWithDataSource()

```c
OH_AVSource *OH_AVSource_CreateWithDataSource(OH_AVDataSource *dataSource)
```

**Description**

Creates an OH_AVSource instance with a user-defined data source. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> The lifecycle of **dataSource** must be the same as that of the returned OH_AVSource * pointer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVDataSource *dataSource | Pointer to user-defined data source. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVSource *](capi-avsource-oh-avsource.md) | Pointer to the OH_AVSource instance created. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of dataSource is nullptr.      <br>2. The size of the data source is 0.      <br>3. Setting the data source fails.      <br>4. The memory is insufficient.      <br>5. The decoder engine is nullptr.      <br>6. dataSource-&gt;readAt == nullptr. |

### OH_AVSource_CreateWithDataSourceExt()

```c
OH_AVSource *OH_AVSource_CreateWithDataSourceExt(OH_AVDataSourceExt *dataSource, void *userData)
```

**Description**

Creates an OH_AVSource instance with a user-defined data source. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> User-defined data can be passed to its callback functions through the **userData** parameter.<br> The lifecycle of **dataSource** must be the same as that of the returned OH_AVSource * pointer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVDataSourceExt *dataSource | Pointer to the data source struct, which is used to obtain the input data. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVSource *](capi-avsource-oh-avsource.md) | Pointer to the OH_AVSource instance created. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of dataSource is nullptr.      <br>2. The size of the data source is 0.      <br>3. Setting the data source fails.      <br>4. The memory is insufficient.      <br>5. The decoder engine is nullptr.      <br>6. dataSource-&gt;readAt == nullptr. |

### OH_AVSource_CreateWithURI()

```c
OH_AVSource *OH_AVSource_CreateWithURI(char *uri)
```

**Description**

Creates an OH_AVSource instance based on a URI. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy). This function supports only HTTP progressive streaming media, but not HLS/DASH streaming media. For HLS/DASH streaming media playback, use the AVPlayer for development.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *uri | URI of the media resource. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVSource *](capi-avsource-oh-avsource.md) | Pointer to the OH_AVSource instance created. If the operation fails, NULL is returned.   The possible causes of an operation failure are as follows:      <br>1. The network is abnormal.      <br>2. The resource is invalid.      <br>3. The file format is not supported.      <br>4. The application configuration is intercepted because it contains plaintext data. |

### OH_AVSource_CreateWithFD()

```c
OH_AVSource *OH_AVSource_CreateWithFD(int32_t fd, int64_t offset, int64_t size)
```

**Description**

Creates an OH_AVSource instance based on an FD. You can release the instance by calling [OH_AVSource_Destroy](capi-native-avsource-h.md#oh_avsource_destroy).<br> If **offset** is not the start position of the file or **size** is not the file size, undefined errors such as creation failure and demultiplexing failure may occur due to incomplete data obtained.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fd | FD of a media resource file. |
| int64_t offset | Position from which data is to read. |
| int64_t size | File size, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVSource *](capi-avsource-oh-avsource.md) | Pointer to the OH_AVSource instance created. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The FD is invalid.      <br>2. The offset is not the start position of the file.      <br>3. The size is incorrect.      <br>4. The resource is invalid.      <br>5. The file format is not supported. |

### OH_AVSource_Destroy()

```c
OH_AVErrCode OH_AVSource_Destroy(OH_AVSource *source)
```

**Description**

Destroys an OH_AVSource instance and clears internal resources.<br> An instance can be destroyed only once. The destroyed instance cannot be used until it is re-created. You are advised to set the pointer to NULL after the instance is destroyed.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSource](capi-avsource-oh-avsource.md) *source | Pointer to an OH_AVSource instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}:      <br>1. The value of source is nullptr.      <br>2. The value of source does not point to an OH_AVSource instance. |

### OH_AVSource_GetSourceFormat()

```c
OH_AVFormat *OH_AVSource_GetSourceFormat(OH_AVSource *source)
```

**Description**

Obtains the basic information about a media resource file.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSource](capi-avsource-oh-avsource.md) *source | Pointer to an OH_AVSource instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Basic information about the file. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of source is nullptr.      <br>2. The pointer is null or does not point to an OH_AVSource instance.      <br>3. The source is not initialized. |

### OH_AVSource_GetTrackFormat()

```c
OH_AVFormat *OH_AVSource_GetTrackFormat(OH_AVSource *source, uint32_t trackIndex)
```

**Description**

Obtains the basic information about a track.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSource](capi-avsource-oh-avsource.md) *source | Pointer to an OH_AVSource instance. |
| uint32_t trackIndex | Index of the track whose information is to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Basic information about the track. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of source is invalid (either nullptr or a pointer to a non-OH_AVSource instance).      <br>2. The track index is out of range.      <br>3. The source is not initialized. |

### OH_AVSource_GetCustomMetadataFormat()

```c
OH_AVFormat *OH_AVSource_GetCustomMetadataFormat(OH_AVSource *source)
```

**Description**

Obtains the basic information about custom metadata.<br> You must call {@link OH_AVFormat_Destroy} to release the OH_AVFormat instance when its lifecycle ends.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSource](capi-avsource-oh-avsource.md) *source | Pointer to an OH_AVSource instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Basic information about the metadata. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of source is nullptr.      <br>2. The pointer is null or does not point to an OH_AVSource instance.      <br>3. The source is not initialized. |


