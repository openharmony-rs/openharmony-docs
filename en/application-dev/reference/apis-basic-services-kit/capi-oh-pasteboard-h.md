# oh_pasteboard.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @zhusiyuan2-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=3f7e8cc3ffe8312d3c00ac721422357ddd729ccb translatedAt=2026-11-10T03:58:01.021Z pushedAt=2026-11-10T05:58:19.838Z nl=1 -->

## Overview

Provides the interfaces, data structures, and enum types for accessing the system pasteboard. Supports reading and writing pasteboard data, listening for pasteboard content changes, and obtaining the paste progress.

**File to include**: <database/pasteboard/oh_pasteboard.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-pasteboard.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md) | Pasteboard_ProgressInfo | Defines a struct for the progress information. |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) | Pasteboard_GetDataParams | Defines the parameters required for obtaining paste data and progress from the clipboard. |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) | OH_PasteboardObserver | Defines a pasteboard observer to listen for pasteboard data change events. When the pasteboard content is updated, a callback will be invoked to notify the application. This API is used in applications that need to respond to pasteboard content changes. |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) | OH_Pasteboard | Defines the pasteboard object to operate the system pasteboard. |

### Macros

| Name  | Description   |
|--------------|-----------|
| [PASTEBOARD_MIMETYPE_TEXT_PLAIN](#pasteboard_mimetype_text_plain)  "text/plain" | Defines the plain text type. |
| [PASTEBOARD_MIMETYPE_TEXT_URI](#pasteboard_mimetype_text_uri)  "text/uri" | Defines the URI type. |
| [PASTEBOARD_MIMETYPE_TEXT_HTML](#pasteboard_mimetype_text_html)  "text/html" | Defines the HTML type. |
| [PASTEBOARD_MIMETYPE_PIXELMAP](#pasteboard_mimetype_pixelmap)  "pixelMap" | PixelMap. |
| [PASTEBOARD_MIMETYPE_TEXT_WANT](#pasteboard_mimetype_text_want)  "text/want" | Want. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [Pasteboard_NotifyType](#pasteboard_notifytype) | Pasteboard_NotifyType | Enumerates the data change types of the pasteboard. |
| [Pasteboard_FileConflictOptions](#pasteboard_fileconflictoptions) | Pasteboard_FileConflictOptions | Enumerates the options used to resolve file copy conflicts. |
| [Pasteboard_ProgressIndicator](#pasteboard_progressindicator) | Pasteboard_ProgressIndicator | Enumerates the progress indicator options. You can use the default progress indicator as required. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)](#oh_pasteboard_progresslistener) | OH_Pasteboard_ProgressListener | Defines a callback to be invoked to obtain the progress information when the default progress indicator is not used. |
| [typedef void (\*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)](#pasteboard_notify) | Pasteboard_Notify | Defines a callback to be invoked when the pasteboard content changes. |
| [typedef void (\*Pasteboard_Finalize)(void* context)](#pasteboard_finalize) | Pasteboard_Finalize | Defines a callback to be invoked to release the context when the pasteboard observer object is destroyed. |
| [OH_PasteboardObserver* OH_PasteboardObserver_Create()](#oh_pasteboardobserver_create) | - | Creates an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance and a pointer to it. |
| [int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)](#oh_pasteboardobserver_destroy) | - | Destroys the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. |
| [int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context,const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)](#oh_pasteboardobserver_setdata) | - | Sets a callback for the pasteboard observer. |
| [OH_Pasteboard* OH_Pasteboard_Create()](#oh_pasteboard_create) | - | Creates an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance and a pointer to it. |
| [void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)](#oh_pasteboard_destroy) | - | Destroys the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| [int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)](#oh_pasteboard_subscribe) | - | Subscribes to the pasteboard observer. |
| [int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)](#oh_pasteboard_unsubscribe) | - | Unsubscribes from the pasteboard observer. |
| [bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)](#oh_pasteboard_isremotedata) | - | Checks whether the pasteboard data comes from remote devices. |
| [int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)](#oh_pasteboard_getdatasource) | - | Obtains the pasteboard data source. |
| [bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)](#oh_pasteboard_hastype) | - | Checks whether the pasteboard contains data of the specified type. |
| [bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)](#oh_pasteboard_hasdata) | - | Checks whether the pasteboard contains data. |
| [OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)](#oh_pasteboard_getdata) | - | Obtains data from the pasteboard. |
| [int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)](#oh_pasteboard_setdata) | - | Sets the unified data object in the OH_Pasteboard instance. |
| [int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)](#oh_pasteboard_cleardata) | - | Clears data from the pasteboard. |
| [char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)](#oh_pasteboard_getmimetypes) | - | Obtains the MIME types from the pasteboard. |
| [Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)](#oh_pasteboard_getdataparams_create) | - | Creates a [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) instance and a pointer to it. |
| [void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)](#oh_pasteboard_getdataparams_destroy) | - | Destroys the [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) instance. |
| [void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params,Pasteboard_ProgressIndicator progressIndicator)](#oh_pasteboard_getdataparams_setprogressindicator) | - | Sets a progress indicator in [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md). You can use the default progress indicator as required. |
| [void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)](#oh_pasteboard_getdataparams_setdesturi) | - | Sets the destination path for copying files for the pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md). If file processing is not supported, this parameter does not need to be set. If the application involves complex file processing policies or needs to distinguish multiple storage paths for files, it is recommended not to set this parameter and let the application complete the file copy processing on its own. |
| [void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params,Pasteboard_FileConflictOptions option)](#oh_pasteboard_getdataparams_setfileconflictoptions) | - | Sets the options used to resolve file copy conflicts in a [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) instance. |
| [void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params,const OH_Pasteboard_ProgressListener listener)](#oh_pasteboard_getdataparams_setprogresslistener) | - | Sets a progress listener in a [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) instance. |
| [int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)](#oh_pasteboard_progressinfo_getprogress) | - | Obtains the paste progress in a [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md) instance. |
| [void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)](#oh_pasteboard_progresscancel) | - | Cancels the ongoing paste operation when the pasteboard data is obtained. |
| [OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params,int* status)](#oh_pasteboard_getdatawithprogress) | - | Obtains the pasteboard data and paste progress. Folders cannot be copied. |
| [uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)](#oh_pasteboard_getchangecount) | - | Obtains the number of pasteboard content changes. |
| [void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode))](#oh_pasteboard_syncdelayeddataasync) | - | Syncs all delayed data from the application to the pasteboard. Use this API together with the [OH_UdmfRecordProvider_SetData](../apis-arkdata/capi-udmf-h.md#oh_udmfrecordprovider_setdata) API. When the application uses the delayed copy feature, only the data types supported by the application are written to the pasteboard. Before the application exits, it should call the [OH_Pasteboard_SetData()](#oh_pasteboard_setdata) API to submit all copied data or call the **OH_Pasteboard_SyncDelayedDataAsync** API to notify the pasteboard to obtain all data. The application can exit only after the data sync is complete. Otherwise, other applications may fail to obtain the data. |
| [bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)](#oh_pasteboard_hasremotedata) | - | Checks whether the pasteboard data to be pasted is on a remote device. |

## Macro Description

### PASTEBOARD_MIMETYPE_TEXT_PLAIN

```c
#define PASTEBOARD_MIMETYPE_TEXT_PLAIN "text/plain"
```

**Description**

Defines the plain text type.

**Since**: 22

### PASTEBOARD_MIMETYPE_TEXT_URI

```c
#define PASTEBOARD_MIMETYPE_TEXT_URI "text/uri"
```

**Description**

Defines the URI type.

**Since**: 22

### PASTEBOARD_MIMETYPE_TEXT_HTML

```c
#define PASTEBOARD_MIMETYPE_TEXT_HTML "text/html"
```

**Description**

Defines the HTML type.

**Since**: 22

### PASTEBOARD_MIMETYPE_PIXELMAP

```c
#define PASTEBOARD_MIMETYPE_PIXELMAP "pixelMap"
```

**Description**

Defines the pixelMap type.

**Since**: 22

### PASTEBOARD_MIMETYPE_TEXT_WANT

```c
#define PASTEBOARD_MIMETYPE_TEXT_WANT "text/want"
```

**Description**

Defines the Want type.

**Since**: 22

## Enum Description

### Pasteboard_NotifyType

```c
enum Pasteboard_NotifyType
```

**Description**

Enumerates the data change types of the pasteboard. It is used to distinguish the source of pasteboard data changes, that is, whether the data change occurs on the local device or a remote device.

**Since**: 13

| Enum | Description |
| -- | -- |
| NOTIFY_LOCAL_DATA_CHANGE = 1 | Data change on the local device pasteboard. |
| NOTIFY_REMOTE_DATA_CHANGE = 2 | Data change on a non-local device pasteboard in the network. |

### Pasteboard_FileConflictOptions

```c
enum Pasteboard_FileConflictOptions
```

**Description**

Enumerates the options for handling file copy conflicts. When a file with the same name already exists in the destination path of a paste operation, the pasteboard handles the conflict based on the specified policy.

**Since**: 15

| Enum | Description |
| -- | -- |
| PASTEBOARD_OVERWRITE = 0 | Overwrites the file with the same name in the destination path. |
| PASTEBOARD_SKIP = 1 | Skips the file with the same name in the destination path. |

### Pasteboard_ProgressIndicator

```c
enum Pasteboard_ProgressIndicator
```

**Description**

Enumerates the progress indicator options. You can use the default progress indicator as required.

**Since**: 15

| Enum | Description |
| -- | -- |
| PASTEBOARD_NONE = 0 | The default progress indicator is not used. |
| PASTEBOARD_DEFAULT = 1 | The default progress indicator is used. |

## Function Description

### OH_Pasteboard_ProgressListener()

```c
typedef void (*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)
```

**Description**

When the default system progress display is not used, this callback notifies the application of the progress of a copy-paste task to support the implementation of a custom progress UI.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md)* progressInfo | Pointer to the data structure that defines the progress to report. This information is reported only when the progress indicator option [Pasteboard_ProgressIndicator](#pasteboard_progressindicator) is set to PASTEBOARD_NONE. |

### Pasteboard_Notify()

```c
typedef void (*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)
```

**Description**

Defines the callback invoked when the clipboard content changes. Implement this callback to execute application-specific logic after the copied data saved in the clipboard changes.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| void* context | Pointer to the context information passed in by [OH_PasteboardObserver_SetData](#oh_pasteboardobserver_setdata). |
| [Pasteboard_NotifyType](#pasteboard_notifytype) type | Type of the data change. For details, see [Pasteboard_NotifyType](#pasteboard_notifytype). |

### Pasteboard_Finalize()

```c
typedef void (*Pasteboard_Finalize)(void* context)
```

**Description**

Defines a callback used to release the context. It is triggered when the pasteboard data change observer object is destroyed. If resources are dynamically allocated in the Pasteboard_Notify callback, implement this callback to release them.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| void* context | Pointer to the context to be released. When context points to dynamic memory or resources that need to be released manually, release them in the callback. When context points to static memory or resources that do not need to be managed, the callback can do nothing. |

### OH_PasteboardObserver_Create()

```c
OH_PasteboardObserver* OH_PasteboardObserver_Create()
```

**Description**

Creates a pointer to and an instance of a pasteboard data change observer [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md). Typical use cases include listening for pasteboard content changes to implement data synchronization and triggering business logic when the pasteboard content is updated. After this function is called, the system initializes a pasteboard data change observer object and returns a pointer to the object. After the observer is created, the developer needs to set the callback through [OH_PasteboardObserver_SetData](#oh_pasteboardobserver_setdata) and then subscribe to pasteboard change events through [OH_Pasteboard_Subscribe](#oh_pasteboard_subscribe).

- The caller should call [OH_PasteboardObserver_Destroy](#oh_pasteboardobserver_destroy) to release resources when it no longer needs to listen for pasteboard data changes. Otherwise, memory leaks will occur.
- The observer object does not support concurrent access from multiple threads. It must be created and destroyed in the same thread.

**Since**: 13

**Return**

| Type | Description |
| -- | -- |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* | Pointer to the instance of the pasteboard data change observer [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) if the operation is successful; a null pointer otherwise.<br> When the pointer is no longer needed, use [OH_PasteboardObserver_Destroy](#oh_pasteboardobserver_destroy) to destroy the instance. Otherwise, memory leaks will occur. |

### OH_PasteboardObserver_Destroy()

```c
int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)
```

**Description**

Destroys the instance pointed to by the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) pointer. Call this function to destroy the observer object when you no longer need to listen for pasteboard data changes. Before calling this function, ensure that [OH_Pasteboard_Unsubscribe](#oh_pasteboard_unsubscribe) has been called to unsubscribe.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| int | Result code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_PasteboardObserver_SetData()

```c
int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)
```

**Description**

Sets the callback for a pasteboard data change observer. When an application needs to perform specific operations (such as updating the UI display or synchronizing data to other modules) upon pasteboard data changes, it can set the callback through this API. After the callback is set, it is triggered when the corresponding type of pasteboard data changes. The callback is usually executed in a system thread, so thread safety must be ensured. The lifecycle of the callback must not be shorter than that of the observer.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. |
| void* context | Pointer to the context data, which is passed to [Pasteboard_Notify](#pasteboard_notify) as the first parameter. |
| const [Pasteboard_Notify](#pasteboard_notify) callback | Callback invoked when the pasteboard data changes. For details, see [Pasteboard_Notify](#pasteboard_notify). |
| const [Pasteboard_Finalize](#pasteboard_finalize) finalize | Optional callback used to release the context data when the pasteboard data change observer is destroyed. The default value is nullptr, which means no release operation is performed. For details, see [Pasteboard_Finalize](#pasteboard_finalize). |

**Return**

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_Create()

```c
OH_Pasteboard* OH_Pasteboard_Create()
```

**Description**

Creates a pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance and the instance object. Use this function to create a pasteboard object instance when you need to access or operate the system pasteboard. Use the created instance in a timely manner.

**Since**: 13

**Return**

| Type | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance object if the operation is successful; nullptr otherwise.<br> When the pointer is no longer needed, use [OH_Pasteboard_Destroy](#oh_pasteboard_destroy) to destroy the instance object. Otherwise, a memory leak occurs. |

### OH_Pasteboard_Destroy()

```c
void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)
```

**Description**

Destroys the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. This API is used to destroy the pasteboard object and release resources when the pasteboard is no longer needed. Ensure that all subscriptions are canceled before destruction.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

### OH_Pasteboard_Subscribe()

```c
int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)
```

**Description**

Subscribes to pasteboard data change events. Typical use cases include listening for pasteboard content changes, implementing cross-device pasteboard synchronization, and updating the UI when pasteboard content changes. After this function is called, when the pasteboard data changes, the system notifies the application through the observer callback [Pasteboard_Notify](#pasteboard_notify). You can subscribe to data change events of the local device or a remote device, and specify the event type to subscribe to through the type parameter.

- After calling this method to subscribe to pasteboard change events, you must call [OH_Pasteboard_Unsubscribe](#oh_pasteboard_unsubscribe) to unsubscribe when listening is no longer needed.
- When unsubscribing, you must pass in the same observer object and event type as those used for subscription.
- Failure to unsubscribe may result in continuous listening and resource occupation.
- The same observer cannot subscribe to the same event type repeatedly; otherwise, an error is returned.
- The observer object cannot be destroyed before unsubscribing.
- The callback is executed in an asynchronous IPC thread, so thread safety must be ensured.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int type | Type of the pasteboard data change to subscribe to. For details, see [Pasteboard_NotifyType](#pasteboard_notifytype). |
| const [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. It specifies the callback invoked when the pasteboard data changes. For details, see [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md). |

**Return**

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_Unsubscribe()

```c
int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)
```

**Description**

Unsubscribes from the pasteboard data change event. Before calling this API, you must call OH_Pasteboard_Subscribe to subscribe to the pasteboard data change event. This API is used to unsubscribe and release resources when the pasteboard data change event no longer needs to be listened for.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int type | Type of the pasteboard data change subscribed to. It must be the same as the type value passed in during subscription. For details, see [Pasteboard_NotifyType](#pasteboard_notifytype). |
| const [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. It specifies the callback invoked when the pasteboard data changes. For details, see [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md). |

**Return**

| Type | Description |
| -- | -- |
| int | Result code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_IsRemoteData()

```c
bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the data in the pasteboard comes from a remote device. Typical use cases include cross-device pasteboard synchronization, selecting a processing policy based on the data source in distributed scenarios, and implementing security verification related to the data source.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the data comes from a remote device. The value **true** means the data is from a remote device; **false** means the data is from the local device. |

### OH_Pasteboard_GetDataSource()

```c
int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)
```

**Description**

Obtains the data source of the data in the pasteboard. This API is applicable to scenarios where the data source needs to be identified or permission control is required. Calling this API may be time-consuming. You are advised to call it in a non-UI thread.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| char* source | Pointer to the memory used to store the pasteboard data source instance. You need to allocate the memory pointed to by the pointer before calling this API. A size of 128 bytes is recommended. |
| unsigned int len | Length of the memory corresponding to the source pointer. The value must be no less than the length of the data source string (including the string terminator). The recommended length is 128 bytes. If the memory length is insufficient, **ERR_INVALID_PARAMETER** is returned. |

**Return**

| Type | Description |
| -- | -- |
| int | Result code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_HasType()

```c
bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)
```

**Description**

Checks whether the pasteboard contains data of the specified type. Typical use cases include checking whether the pasteboard data type is supported before pasting, selecting different processing methods based on the data type, and verifying the pasteboard data format. Calling this API may take a long time. You are advised to call it in a non-UI thread.
**Since:** 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| const char* type | Data type to be checked, which includes the basic data types and custom data types. The options of the basic data types are as follows: **"text/plain"**, **"text/html"**, **"text/uri"**, **"text/want"**, and **"pixelMap"**. For details, see [Macros](#macros). |

**Return**

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the pasteboard contains data of the specified type. The value **true** means the pasteboard contains data of the specified type; the value **false** means the opposite. |

### OH_Pasteboard_HasData()

```c
bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the pasteboard contains data. This API is used to check whether data exists before reading pasteboard data, so as to avoid operations on empty data.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the pasteboard contains data. The value true means the pasteboard contains data; the value false means the opposite. |

### OH_Pasteboard_HasRemoteData()

```c
bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the pasteboard data is on a remote device. Transferring data across devices takes time. If the pasteboard data is on a remote device, do not check for custom data types or read the pasteboard data on the UI thread.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | Returns the check result. The value **true** indicates that the pasteboard data is on a remote device, and **false** indicates the opposite. Default value: **false**. |

### OH_Pasteboard_GetData()

```c
OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)
```

**Description**

Obtains the data in the pasteboard. After this function is called, the system reads the content in the pasteboard and returns a pointer to the unified data object [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md) instance. Developers can parse the data content through the related OH_UdmfData APIs. The obtained data object must be released by the developer. Because the latency of obtaining data from the pasteboard is affected by the data size and network environment, calling this API may take a long time. It is recommended that developers call this API in a non-UI thread.

- If the pasteboard is empty or the data format is not supported, nullptr is returned.
- The returned OH_UdmfData object must be released by the developer by calling [OH_UdmfData_Destroy](../apis-arkdata/capi-udmf-h.md#oh_udmfdata_destroy).
- When the amount of data to be pasted is large, it is recommended that you use [OH_Pasteboard_GetDataWithProgress](#oh_pasteboard_getdatawithprogress) to obtain progress information.

**Since**: 13

To use the custom control to access the pasteboard content, you must [request the permission to access the pasteboard](../../basic-services/pasteboard/get-pastedata-permission-guidelines.md). Those using [PasteButton](../../security/AccessToken/pastebutton.md) can access the pasteboard content without permission requests.

**Required permissions**: ohos.permission.READ_PASTEBOARD

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int* status | Output parameter, indicating the error code of the operation. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md)* | Pointer to the unified data object [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md) instance if the operation is successful. Otherwise, a null pointer is returned. |

### OH_Pasteboard_SetData()

```c
int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)
```

**Description**

Writes a unified data object to the pasteboard. After the data is written successfully, other applications can access the data through the data reading APIs provided by the system pasteboard. The size of the unified data object is limited by the system pasteboard capacity. After the data is written to the system pasteboard, its lifecycle is managed by the system pasteboard. After this API is called, the valid data content is written to the system pasteboard, overwriting the previous pasteboard content. After the data is written successfully, the callbacks of all observers that have subscribed to the pasteboard data change event are triggered. Other applications can read the data through the pasteboard APIs. This API may take a long time to complete. You are advised to call it in a non-UI thread.

- The size of the serialized data cannot exceed the system capacity limit (the capacity varies with devices and is usually 128 MB).
- The write operation clears all previous content in the pasteboard.
- For scenarios where a large amount of data is copied, you are advised to use the deferred copy feature to improve performance.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md)* data | Pointer to the unified data object [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| int | Result code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_ClearData()

```c
int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)
```

**Description**

Clears the data in the pasteboard. This API is used when the data in the pasteboard needs to be cleared, for example, clearing sensitive data when an application exits. Calling this API may take a long time. It is recommended that developers call it on a non-UI thread.

**Since**: 13

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode).<br> Returns **ERR_OK** if the operation is successful.<br> Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

### OH_Pasteboard_GetMimeTypes()

```c
char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)
```

**Description**

Obtains the MIME types in the pasteboard. Typical use cases include determining the pasteboard data type to select an appropriate processing method and checking whether the data type is supported before pasting. This API may take a long time to complete. You are advised to call it in a non-UI thread.

**Since**: 14

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) *pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| unsigned int *count | Output parameter, which indicates the number of types in the result set. |

**Return**

| Type | Description |
| -- | -- |
| char ** | Pointer to the array of MIME types of all pasteboard content if the operation is successful; otherwise, nullptr. The size of the array is indicated by the count parameter. |

### OH_Pasteboard_GetDataParams_Create()

```c
Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)
```

**Description**

Creates a pointer to the pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) and an instance object. When an application needs to obtain pasteboard data and monitor the progress (for example, in a large file copy scenario), the application calls [OH_Pasteboard_GetDataParams_SetProgressIndicator](#oh_pasteboard_getdataparams_setprogressindicator), [OH_Pasteboard_GetDataParams_SetDestUri](#oh_pasteboard_getdataparams_setdesturi), and [OH_Pasteboard_GetDataParams_SetFileConflictOptions](#oh_pasteboard_getdataparams_setfileconflictoptions) as needed to configure the progress indicator options, the destination path for copying files, and the file conflict options.

**Since**: 15

**Return**

| Type | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) * | Pointer to a pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) instance object if the operation is successful; otherwise, a null pointer.<br> When the pointer is no longer needed, use [OH_Pasteboard_GetDataParams_Destroy](#oh_pasteboard_getdataparams_destroy) to destroy the instance object. Otherwise, a memory leak will occur. |

### OH_Pasteboard_GetDataParams_Destroy()

```c
void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)
```

**Description**

Destroys the instance object pointed to by the [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) pointer of the pasteboard. After this function is called, the Pasteboard_GetDataParams object is released and its parameter configuration becomes invalid. If the parameter object is destroyed while paste data is being obtained, the progress callback may fail to be triggered. This function applies when the Pasteboard_GetDataParams object is no longer needed and its resources should be released.

- This method is used in pair with [OH_Pasteboard_GetDataParams_Create](#oh_pasteboard_getdataparams_create).
- The parameter object must be destroyed after [OH_Pasteboard_GetDataWithProgress](#oh_pasteboard_getdatawithprogress) is called.
- This method must not be called to destroy the object in the progress callback.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the Pasteboard_GetDataParams object of the pasteboard. |

### OH_Pasteboard_GetDataParams_SetProgressIndicator()

```c
void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params, Pasteboard_ProgressIndicator progressIndicator)
```

**Description**

Sets the progress indicator option for the pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md), which determines whether to use the system default progress display. Typical use cases: when pasting large files, use PASTEBOARD_DEFAULT to display the system default progress bar; when a custom progress UI or silent background pasting is required, use PASTEBOARD_NONE.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the pasteboard Pasteboard_GetDataParams. |
| [Pasteboard_ProgressIndicator](#pasteboard_progressindicator) progressIndicator | Progress indicator option. |

### OH_Pasteboard_GetDataParams_SetDestUri()

```c
void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)
```

**Description**

Sets the destination path for copying files. If file processing is not supported, this parameter does not need to be set. If the application involves complex file processing policies or needs to distinguish multiple storage paths for files, it is recommended not to set this parameter and let the application complete the file copy processing on its own. This applies when files in the pasteboard need to be copied to a specified destination path.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the Pasteboard_GetDataParams struct of the pasteboard. |
| const char* destUri | Defines the destination path for copying files. The path must be in absolute path format, and the application must have read and write permissions on the path. |
| uint32_t destUriLen | Defines the length of the destination path for copying files (including the string terminator), in bytes. This value must be equal to the actual length of the string pointed to by destUri. If 0 is passed in or the value does not match the actual length, the API call fails. |

### OH_Pasteboard_GetDataParams_SetFileConflictOptions()

```c
void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params, Pasteboard_FileConflictOptions option)
```

**Description**

Sets the file conflict option for the pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md). When calling [OH_Pasteboard_GetDataWithProgress](#oh_pasteboard_getdatawithprogress), pass the [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md) with the file conflict option already set as a parameter. This applies when a file with the same name exists at the destination path during file copying and a conflict handling policy needs to be set.

- PASTEBOARD_OVERWRITE: Select overwrite when the latest file content must be used.
- PASTEBOARD_SKIP: Select skip when the original file must be retained.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the pasteboard Pasteboard_GetDataParams. |
| [Pasteboard_FileConflictOptions](#pasteboard_fileconflictoptions) option | Option for file copy conflicts. The default value is PASTEBOARD_OVERWRITE. |

### OH_Pasteboard_GetDataParams_SetProgressListener()

```c
void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params, const OH_Pasteboard_ProgressListener listener)
```

**Description**

Sets the progress reporting callback for the pasteboard [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md). This is applicable when you need to customize the progress display UI or silently process paste tasks in the background, in which case you can set this callback to receive progress updates.

**Since**: 15

**Parameters**

| Name                                                                         | Description |
|----------------------------------------------------------------------------------| -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params             | Pointer to the pasteboard Pasteboard_GetDataParams struct. |
| const [OH_Pasteboard_ProgressListener](#oh_pasteboard_progresslistener) listener | Progress reporting callback. It takes effect only when [progressIndicator](#oh_pasteboard_getdataparams_setprogressindicator) is set to PASTEBOARD_NONE. This parameter can be set to NULL to indicate that no progress callback is required. |

### OH_Pasteboard_ProgressInfo_GetProgress()

```c
int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)
```

**Description**

Obtains the paste progress in a [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md) instance. Typical use cases include updating the UI progress bar in a custom progress callback, monitoring the paste progress of large files, and adjusting business logic based on the progress.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md)* progressInfo | Pointer to the [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md) instance of the pasteboard. |

**Return**

| Type | Description |
| -- | -- |
| int | Paste progress percentage, ranging from 0 to 100. |

### OH_Pasteboard_ProgressCancel()

```c
void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)
```

**Description**

Cancels the ongoing paste operation. This function is used to interrupt the data transfer during the execution of [OH_Pasteboard_GetDataWithProgress](#oh_pasteboard_getdatawithprogress). After the call, the current paste operation is terminated, and the partially transferred data may be retained or cleared, depending on the specific operation state. To obtain the pasteboard data again after cancellation, call [OH_Pasteboard_GetDataWithProgress](#oh_pasteboard_getdatawithprogress) again. This function applies to scenarios such as user-initiated cancellation, error-triggered transfer interruption, or paste timeout limitation.

- The cancellation is asynchronous and may not take effect immediately.
- The cancellation is irreversible. Once canceled, if you need to obtain the pasteboard data, you must restart the paste process.

**Since**: 15

**Parameters**

| Name | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the pasteboard Pasteboard_GetDataParams. |

### OH_Pasteboard_GetDataWithProgress()

```c
OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)
```

**Description**

Obtains the data and paste progress of the pasteboard. Copying folders is not supported. After this function is called, the system starts to obtain data from the system pasteboard. If the pasteboard data comes from a remote device or contains a large number of files, the progress is reported through the [OH_Pasteboard_ProgressListener](#oh_pasteboard_progresslistener) callback. After the data transfer is complete, a pointer to the unified data object is returned. The entire process may take a long time, so it is recommended that you call this function in a non-UI thread.

**Since**: 15

To use the custom control to access the pasteboard content, you must [request the permission to access the pasteboard](../../basic-services/pasteboard/get-pastedata-permission-guidelines.md). Those using [PasteButton](../../security/AccessToken/pastebutton.md) can access the pasteboard content without permission requests.

**Required permissions**: ohos.permission.READ_PASTEBOARD

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)* params | Pointer to the Pasteboard_GetDataParams instance. |
| int* status | Output parameter, indicating the error code of the operation. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_UdmfData](../apis-arkdata/capi-udmf-oh-udmfdata.md)* | Pointer to the OH_UdmfData instance returned when the operation is successful. Otherwise, a null pointer is returned. |

### OH_Pasteboard_GetChangeCount()

```c
uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)
```

**Description**

Obtains the number of times the pasteboard content has changed. Typical use cases include determining whether the pasteboard content has changed, implementing incremental synchronization of the pasteboard content, detecting whether the pasteboard content is expired, and implementing cache optimization based on the change count.

**Since**: 18

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) *pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Return**

| Type | Description |
| -- | -- |
| uint32_t | Number of times the pasteboard content has changed if the operation is successful; 0 otherwise.<br> When the pasteboard content is expired or becomes empty after APIs such as OH_Pasteboard_ClearData are called, the change count does not change.<br> When the system restarts or the pasteboard service restarts abnormally, the change count is reset to 0. Copying the same content multiple times in succession is treated as multiple changes, and each copy increments the change count. |

### OH_Pasteboard_SyncDelayedDataAsync()

```c
void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode))
```

**Description**

Notifies the pasteboard to synchronize all delayed data from the application. Delayed data refers to a data transfer mechanism in delayed copy mode, in which the data type is first written to the pasteboard and the actual data content is loaded on demand. This API is used together with the delayed copy API [OH_UdmfRecordProvider_SetData](../apis-arkdata/capi-udmf-h.md#oh_udmfrecordprovider_setdata). When all delayed data is synchronized, the application is notified asynchronously through the callback. When an application copies data using the delayed copy feature, only the data types supported by the application are written to the pasteboard. When the application exits, it should call [OH_Pasteboard_SetData](#oh_pasteboard_setdata) again to proactively submit all copied data, or call this API to notify the pasteboard to obtain the full data, and wait until the data synchronization is complete before continuing to exit. Otherwise, other applications may fail to obtain the data when pasting.

> **NOTE**
> - Calling this API prolongs the exit process. You are advised to directly set data to the pasteboard instead of calling the [OH_UdmfRecordProvider_SetData](../apis-arkdata/capi-udmf-h.md#oh_udmfrecordprovider_setdata) and **OH_Pasteboard_SyncDelayedDataAsync** APIs.

**Since**: 21

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) *pasteboard | Pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| void (*callback)(int errorCode) | Callback invoked when the data synchronization is complete. errorCode indicates the result of the synchronization task. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |