# native_avqueueitem.h

## Overview

Declare avqueueitem related interfaces.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVSession_AVQueueItem](capi-ohavsession-oh-avsession-avqueueitem.md) | OH_AVSession_AVQueueItem | Declaring the avqueue item. The instance of AVQueueItem. |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md) | OH_AVSession_AVMediaDescription | Declaring the AVMediaDescription. The instance of AVMediaDescription set by application for current resource. |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md) | OH_AVSession_AVMediaDescriptionBuilder | Declaring the AVMediaDescription builder. The instance of builder is used for creating AVMediaDescription. |

### Function

| Name | Description |
| -- | -- |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Create(OH_AVSession_AVMediaDescriptionBuilder** builder)](#oh_avsession_avmediadescriptionbuilder_create) | Creates an OH_AVSession_AVMediaDescriptionBuilder instance. Call [OH_AVSession_AVMediaDescriptionBuilder_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescriptionbuilder_destroy) to release the builder object when it is not used anymore. |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Destroy(OH_AVSession_AVMediaDescriptionBuilder* builder)](#oh_avsession_avmediadescriptionbuilder_destroy) | Destroys a builder. |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAssetId(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* assetId)](#oh_avsession_avmediadescriptionbuilder_setassetid) | Set current asset id of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* title)](#oh_avsession_avmediadescriptionbuilder_settitle) | Set the title of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* subtitle)](#oh_avsession_avmediadescriptionbuilder_setsubtitle) | Set the subtitle of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetArtist(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* artist)](#oh_avsession_avmediadescriptionbuilder_setartist) | Set the artist of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumCoverUri)](#oh_avsession_avmediadescriptionbuilder_setalbumcoveruri) | Set the media image url of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaType(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaType)](#oh_avsession_avmediadescriptionbuilder_setmediatype) | Set the media type of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* lyricContent)](#oh_avsession_avmediadescriptionbuilder_setlyriccontent) | Set the lyric content of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetDuration(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t duration)](#oh_avsession_avmediadescriptionbuilder_setduration) | Set the duration of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaUri)](#oh_avsession_avmediadescriptionbuilder_setmediauri) | Set the media uri of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t startPosition)](#oh_avsession_avmediadescriptionbuilder_setstartposition) | Set the start position of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t mediaSize)](#oh_avsession_avmediadescriptionbuilder_setmediasize) | Set the size of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumTitle)](#oh_avsession_avmediadescriptionbuilder_setalbumtitle) | Set the album title of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAppName(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* appName)](#oh_avsession_avmediadescriptionbuilder_setappname) | Set the app name of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAssetId(OH_AVSession_AVMediaDescription* description, char** assetId)](#oh_avsession_avmediadescription_getassetid) | Get current asset id of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetTitle(OH_AVSession_AVMediaDescription* description, char** title)](#oh_avsession_avmediadescription_gettitle) | Get the title of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetSubtitle(OH_AVSession_AVMediaDescription* description, char** subtitle)](#oh_avsession_avmediadescription_getsubtitle) | Get the subtitle of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetArtist(OH_AVSession_AVMediaDescription* description, char** artist)](#oh_avsession_avmediadescription_getartist) | Get the artist of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumCoverUri(OH_AVSession_AVMediaDescription* description, char** albumCoverUri)](#oh_avsession_avmediadescription_getalbumcoveruri) | Get the media image url of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaType(OH_AVSession_AVMediaDescription* description, char** mediaType)](#oh_avsession_avmediadescription_getmediatype) | Get the media type information |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetLyricContent(OH_AVSession_AVMediaDescription* description, char** lyricContent)](#oh_avsession_avmediadescription_getlyriccontent) | Get the lyric content of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetDuration(OH_AVSession_AVMediaDescription* description, int32_t* duration)](#oh_avsession_avmediadescription_getduration) | Get the duration of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaUri(OH_AVSession_AVMediaDescription* description, char** mediaUri)](#oh_avsession_avmediadescription_getmediauri) | Get the media uri of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetStartPosition(OH_AVSession_AVMediaDescription* description, int32_t* startPosition)](#oh_avsession_avmediadescription_getstartposition) | Get start position of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaSize(OH_AVSession_AVMediaDescription* description, int32_t* mediaSize)](#oh_avsession_avmediadescription_getmediasize) | Get media size of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumTitle(OH_AVSession_AVMediaDescription* description, char** albumTitle)](#oh_avsession_avmediadescription_getalbumtitle) | Get the album title of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAppName(OH_AVSession_AVMediaDescription* description, char** appName)](#oh_avsession_avmediadescription_getappname) | Get the app name of the resource |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription(OH_AVSession_AVMediaDescriptionBuilder* builder, OH_AVSession_AVMediaDescription** avMediaDescription)](#oh_avsession_avmediadescriptionbuilder_generateavmediadescription) | Create the avMediaDescription. Call [OH_AVSession_AVMediaDescription_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescription_destroy) to release the avMediaDescription object when it is not used anymore. |
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_Destroy(OH_AVSession_AVMediaDescription* avMediaDescription)](#oh_avsession_avmediadescription_destroy) | Request to release the avMediaDescription. |

## Function description

### OH_AVSession_AVMediaDescriptionBuilder_Create()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Create(OH_AVSession_AVMediaDescriptionBuilder** builder)
```

**Description**

Creates an OH_AVSession_AVMediaDescriptionBuilder instance. Call [OH_AVSession_AVMediaDescriptionBuilder_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescriptionbuilder_destroy) to release the builder object when it is not used anymore.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)** builder | The builder reference to the created result. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM} The param of builder is nullptr.<br>        {@link AVQUEUEITEM_ERROR_NO_MEMORY} No memory to allocate a new instance. |

### OH_AVSession_AVMediaDescriptionBuilder_Destroy()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Destroy(OH_AVSession_AVMediaDescriptionBuilder* builder)
```

**Description**

Destroys a builder.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM} The param of builder is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetAssetId()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAssetId(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* assetId)
```

**Description**

Set current asset id of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* assetId | The current assetId of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of assetId is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* title)
```

