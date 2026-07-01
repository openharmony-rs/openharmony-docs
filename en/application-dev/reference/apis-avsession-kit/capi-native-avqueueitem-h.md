# native_avqueueitem.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

Declares the definitions of audio and video queue items.

**File to include:** <multimedia/av_session/native_avqueueitem.h>

**Library:** libohavsession.so

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVSession_AVQueueItem](capi-ohavsession-oh-avsession-avqueueitem.md) | OH_AVSession_AVQueueItem | Defines a struct for the audio and video queue item.|
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md) | OH_AVSession_AVMediaDescription | Defines a struct for the **AVMediaDescription**. It is the audio and video media description instance set by the application for the current resource.|
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md) | OH_AVSession_AVMediaDescriptionBuilder | Defines a struct for the audio and video media description builder. The builder instance is used to create media description information.|

### Functions

| Name| Description|
| -- | -- |
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Create(OH_AVSession_AVMediaDescriptionBuilder** builder)](#oh_avsession_avmediadescriptionbuilder_create) | Creates an **OH_AVSession_AVMediaDescriptionBuilder** instance. When the instance is no longer used, call [OH_AVSession_AVMediaDescriptionBuilder_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescriptionbuilder_destroy) to release the builder object.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Destroy(OH_AVSession_AVMediaDescriptionBuilder* builder)](#oh_avsession_avmediadescriptionbuilder_destroy) | Destroys a builder.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAssetId(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* assetId)](#oh_avsession_avmediadescriptionbuilder_setassetid) | Sets the current asset ID of the media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* title)](#oh_avsession_avmediadescriptionbuilder_settitle) | Sets the title of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* subtitle)](#oh_avsession_avmediadescriptionbuilder_setsubtitle) | Sets the subtitle of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetArtist(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* artist)](#oh_avsession_avmediadescriptionbuilder_setartist) | Sets the artist information of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumCoverUri)](#oh_avsession_avmediadescriptionbuilder_setalbumcoveruri) | Sets the media image URL of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaType(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaType)](#oh_avsession_avmediadescriptionbuilder_setmediatype) | Sets the media type of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* lyricContent)](#oh_avsession_avmediadescriptionbuilder_setlyriccontent) | Sets the lyrics content of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetDuration(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t duration)](#oh_avsession_avmediadescriptionbuilder_setduration) | Sets the duration of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaUri)](#oh_avsession_avmediadescriptionbuilder_setmediauri) | Sets the media URI of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t startPosition)](#oh_avsession_avmediadescriptionbuilder_setstartposition) | Sets the start position of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t mediaSize)](#oh_avsession_avmediadescriptionbuilder_setmediasize) | Sets the size of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumTitle)](#oh_avsession_avmediadescriptionbuilder_setalbumtitle) | Sets the album title of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAppName(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* appName)](#oh_avsession_avmediadescriptionbuilder_setappname) | Sets the name of the application that provides the media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAssetId(OH_AVSession_AVMediaDescription* description, char** assetId)](#oh_avsession_avmediadescription_getassetid) | Obtains the current asset ID of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetTitle(OH_AVSession_AVMediaDescription* description, char** title)](#oh_avsession_avmediadescription_gettitle) | Obtains the title of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetSubtitle(OH_AVSession_AVMediaDescription* description, char** subtitle)](#oh_avsession_avmediadescription_getsubtitle) | Obtains the subtitle of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetArtist(OH_AVSession_AVMediaDescription* description, char** artist)](#oh_avsession_avmediadescription_getartist) | Obtains the artist information of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumCoverUri(OH_AVSession_AVMediaDescription* description, char** albumCoverUri)](#oh_avsession_avmediadescription_getalbumcoveruri) | Obtains the media image URL of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaType(OH_AVSession_AVMediaDescription* description, char** mediaType)](#oh_avsession_avmediadescription_getmediatype) | Obtains the media type information.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetLyricContent(OH_AVSession_AVMediaDescription* description, char** lyricContent)](#oh_avsession_avmediadescription_getlyriccontent) | Obtains the lyrics content of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetDuration(OH_AVSession_AVMediaDescription* description, int32_t* duration)](#oh_avsession_avmediadescription_getduration) | Obtains the duration of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaUri(OH_AVSession_AVMediaDescription* description, char** mediaUri)](#oh_avsession_avmediadescription_getmediauri) | Obtains the media URI of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetStartPosition(OH_AVSession_AVMediaDescription* description, int32_t* startPosition)](#oh_avsession_avmediadescription_getstartposition) | Obtains the start position of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaSize(OH_AVSession_AVMediaDescription* description, int32_t* mediaSize)](#oh_avsession_avmediadescription_getmediasize) | Obtains the media size of a resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumTitle(OH_AVSession_AVMediaDescription* description, char** albumTitle)](#oh_avsession_avmediadescription_getalbumtitle) | Obtains the album title of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAppName(OH_AVSession_AVMediaDescription* description, char** appName)](#oh_avsession_avmediadescription_getappname) | Obtains the application name of a media resource.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription(OH_AVSession_AVMediaDescriptionBuilder* builder, OH_AVSession_AVMediaDescription** avMediaDescription)](#oh_avsession_avmediadescriptionbuilder_generateavmediadescription) | Creates an **avMediaDescription** object. When the object is no longer used, call [OH_AVSession_AVMediaDescription_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescription_destroy) to release the **avMediaDescription** object.|
| [AVQueueItem_Result OH_AVSession_AVMediaDescription_Destroy(OH_AVSession_AVMediaDescription* avMediaDescription)](#oh_avsession_avmediadescription_destroy) | Releases an **avMediaDescription** object.|

## Function Description

### OH_AVSession_AVMediaDescriptionBuilder_Create()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Create(OH_AVSession_AVMediaDescriptionBuilder** builder)
```

**Description**

Creates an **OH_AVSession_AVMediaDescriptionBuilder** instance. When the instance is no longer used, call [OH_AVSession_AVMediaDescriptionBuilder_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescriptionbuilder_destroy) to release the builder object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)** builder | Double pointer to the builder object of the creation result.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**: The **builder** parameter is **nullptr**.<br>         **AVQUEUEITEM_ERROR_NO_MEMORY**: Insufficient memory.|

### OH_AVSession_AVMediaDescriptionBuilder_Destroy()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_Destroy(OH_AVSession_AVMediaDescriptionBuilder* builder)
```

**Description**

Destroys a builder.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**: The **builder** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetAssetId()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAssetId(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* assetId)
```

**Description**

Sets the current asset ID of the media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* assetId | Pointer to the current asset ID of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **assetId** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* title)
```

**Description**

Sets the title of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* title | Pointer to the title of the media asset.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **title** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetSubTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* subtitle)
```

**Description**

Sets the subtitle of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* subtitle | Pointer to the subtitle of a media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **subtitle** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetArtist()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetArtist(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* artist)
```

**Description**

Sets the artist information of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* artist | Pointer to the artist information of the media asset.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **artist** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumCoverUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumCoverUri)
```

**Description**

Sets the media image URL of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* albumCoverUri | Pointer to the image URL of the resource displayed in the media center.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **albumCoverUri** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaType()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaType(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaType)
```

