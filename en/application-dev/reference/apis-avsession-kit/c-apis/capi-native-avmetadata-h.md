# native_avmetadata.h

## Overview

Declare avmetadata builder related interfaces.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMetadataBuilderStruct](capi-ohavsession-oh-avmetadatabuilderstruct.md) | OH_AVMetadataBuilder | Declaring the avmetadata builder. The instance of builder is used for creating avmetadata. |
| [OH_AVMetadataStruct](capi-ohavsession-oh-avmetadatastruct.md) | OH_AVMetadata | Declaring the avmetadata. The instance of avmetadata set by application for current resource. |

### Function

| Name | Description |
| -- | -- |
| [AVMetadata_Result OH_AVMetadataBuilder_Create(OH_AVMetadataBuilder** builder)](#oh_avmetadatabuilder_create) | Creates an AVMetadataBuilder instance. |
| [AVMetadata_Result OH_AVMetadataBuilder_Destroy(OH_AVMetadataBuilder* builder)](#oh_avmetadatabuilder_destroy) | Destroy a builder. |
| [AVMetadata_Result OH_AVMetadataBuilder_SetAssetId(OH_AVMetadataBuilder* builder, const char* assetId)](#oh_avmetadatabuilder_setassetid) | Set current asset id of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetTitle(OH_AVMetadataBuilder* builder, const char* title)](#oh_avmetadatabuilder_settitle) | Set the title of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetArtist(OH_AVMetadataBuilder* builder, const char* artist)](#oh_avmetadatabuilder_setartist) | Set the artist of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetAuthor(OH_AVMetadataBuilder* builder, const char* author)](#oh_avmetadatabuilder_setauthor) | Set the author of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetAlbum(OH_AVMetadataBuilder* builder, const char* album)](#oh_avmetadatabuilder_setalbum) | Set the album information |
| [AVMetadata_Result OH_AVMetadataBuilder_SetWriter(OH_AVMetadataBuilder* builder, const char* writer)](#oh_avmetadatabuilder_setwriter) | Set the writer of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetComposer(OH_AVMetadataBuilder* builder, const char* composer)](#oh_avmetadatabuilder_setcomposer) | Set the composer of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetDuration(OH_AVMetadataBuilder* builder, int64_t duration)](#oh_avmetadatabuilder_setduration) | Set the duration of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetMediaImageUri(OH_AVMetadataBuilder* builder, const char* mediaImageUri)](#oh_avmetadatabuilder_setmediaimageuri) | Set the media image uri of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetSubtitle(OH_AVMetadataBuilder* builder, const char* subtitle)](#oh_avmetadatabuilder_setsubtitle) | Set the subtitle of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetDescription(OH_AVMetadataBuilder* builder, const char* description)](#oh_avmetadatabuilder_setdescription) | Set the media description of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetLyric(OH_AVMetadataBuilder* builder, const char* lyric)](#oh_avmetadatabuilder_setlyric) | Set the media lyric content of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetSkipIntervals(OH_AVMetadataBuilder* builder, AVMetadata_SkipIntervals intervals)](#oh_avmetadatabuilder_setskipintervals) | Set the skip intervals of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetDisplayTags(OH_AVMetadataBuilder* builder, int32_t tags)](#oh_avmetadatabuilder_setdisplaytags) | Set the display tags of the resource |
| [AVMetadata_Result OH_AVMetadataBuilder_SetFilter(OH_AVMetadataBuilder* builder, uint32_t filter)](#oh_avmetadatabuilder_setfilter) | Set the protocols supported |
| [AVMetadata_Result OH_AVMetadataBuilder_GenerateAVMetadata(OH_AVMetadataBuilder* builder, OH_AVMetadata** avMetadata)](#oh_avmetadatabuilder_generateavmetadata) | Create the avmetadata. |
| [AVMetadata_Result OH_AVMetadata_Destroy(OH_AVMetadata* avMetadata)](#oh_avmetadata_destroy) | Request to release the avmetadata. |

## Function description

### OH_AVMetadataBuilder_Create()

```c
AVMetadata_Result OH_AVMetadataBuilder_Create(OH_AVMetadataBuilder** builder)
```

**Description**

Creates an AVMetadataBuilder instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)** builder | The builder reference to the created result. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM} The param of builder is nullptr.<br>        {@link AVMETADATA_ERROR_NO_MEMORY} No memory to allocate a new instance. |

### OH_AVMetadataBuilder_Destroy()

```c
AVMetadata_Result OH_AVMetadataBuilder_Destroy(OH_AVMetadataBuilder* builder)
```

**Description**

Destroy a builder.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM} The param of builder is nullptr. |

### OH_AVMetadataBuilder_SetAssetId()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetAssetId(OH_AVMetadataBuilder* builder, const char* assetId)
```

**Description**

Set current asset id of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* assetId | The current assetId of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of assetId is nullptr. |

### OH_AVMetadataBuilder_SetTitle()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetTitle(OH_AVMetadataBuilder* builder, const char* title)
```

**Description**

Set the title of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* title | The title of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of title is nullptr. |

### OH_AVMetadataBuilder_SetArtist()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetArtist(OH_AVMetadataBuilder* builder, const char* artist)
```

**Description**

Set the artist of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* artist | The artist of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of artist is nullptr. |

### OH_AVMetadataBuilder_SetAuthor()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetAuthor(OH_AVMetadataBuilder* builder, const char* author)
```

**Description**

Set the author of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* author | The author of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of author is nullptr. |

### OH_AVMetadataBuilder_SetAlbum()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetAlbum(OH_AVMetadataBuilder* builder, const char* album)
```

**Description**

Set the album information

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* album | The album name |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Return code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of album is nullptr. |

### OH_AVMetadataBuilder_SetWriter()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetWriter(OH_AVMetadataBuilder* builder, const char* writer)
```

**Description**

Set the writer of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* writer | The writer of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of writer is nullptr. |

### OH_AVMetadataBuilder_SetComposer()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetComposer(OH_AVMetadataBuilder* builder, const char* composer)
```

**Description**

Set the composer of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* composer | The composer of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of composer is nullptr. |

### OH_AVMetadataBuilder_SetDuration()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetDuration(OH_AVMetadataBuilder* builder, int64_t duration)
```

**Description**

Set the duration of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| int64_t duration | The duration of resource, in miliseconds |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM} The param of builder is nullptr. |

### OH_AVMetadataBuilder_SetMediaImageUri()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetMediaImageUri(OH_AVMetadataBuilder* builder, const char* mediaImageUri)
```

**Description**

Set the media image uri of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* mediaImageUri | The mediaImageUri of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of mediaImageUri nullptr. |

### OH_AVMetadataBuilder_SetSubtitle()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetSubtitle(OH_AVMetadataBuilder* builder, const char* subtitle)
```

**Description**

Set the subtitle of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* subtitle | The subtitle of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of subtitle nullptr. |

### OH_AVMetadataBuilder_SetDescription()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetDescription(OH_AVMetadataBuilder* builder, const char* description)
```

**Description**

Set the media description of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* description | The description of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of description nullptr. |

### OH_AVMetadataBuilder_SetLyric()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetLyric(OH_AVMetadataBuilder* builder, const char* lyric)
```

**Description**

Set the media lyric content of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| const char* lyric | The lyric of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of lyric nullptr. |

### OH_AVMetadataBuilder_SetSkipIntervals()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetSkipIntervals(OH_AVMetadataBuilder* builder, AVMetadata_SkipIntervals intervals)
```

**Description**

Set the skip intervals of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| AVMetadata_SkipIntervals intervals | The intervals of resource, only can be set : 10, 15, 30 |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of intervals is invalid. |

### OH_AVMetadataBuilder_SetDisplayTags()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetDisplayTags(OH_AVMetadataBuilder* builder, int32_t tags)
```

**Description**

Set the display tags of the resource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| int32_t tags | The display tags of resource which are supported by this app to be displayed on the media center |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM} The param of builder is nullptr. |

### OH_AVMetadataBuilder_SetFilter()

```c
AVMetadata_Result OH_AVMetadataBuilder_SetFilter(OH_AVMetadataBuilder* builder, uint32_t filter)
```

**Description**

Set the protocols supported

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| uint32_t filter | The protocols supported by this session,if not set, the default is {@link TYPE_CAST_PLUS_STREAM} |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of filter is invalid. |

### OH_AVMetadataBuilder_GenerateAVMetadata()

```c
AVMetadata_Result OH_AVMetadataBuilder_GenerateAVMetadata(OH_AVMetadataBuilder* builder, OH_AVMetadata** avMetadata)
```

**Description**

Create the avmetadata.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataBuilder](capi-ohavsession-oh-avmetadatabuilderstruct.md)* builder | The metadata builder instance pointer |
| [OH_AVMetadata](capi-ohavsession-oh-avmetadatastruct.md)** avMetadata | Pointer to a variable to receive the avMetadata object. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_NO_MEMORY} No memory to allocate a new instance.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of avMetadata is nullptr. |

### OH_AVMetadata_Destroy()

```c
AVMetadata_Result OH_AVMetadata_Destroy(OH_AVMetadata* avMetadata)
```

**Description**

Request to release the avmetadata.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadata](capi-ohavsession-oh-avmetadatastruct.md)* avMetadata | Pointer to a variable to receive the avMetadata object. |

**Returns**:

| Type | Description |
| -- | -- |
| AVMetadata_Result | Function result code:          {@link AVMETADATA_SUCCESS} If the execution is successful.<br>        {@link AVMETADATA_ERROR_INVALID_PARAM} The param of avMetadata is nullptr. |