**Description**

Set the title of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* title | The title of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of title is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* subtitle)
```

**Description**

Set the subtitle of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* subtitle | The subtitle of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of subtitle is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetArtist()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetArtist(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* artist)
```

**Description**

Set the artist of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* artist | The artist of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of artist is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumCoverUri)
```

**Description**

Set the media image url of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* albumCoverUri | The image url of resource use to display in media center. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of albumCoverUri is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaType()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaType(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaType)
```

**Description**

Set the media type of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* mediaType | The media type of the resource, such as VIDEO or AUDIO. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Return code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of mediaType is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* lyricContent)
```

**Description**

Set the lyric content of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* lyricContent | The lyricContent of resource, it should be lrc format. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of lyricContent is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetDuration()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetDuration(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t duration)
```

**Description**

Set the duration of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const int32_t duration | The duration of resource, in milliseconds |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of duration is invalid. |

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaUri)
```

**Description**

Set the media uri of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* mediaUri | The media uri of the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of mediaUri is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t startPosition)
```

**Description**

Set the start position of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const int32_t startPosition | The start position of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of startPosition is invalid. |

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t mediaSize)
```

**Description**

Set the size of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const int32_t mediaSize | The size of the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Return code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1. The param of builder is nullptr.                                                  2. The param of mediaSize is invalid. |

### OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumTitle)
```

**Description**

Set the album title of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* albumTitle | The album title of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr.                                                  2.The param of albumTitle is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_SetAppName()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAppName(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* appName)
```

**Description**

Set the app name of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| const char* appName | The app name of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr.                                                  2.The param of title  is appName. |

### OH_AVSession_AVMediaDescription_GetAssetId()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAssetId(OH_AVSession_AVMediaDescription* description, char** assetId)
```

**Description**

Get current asset id of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** assetId | Pointer variable that will be set assetId. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of assetId is nullptr. |

### OH_AVSession_AVMediaDescription_GetTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetTitle(OH_AVSession_AVMediaDescription* description, char** title)
```

**Description**

Get the title of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** title | Pointer variable that will be set title. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of title is nullptr. |

### OH_AVSession_AVMediaDescription_GetSubtitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetSubtitle(OH_AVSession_AVMediaDescription* description, char** subtitle)
```

**Description**

Get the subtitle of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** subtitle | Pointer variable that will be set subtitle. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of subtitle is nullptr. |