**Description**

Sets the media type of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* mediaType | Pointer to the media type of a media resource. For example, **VIDEO** or **AUDIO**.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **mediaType** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetLyricContent(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* lyricContent)
```

**Description**

Sets the lyrics content of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* lyricContent | Pointer to the lyrics content of a media resource. The format is Lyric Reduced Codec (LRC).|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **lyricContent** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetDuration()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetDuration(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t duration)
```

**Description**

Sets the duration of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const int32_t duration | Duration of a media resource. The unit is milliseconds.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **duration** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaUri(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* mediaUri)
```

**Description**

Sets the media URI of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* mediaUri | Pointer to the URI of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **mediaUri** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetStartPosition(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t startPosition)
```

**Description**

Sets the start position of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const int32_t startPosition | Start position of a media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **startPosition** parameter is invalid.|

### OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetMediaSize(OH_AVSession_AVMediaDescriptionBuilder* builder, const int32_t mediaSize)
```

**Description**

Sets the size of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const int32_t mediaSize | Size of a media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **mediaSize** parameter is invalid.|

### OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAlbumTitle(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* albumTitle)
```

**Description**

Sets the album title of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* albumTitle | Pointer to the album title of a media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **albumTitle** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_SetAppName()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_SetAppName(OH_AVSession_AVMediaDescriptionBuilder* builder, const char* appName)
```

**Description**

Sets the name of the application that provides the media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| const char* appName | Pointer to the name of the application that provides the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **appName** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetAssetId()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAssetId(OH_AVSession_AVMediaDescription* description, char** assetId)
```

