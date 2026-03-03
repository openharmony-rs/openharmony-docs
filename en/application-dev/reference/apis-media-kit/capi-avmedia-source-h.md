# avmedia_source.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xushubo; @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

Defines the struct and enum of **AVMediaSource**.

**File to include**: <multimedia/player_framework/avmedia_source.h>

**Library**: libavmedia_source.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 23

**Related module**: [avmedia_source](capi-avmedia-source.md)

## Total

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) | OH_AVHttpHeader | Defines the HTTP header.|
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) | OH_AVMediaSource | Defines the media source type.|
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) | OH_AVMediaSourceLoadingRequest | Defines the loading request object, which is used by the application to obtain the location of the requested resource.|
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) | OH_AVMediaSourceLoader | Defines the media data loader type, which is implemented by the application.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVLoadingRequestError](#avloadingrequesterror) | AVLoadingRequestError | Enumerates the error codes of network loading requests.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVHttpHeader *OH_AVHttpHeader_Create(void)](#oh_avhttpheader_create) | - | Creates an HTTP header instance.|
| [OH_AVErrCode OH_AVHttpHeader_Destroy(OH_AVHttpHeader *header)](#oh_avhttpheader_destroy) | - | Releases an HTTP header instance.|
| [OH_AVErrCode OH_AVHttpHeader_GetCount(OH_AVHttpHeader *header, uint32_t *count)](#oh_avhttpheader_getcount) | - | Obtains the number of records in an HTTP header instance.|
| [OH_AVErrCode OH_AVHttpHeader_AddRecord(OH_AVHttpHeader *header, const char *key, const char *value)](#oh_avhttpheader_addrecord) | - | Adds a key-value pair record to an HTTP header instance.|
| [OH_AVErrCode OH_AVHttpHeader_GetRecord(OH_AVHttpHeader *header, uint32_t index, const char **key, const char **value)](#oh_avhttpheader_getrecord) | - | Obtains a key-value pair record in an HTTP header instance by index.|
| [OH_AVMediaSource *OH_AVMediaSource_CreateWithUrl(const char *url, OH_AVHttpHeader *header)](#oh_avmediasource_createwithurl) | - | Creates a media source using a URL.|
| [OH_AVMediaSource *OH_AVMediaSource_CreateWithDataSource(OH_AVDataSource *dataSource)](#oh_avmediasource_createwithdatasource) | - | Creates a media source using **OH_AVDataSource**.|
| [OH_AVMediaSource *OH_AVMediaSource_CreateWithFd(int32_t fd, int64_t offset, int64_t size)](#oh_avmediasource_createwithfd) | - | Creates a media source using a file descriptor.|
| [OH_AVErrCode OH_AVMediaSource_Destroy(OH_AVMediaSource *source)](#oh_avmediasource_destroy) | - | Releases a media source instance.|
| [OH_AVErrCode OH_AVMediaSource_SetMimeType(OH_AVMediaSource *source, const char *mimetype)](#oh_avmediasource_setmimetype) | - | Sets the MIME type to process extended media sources.|
| [OH_AVErrCode OH_AVMediaSourceLoadingRequest_GetUrl(OH_AVMediaSourceLoadingRequest *request, const char **url)](#oh_avmediasourceloadingrequest_geturl) | - | Obtains the URL of a request.|
| [OH_AVErrCode OH_AVMediaSourceLoadingRequest_GetHttpHeader(OH_AVMediaSourceLoadingRequest *request, OH_AVHttpHeader **header)](#oh_avmediasourceloadingrequest_gethttpheader) | - | Obtains the HTTP header of a request.|
| [int32_t OH_AVMediaSourceLoadingRequest_RespondData(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, int64_t offset, const uint8_t *data, uint64_t dataSize)](#oh_avmediasourceloadingrequest_responddata) | - | Sends request data to the AVPlayer.|
| [void OH_AVMediaSourceLoadingRequest_RespondHeader(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, OH_AVHttpHeader *header, const char *redirectUrl)](#oh_avmediasourceloadingrequest_respondheader) | - | Sends the response header to the AVPlayer. This API must be called before [OH_AVMediaSourceLoadingRequest_RespondData](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_responddata) is called for the first time.|
| [void OH_AVMediaSourceLoadingRequest_FinishLoading(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, AVLoadingRequestError error)](#oh_avmediasourceloadingrequest_finishloading) | - | Notifies the player of the current request status. After pushing all data of a single resource, the application should send the **LOADING_ERROR_SUCCESS** state to notify the player that the resource push is complete.|
| [OH_AVMediaSourceLoader *OH_AVMediaSourceLoader_Create(void)](#oh_avmediasourceloader_create) | - | Creates an **OH_AVMediaSourceLoader** instance. If the operation is successful, the **OH_AVMediaSourceLoader** pointer is returned. If the operation fails, a null pointer is returned.|
| [OH_AVErrCode OH_AVMediaSourceLoader_Destroy(OH_AVMediaSourceLoader *loader)](#oh_avmediasourceloader_destroy) | - | Releases an **OH_AVMediaSourceLoader** instance.|
| [OH_AVErrCode OH_AVMediaSource_SetMediaSourceLoader(OH_AVMediaSource *source, OH_AVMediaSourceLoader *loader)](#oh_avmediasource_setmediasourceloader) | - | Sets a source loader for the media source instance.|
| [typedef int64_t (\*OH_AVMediaSourceLoaderOnSourceOpenedCallback)(OH_AVMediaSourceLoadingRequest *request, void *userData)](#oh_avmediasourceloaderonsourceopenedcallback) | OH_AVMediaSourceLoaderOnSourceOpenedCallback | Defines the **SourceOpenCallback** function called by the server. The client should handle the passed request and return the unique handle of the opened resource. The client must return the handle immediately after processing the request.|
| [typedef void (\*OH_AVMediaSourceLoaderOnSourceReadCallback)(int64_t uuid, int64_t requestedOffset, int64_t requestedLength, void *userData)](#oh_avmediasourceloaderonsourcereadcallback) | OH_AVMediaSourceLoaderOnSourceReadCallback | Defines the **SourceReadCallback** function called by the server. The client should record the read request and push data using the [OH_AVMediaSourceLoadingRequest_RespondData](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_responddata) and [OH_AVMediaSourceLoadingRequest_RespondHeader](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_respondheader) methods of the request object when there is sufficient data. The client must return immediately after the request is processed.|
| [typedef void (\*OH_AVMediaSourceLoaderOnSourceClosedCallback)(int64_t uuid, void *userData)](#oh_avmediasourceloaderonsourceclosedcallback) | OH_AVMediaSourceLoaderOnSourceClosedCallback | Defines the **SourceCloseCallback** function called by the server. The client should release related resources and return immediately after the request is processed.|
| [OH_AVErrCode OH_AVMediaSourceLoader_SetSourceOpenCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceOpenedCallback callback, void *userData)](#oh_avmediasourceloader_setsourceopencallback) | - | Sets the open callback function for **OH_AVMediaSourceLoader**.|
| [OH_AVErrCode OH_AVMediaSourceLoader_SetSourceReadCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceReadCallback callback, void *userData)](#oh_avmediasourceloader_setsourcereadcallback) | - | Sets the read callback function for **OH_AVMediaSourceLoader**.|
| [OH_AVErrCode OH_AVMediaSourceLoader_SetSourceCloseCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceClosedCallback callback, void *userData)](#oh_avmediasourceloader_setsourceclosecallback) | - | Sets the close callback function for **OH_AVMediaSourceLoader**.|

## Enum Description

### AVLoadingRequestError

```c
enum AVLoadingRequestError
```

**Description**

Enumerates the error codes of network loading requests.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| AV_LOADING_ERROR_SUCCESS = 0 | The resource is successfully downloaded.|
| AV_LOADING_ERROR_NOT_READY = 1 | The resource is not ready and cannot be accessed.|
| AV_LOADING_ERROR_NO_RESOURCE = 2 | The resource URL does not exist.|
| AV_LOADING_ERROR_INVALID_HANDLE = 3 | The UUID of the resource handle is invalid.|
| AV_LOADING_ERROR_ACCESS_DENIED = 4 | The client does not have the permission to request the resource.|
| AV_LOADING_ERROR_ACCESS_TIMEOUT = 5 | The access times out.|
| AV_LOADING_ERROR_AUTHORIZE_FAILED = 6 | The authorization failed.|


## Function Description

### OH_AVHttpHeader_Create()

```c
OH_AVHttpHeader *OH_AVHttpHeader_Create(void)
```

**Description**

Creates an HTTP header instance.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVHttpHeader *](capi-avmedia-source-oh-avhttpheader.md) | Pointer to the **OH_AVHttpHeader** instance if the operation is successful; null pointer if the operation fails.|

### OH_AVHttpHeader_Destroy()

```c
OH_AVErrCode OH_AVHttpHeader_Destroy(OH_AVHttpHeader *header)
```

**Description**

Releases an HTTP header instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the **OH_AVHttpHeader** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The header is a null pointer or the instance fails to be destroyed.|

### OH_AVHttpHeader_GetCount()

```c
OH_AVErrCode OH_AVHttpHeader_GetCount(OH_AVHttpHeader *header, uint32_t *count)
```

**Description**

Obtains the number of records in an HTTP header instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the **OH_AVHttpHeader** instance.|
| uint32_t *count | Pointer to the number of records in the header instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The header is a null pointer.|

### OH_AVHttpHeader_AddRecord()

```c
OH_AVErrCode OH_AVHttpHeader_AddRecord(OH_AVHttpHeader *header, const char *key, const char *value)
```

**Description**

Adds a key-value pair record to an HTTP header instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the **OH_AVHttpHeader** instance.|
| const char *key | Pointer to the key name of the record.|
| const char *value | Pointer to the value of the record.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: Any parameter is a null pointer.|

### OH_AVHttpHeader_GetRecord()

```c
OH_AVErrCode OH_AVHttpHeader_GetRecord(OH_AVHttpHeader *header, uint32_t index, const char **key, const char **value)
```

**Description**

Obtains a key-value pair record in an HTTP header instance by index.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the **OH_AVHttpHeader** instance.|
| uint32_t index | Position of the record in the header.|
| const char **key | Double pointer to the key name of the record.|
| const char **value | Double pointer to the value of the record.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The header is a null pointer or the index is out of range.|

### OH_AVMediaSource_CreateWithUrl()

```c
OH_AVMediaSource *OH_AVMediaSource_CreateWithUrl(const char *url, OH_AVHttpHeader *header)
```

**Description**

Creates a media source using a URL.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const char *url | Pointer to the URL of the media source. The following streaming media formats are supported: HLS, HTTP-FLV, DASH, and HTTPS.|
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the HTTP header attached to the network request.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVMediaSource *](capi-avmedia-source-oh-avmediasource.md) | Pointer to the **OH_AVMediaSource** instance if the operation is successful; null pointer if the operation fails.|

### OH_AVMediaSource_CreateWithDataSource()

```c
OH_AVMediaSource *OH_AVMediaSource_CreateWithDataSource(OH_AVDataSource *dataSource)
```

**Description**

Creates a media source using **OH_AVDataSource**.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| OH_AVDataSource *dataSource | Pointer to **OH_AVDataSource**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVMediaSource *](capi-avmedia-source-oh-avmediasource.md) | Pointer to the **OH_AVMediaSource** instance if the operation is successful; null pointer if the operation fails.|

### OH_AVMediaSource_CreateWithFd()

```c
OH_AVMediaSource *OH_AVMediaSource_CreateWithFd(int32_t fd, int64_t offset, int64_t size)
```

**Description**

Creates a media source using a file descriptor.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| int32_t fd | FD of a media source file.|
| int64_t offset | Offset of the file to be read.|
| int64_t size | File size, in bytes|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVMediaSource *](capi-avmedia-source-oh-avmediasource.md) | Pointer to the **OH_AVMediaSource** instance if the operation is successful; null pointer if the operation fails.|

### OH_AVMediaSource_Destroy()

```c
OH_AVErrCode OH_AVMediaSource_Destroy(OH_AVMediaSource *source)
```

**Description**

Releases a media source instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Pointer to the **OH_AVMediaSource** instance.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **source** is a null pointer or fails to be released.|

### OH_AVMediaSource_SetMimeType()

```c
OH_AVErrCode OH_AVMediaSource_SetMimeType(OH_AVMediaSource *source, const char *mimetype)
```

**Description**

Sets the MIME type to process extended media sources.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Pointer to the **OH_AVMediaSource** instance.|
| const char *mimetype | Pointer to the MIME type ([AV_MimeTypes](arkts-apis-media-e.md#avmimetypes12)) of the media source.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **source** or **mimetype** is a null pointer.<br>     **AV_ERR_UNSUPPORTED_FORMAT**: The **mimetype** is not supported.|

### OH_AVMediaSourceLoadingRequest_GetUrl()

```c
OH_AVErrCode OH_AVMediaSourceLoadingRequest_GetUrl(OH_AVMediaSourceLoadingRequest *request, const char **url)
```

**Description**

Obtains the URL of a request.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) *request | Pointer to the **OH_AVMediaSourceLoadingRequest** instance.|
| const char **url | Double pointer to the URL for output.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **request** is a null pointer or the URL does not exist.|

### OH_AVMediaSourceLoadingRequest_GetHttpHeader()

```c
OH_AVErrCode OH_AVMediaSourceLoadingRequest_GetHttpHeader(OH_AVMediaSourceLoadingRequest *request, OH_AVHttpHeader **header)
```

**Description**

Obtains the HTTP header of a request.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) *request | Pointer to the **OH_AVMediaSourceLoadingRequest** instance.|
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) **header | Double pointer to the HTTP header used for the HTTP request.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **request** is a null pointer.|

### OH_AVMediaSourceLoadingRequest_RespondData()

```c
int32_t OH_AVMediaSourceLoadingRequest_RespondData(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, int64_t offset, const uint8_t *data, uint64_t dataSize)
```

**Description**

Sends request data to the AVPlayer.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) *request | Pointer to the request for opening a resource.|
| int64_t uuid | ID of the resource handle.|
| int64_t offset | Offset of the current media data relative to the start of the resource.|
| const uint8_t *data | Pointer to the media data sent to the player.|
| uint64_t dataSize | Length of the data sent to the player.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of bytes accepted by the current read operation. If the return value is less than 0, the operation fails.<br>     The value **-2** indicates that the player no longer needs the current data, and the client should stop the current read process.<br>     The value **-3** indicates that the player's buffer is full, and the client should wait for the next read.|

### OH_AVMediaSourceLoadingRequest_RespondHeader()

```c
void OH_AVMediaSourceLoadingRequest_RespondHeader(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, OH_AVHttpHeader *header, const char *redirectUrl)
```

**Description**

Sends the response header to the AVPlayer. This API must be called before [OH_AVMediaSourceLoadingRequest_RespondData](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_responddata) is called for the first time.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) *request | Pointer to the request for opening a resource.|
| int64_t uuid | ID of the resource handle.|
| [OH_AVHttpHeader](capi-avmedia-source-oh-avhttpheader.md) *header | Pointer to the header information in the HTTP response.<br>     The application can intersect the header field with the supported fields at the bottom layer and then pass the intersection result to the AVPlayer, or directly pass all the corresponding header information.|
| const char *redirectUrl | Pointer to the redirection URL contained in the HTTP response (if any).|

### OH_AVMediaSourceLoadingRequest_FinishLoading()

```c
void OH_AVMediaSourceLoadingRequest_FinishLoading(OH_AVMediaSourceLoadingRequest *request, int64_t uuid, AVLoadingRequestError error)
```

**Description**

Notifies the player of the current request status. After pushing all data of a single resource, the application should send the **LOADING_ERROR_SUCCESS** state to notify the player that the resource push is complete.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoadingRequest](capi-avmedia-source-oh-avmediasourceloadingrequest.md) *request | Pointer to the request for opening a resource.|
| int64_t uuid | ID of the resource handle.|
| [AVLoadingRequestError](capi-avmedia-source-h.md#avloadingrequesterror) error | Audio playback is in the error state.|

### OH_AVMediaSourceLoader_Create()

```c
OH_AVMediaSourceLoader *OH_AVMediaSourceLoader_Create(void)
```

**Description**

Creates an **OH_AVMediaSourceLoader** instance. If the operation is successful, the **OH_AVMediaSourceLoader** pointer is returned. If the operation fails, a null pointer is returned.

**Since**: 23

### OH_AVMediaSourceLoader_Destroy()

```c
OH_AVErrCode OH_AVMediaSourceLoader_Destroy(OH_AVMediaSourceLoader *loader)
```

**Description**

Releases an **OH_AVMediaSourceLoader** instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) *loader | Pointer to the **OH_AVMediaSourceLoader** instance to be released.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **loader** is a null pointer or fails to be released.|

### OH_AVMediaSource_SetMediaSourceLoader()

```c
OH_AVErrCode OH_AVMediaSource_SetMediaSourceLoader(OH_AVMediaSource *source, OH_AVMediaSourceLoader *loader)
```

**Description**

Sets a source loader for the media source instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Pointer to the **OH_AVMediaSource** that requires a network proxy.|
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) *loader | Pointer to the **OH_AVMediaSourceLoader** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **source** or **loader** is a null pointer, or the operation fails.|

### OH_AVMediaSourceLoaderOnSourceOpenedCallback()

```c
typedef int64_t (*OH_AVMediaSourceLoaderOnSourceOpenedCallback)(OH_AVMediaSourceLoadingRequest *request, void *userData)
```

**Description**

Defines the **SourceOpenCallback** function called by the server. The client should handle the passed request and return the unique handle of the opened resource. The client must return the handle immediately after processing the request.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| OH_AVMediaSourceLoadingRequest \*request | Pointer to the request for opening a resource, including the detailed information about the requested resource and the data push mode.|
| void \*userData | Pointer to the data set by the user in **OH_AVMediaSourceLoader_SetSourceOpenCallback**.|

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Handle of the current resource opening request, which is unique to the request object.<br>     If the value is greater than 0, the request is successful.<br>     Otherwise, the request fails.|

### OH_AVMediaSourceLoaderOnSourceReadCallback()

```c
typedef void (*OH_AVMediaSourceLoaderOnSourceReadCallback)(int64_t uuid, int64_t requestedOffset, int64_t requestedLength, void *userData)
```

**Description**

Defines the **SourceReadCallback** function called by the server. The client should record the read request and push data using the [OH_AVMediaSourceLoadingRequest_RespondData](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_responddata) and [OH_AVMediaSourceLoadingRequest_RespondHeader](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_respondheader) methods of the request object when there is sufficient data. The client must return immediately after the request is processed.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| int64_t uuid | ID of the resource handle.|
| int64_t requestedOffset | Offset of the current media data relative to the start of the resource.|
| int64_t requestedLength | Length of the requested data. The value **-1** indicates that the end of the resource has been reached. In this case, call the [OH_AVMediaSourceLoadingRequest_FinishLoading](capi-avmedia-source-h.md#oh_avmediasourceloadingrequest_finishloading) method to notify the player that the push is complete.|
| void \*userData | Pointer to the data set by the user in **OH_AVMediaSourceLoader_SetSourceReadCallback**.|

### OH_AVMediaSourceLoaderOnSourceClosedCallback()

```c
typedef void (*OH_AVMediaSourceLoaderOnSourceClosedCallback)(int64_t uuid, void *userData)
```

**Description**

Defines the **SourceCloseCallback** function called by the server. The client should release related resources and return immediately after the request is processed.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| int64_t uuid | ID of the resource handle.|
| void \*userData | Pointer to the data set by the user in **OH_AVMediaSourceLoader_SetSourceCloseCallback**.|

### OH_AVMediaSourceLoader_SetSourceOpenCallback()

```c
OH_AVErrCode OH_AVMediaSourceLoader_SetSourceOpenCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceOpenedCallback callback, void *userData)
```

**Description**

Sets the open callback function for **OH_AVMediaSourceLoader**.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) *loader | Pointer to the **OH_AVMediaSourceLoader** instance for which the callback function is to be set.|
| [OH_AVMediaSourceLoaderOnSourceOpenedCallback](capi-avmedia-source-h.md#oh_avmediasourceloaderonsourceopenedcallback) callback | Open callback function to be set.|
| void *userData | Pointer to the user-defined data used in the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **loader** is a null pointer or the operation fails.|

### OH_AVMediaSourceLoader_SetSourceReadCallback()

```c
OH_AVErrCode OH_AVMediaSourceLoader_SetSourceReadCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceReadCallback callback, void *userData)
```

**Description**

Sets the read callback function for **OH_AVMediaSourceLoader**.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) *loader | Pointer to the **OH_AVMediaSourceLoader** instance for which the callback function is to be set.|
| [OH_AVMediaSourceLoaderOnSourceReadCallback](capi-avmedia-source-h.md#oh_avmediasourceloaderonsourcereadcallback) callback | Read callback function to be set.|
| void *userData | Pointer to the user-defined data used in the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **loader** is a null pointer or the operation fails.|

### OH_AVMediaSourceLoader_SetSourceCloseCallback()

```c
OH_AVErrCode OH_AVMediaSourceLoader_SetSourceCloseCallback(OH_AVMediaSourceLoader *loader, OH_AVMediaSourceLoaderOnSourceClosedCallback callback, void *userData)
```

**Description**

Sets the close callback function for **OH_AVMediaSourceLoader**.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVMediaSourceLoader](capi-avmedia-source-oh-avmediasourceloader.md) *loader | Pointer to the **OH_AVMediaSourceLoader** instance for which the callback function is to be set.|
| [OH_AVMediaSourceLoaderOnSourceClosedCallback](capi-avmedia-source-h.md#oh_avmediasourceloaderonsourceclosedcallback) callback | Close callback function to be set.|
| void *userData | Pointer to the user-defined data used in the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>     **AV_ERR_OK**: The execution is successful.<br>     **AV_ERR_INVALID_VAL**: The **loader** is a null pointer or the operation fails.|