### OH_AVSession_AVMediaDescription_GetArtist()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetArtist(OH_AVSession_AVMediaDescription* description, char** artist)
```

**Description**

Get the artist of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** artist | Pointer variable that will be set artist. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of artist is nullptr. |

### OH_AVSession_AVMediaDescription_GetAlbumCoverUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumCoverUri(OH_AVSession_AVMediaDescription* description, char** albumCoverUri)
```

**Description**

Get the media image url of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** albumCoverUri | Pointer variable that will be set to media image url. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of albumCoverUri is nullptr. |

### OH_AVSession_AVMediaDescription_GetMediaType()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaType(OH_AVSession_AVMediaDescription* description, char** mediaType)
```

**Description**

Get the media type information

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** mediaType | Pointer variable that will be set media type. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of mediaType is nullptr. |

### OH_AVSession_AVMediaDescription_GetLyricContent()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetLyricContent(OH_AVSession_AVMediaDescription* description, char** lyricContent)
```

**Description**

Get the lyric content of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** lyricContent | Pointer variable that will be set lyric content. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of lyricContent is nullptr. |

### OH_AVSession_AVMediaDescription_GetDuration()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetDuration(OH_AVSession_AVMediaDescription* description, int32_t* duration)
```

**Description**

Get the duration of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| int32_t* duration | Pointer variable that will be set duration of the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}                                                 1. The param of builder is nullptr.                                                 2. The param of duration is nullptr. |

### OH_AVSession_AVMediaDescription_GetMediaUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaUri(OH_AVSession_AVMediaDescription* description, char** mediaUri)
```

**Description**

Get the media uri of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** mediaUri | Pointer variable that will be set media uri. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of mediaUri is nullptr. |

### OH_AVSession_AVMediaDescription_GetStartPosition()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetStartPosition(OH_AVSession_AVMediaDescription* description, int32_t* startPosition)
```

**Description**

Get start position of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| int32_t* startPosition | Pointer variable that will be set start position of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}                                                 1. The param of description is nullptr.                                                 2. The param of startPosition is nullptr. |

### OH_AVSession_AVMediaDescription_GetMediaSize()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaSize(OH_AVSession_AVMediaDescription* description, int32_t* mediaSize)
```

**Description**

Get media size of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| int32_t* mediaSize | Pointer variable that will be set media size of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}                                                 1. The param of description is nullptr.                                                 2. The param of mediaSize is nullptr. |

### OH_AVSession_AVMediaDescription_GetAlbumTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumTitle(OH_AVSession_AVMediaDescription* description, char** albumTitle)
```

**Description**

Get the album title of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** albumTitle | Pointer variable that will be set album title of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of albumTitle is nullptr. |

### OH_AVSession_AVMediaDescription_GetAppName()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAppName(OH_AVSession_AVMediaDescription* description, char** appName)
```

**Description**

Get the app name of the resource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | The AVMediaDescription instance pointer |
| char** appName | Pointer variable that will be set to app name of resource. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                 1.The param of description is nullptr.                                                 2.The param of appName is nullptr. |

### OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription(OH_AVSession_AVMediaDescriptionBuilder* builder, OH_AVSession_AVMediaDescription** avMediaDescription)
```

**Description**

Create the avMediaDescription. Call [OH_AVSession_AVMediaDescription_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescription_destroy) to release the avMediaDescription object when it is not used anymore.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | The AVMediaDescription builder instance pointer |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)** avMediaDescription | Pointer to a variable to receive the avMediaDescription object. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_NO_MEMORY} No memory to allocate a new instance.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM}:                                                  1.The param of builder is nullptr;                                                  2.The param of avMediaDescription is nullptr. |

### OH_AVSession_AVMediaDescription_Destroy()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_Destroy(OH_AVSession_AVMediaDescription* avMediaDescription)
```

**Description**

Request to release the avMediaDescription.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* avMediaDescription | Pointer to a variable to receive the avMediaDescription object. |

**Returns**:

| Type | Description |
| -- | -- |
| AVQueueItem_Result | Function result code:          {@link AVQUEUEITEM_SUCCESS} If the execution is successful.<br>        {@link AVQUEUEITEM_ERROR_INVALID_PARAM} The param of avMediaDescription is nullptr. |