**Description**

Obtains the current asset ID of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** assetId | Double pointer to the current asset ID of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. **assetId** is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetTitle(OH_AVSession_AVMediaDescription* description, char** title)
```

**Description**

Obtains the title of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** title | Double pointer to the title of the current media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **title** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetSubtitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetSubtitle(OH_AVSession_AVMediaDescription* description, char** subtitle)
```

**Description**

Obtains the subtitle of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** subtitle | Double pointer to the subtitle of the current media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **subtitle** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetArtist()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetArtist(OH_AVSession_AVMediaDescription* description, char** artist)
```

**Description**

Obtains the artist information of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** artist | Double pointer to the artist information of the current media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **artist** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetAlbumCoverUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumCoverUri(OH_AVSession_AVMediaDescription* description, char** albumCoverUri)
```

**Description**

Obtains the media image URL of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** albumCoverUri | Double pointer to the media image URL of the resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **albumCoverUri** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetMediaType()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaType(OH_AVSession_AVMediaDescription* description, char** mediaType)
```

**Description**

Obtains the media type information.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** mediaType | Double pointer to the current media type.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **mediaType** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetLyricContent()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetLyricContent(OH_AVSession_AVMediaDescription* description, char** lyricContent)
```

**Description**

Obtains the lyrics content of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** lyricContent | Double pointer to the current media lyrics content.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **lyricContent** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetDuration()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetDuration(OH_AVSession_AVMediaDescription* description, int32_t* duration)
```

**Description**

Obtains the duration of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| int32_t* duration | Pointer to the total duration of the current media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **duration** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetMediaUri()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaUri(OH_AVSession_AVMediaDescription* description, char** mediaUri)
```

**Description**

Obtains the media URI of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** mediaUri | Double pointer to the media URI of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **mediaUri** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetStartPosition()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetStartPosition(OH_AVSession_AVMediaDescription* description, int32_t* startPosition)
```

**Description**

Obtains the start position of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| int32_t* startPosition | Pointer to the start position of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **startPosition** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetMediaSize()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetMediaSize(OH_AVSession_AVMediaDescription* description, int32_t* mediaSize)
```

**Description**

Obtains the media size of a resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| int32_t* mediaSize | Pointer to the size of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **mediaSize** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetAlbumTitle()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAlbumTitle(OH_AVSession_AVMediaDescription* description, char** albumTitle)
```

**Description**

Obtains the album title of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** albumTitle | Double pointer to the album title of the current media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **albumTitle** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_GetAppName()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_GetAppName(OH_AVSession_AVMediaDescription* description, char** appName)
```

**Description**

Obtains the application name of a media resource.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* description | Pointer to the audio and video media description instance.|
| char** appName | Double pointer to the application name of the media resource.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **description** parameter is **nullptr**.<br>                                        2. The **appName** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescriptionBuilder_GenerateAVMediaDescription(OH_AVSession_AVMediaDescriptionBuilder* builder, OH_AVSession_AVMediaDescription** avMediaDescription)
```

**Description**

Creates an **avMediaDescription** object. When the object is no longer used, call [OH_AVSession_AVMediaDescription_Destroy](capi-native-avqueueitem-h.md#oh_avsession_avmediadescription_destroy) to release the **avMediaDescription** object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescriptionBuilder](capi-ohavsession-oh-avsession-avmediadescriptionbuilder.md)* builder | Pointer to the builder instance of the audio and video media description.|
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)** avMediaDescription | Double pointer to the **avMediaDescription** object.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_NO_MEMORY**: Insufficient memory.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**:<br>                                        1. The **builder** parameter is **nullptr**.<br>                                        2. The **avMediaDescription** parameter is **nullptr**.|

### OH_AVSession_AVMediaDescription_Destroy()

```c
AVQueueItem_Result OH_AVSession_AVMediaDescription_Destroy(OH_AVSession_AVMediaDescription* avMediaDescription)
```

**Description**

Releases an **avMediaDescription** object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md)* avMediaDescription | Pointer to the **avMediaDescription** object.|

**Return value**

| Type| Description|
| -- | -- |
| [AVQueueItem_Result](capi-native-avsession-errors-h.md#avqueueitem_result) | **AVQUEUEITEM_SUCCESS**: The function is executed successfully.<br>         **AVQUEUEITEM_ERROR_INVALID_PARAM**: The **avMediaDescription** parameter is **nullptr**.|
