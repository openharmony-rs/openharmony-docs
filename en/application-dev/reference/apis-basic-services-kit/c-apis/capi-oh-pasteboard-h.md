# oh_pasteboard.h

## Overview

Provides data structure, enum types, and APIs for accessing the system pasteboard.

**File to Include**: <database/pasteboard/oh_pasteboard.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-basic-services-kit-pasteboard.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md) | Pasteboard_ProgressInfo | Defines a struct for the progress information. |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) | Pasteboard_GetDataParams | Defines the parameters required for obtaining the pasteboard data and paste progress. |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) | OH_PasteboardObserver | Defines a pasteboard observer to listen for pasteboard data change events. When the pasteboard content is updated, a callback will be invoked to notify the application. This API is used in applications that need to respond to pasteboard content changes. |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) | OH_Pasteboard | Defines the pasteboard object to operate the system pasteboard. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Pasteboard_NotifyType](#pasteboard_notifytype) | Pasteboard_NotifyType | Enumerates the data change types of the pasteboard. This enum is used to determine whether the pasteboard data change is from the local device or a remote device. |
| [Pasteboard_FileConflictOptions](#pasteboard_fileconflictoptions) | Pasteboard_FileConflictOptions | Enumerates the options used to resolve file copy conflicts. When a file with the same name already exists in the destination directory, the pasteboard handles the conflict based on the specified policy. |
| [Pasteboard_ProgressIndicator](#pasteboard_progressindicator) | Pasteboard_ProgressIndicator | Enumerates the progress indicator options. You can use the default progress indicator as required. |

### Macros

| Name | Description |
| -- | -- |
| PASTEBOARD_MIMETYPE_TEXT_PLAIN "text/plain" | Plain text type.<br>**Since**: 22 |
| PASTEBOARD_MIMETYPE_TEXT_URI "text/uri" | URI type.<br>**Since**: 22 |
| PASTEBOARD_MIMETYPE_TEXT_HTML "text/html" | HTML type.<br>**Since**: 22 |
| PASTEBOARD_MIMETYPE_PIXELMAP "pixelMap" | PixelMap type.<br>**Since**: 22 |
| PASTEBOARD_MIMETYPE_TEXT_WANT "text/want" | Want type.<br>**Since**: 22 |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)](#oh_pasteboard_progresslistener) | OH_Pasteboard_ProgressListener | Defines a callback to notify the app about the progress of the pasting task when the default progress indicator is not used. This callback is used to support the implementation of a custom progress UI. |
| [typedef void (\*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)](#pasteboard_notify) | Pasteboard_Notify | Defines a callback to be invoked when the pasteboard content changes. Implement this callback when you need to execute app-specific logic upon pasteboard content changes. |
| [typedef void (\*Pasteboard_Finalize)(void* context)](#pasteboard_finalize) | Pasteboard_Finalize | Defines a callback to be invoked to release the context when the pasteboard observer object is destroyed. If resources are dynamically allocated in the **Pasteboard_Notify** callback, you need to implement this callback to release the resources. |
| [OH_PasteboardObserver* OH_PasteboardObserver_Create()](#oh_pasteboardobserver_create) | - | Creates an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance and a pointer to it. Typical use scenarios include listening for pasteboard content changes to implement data synchronization and triggering service logic when the pasteboard content is updated. After this function is called, the system initializes a **PasteboardObserver** instance and returns a pointer to it. After the instance is created, you need to call [OH_PasteboardObserver_SetData](capi-oh-pasteboard-h.md#oh_pasteboardobserver_setdata) to set the callback function and then call [OH_Pasteboard_Subscribe](capi-oh-pasteboard-h.md#oh_pasteboard_subscribe) to subscribe to pasteboard change events.<br> - The caller must call [OH_PasteboardObserver_Destroy](#oh_pasteboardobserver_destroy) to release resources when the pasteboard data changes do not need to be listened for. Otherwise, memory leaks may occur. - The observer instance does not support multi-thread concurrent access and must be created and destroyed in the same thread. |
| [int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)](#oh_pasteboardobserver_destroy) | - | Destroys the OH_PasteboardObserver instance. When you no longer need to listen for clipboard data changes, call this function to destroy the observer object. Before calling this function, ensure that you have called OH_Pasteboard_Unsubscribe to cancel the subscription. |
| [int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)](#oh_pasteboardobserver_setdata) | - | Sets a callback for the pasteboard observer. When an application needs to perform specific operations (such as updating the UI display or synchronizing data to other modules) when the pasteboard data changes, this API is used to set a callback function. After the setting is complete, the callback is triggered when the pasteboard data of the corresponding type changes. The callback is usually executed in the system thread. Therefore, pay attention to thread security. The lifecycle of the callback function must be no shorter than that of the observer. |
| [OH_Pasteboard* OH_Pasteboard_Create()](#oh_pasteboard_create) | - | Creates an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance and a pointer to it. Before accessing or operating the system pasteboard, call this function to create a pasteboard instance. After the instance is created, use it in time. |
| [void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)](#oh_pasteboard_destroy) | - | Destroys the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. When access to the pasteboard is no longer required, destroy the pasteboard instance to release resources. Before destroying the pasteboard instance, ensure that all subscribers have been canceled. |
| [int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)](#oh_pasteboard_subscribe) | - | Subscribes to pasteboard data changes. Typical use scenarios include listening for pasteboard content changes, implementing cross-device pasteboard data synchronization, and updating the UI when the pasteboard content changes. After this function is called, the system notifies the application using the observer callback [Pasteboard_Notify](capi-oh-pasteboard-h.md#pasteboard_notify) when the pasteboard data changes. The application can subscribe to data change events of the local device or a remote device by specifying the event type using **type**.<br> - After this API is called to subscribe to pasteboard change events, you must call {@link OH_Pasteboard_Unsubscribe to unsubscribe from the events when the listening is no longer needed. - The same observer instance and event type must be passed for subscribing to and unsubscribing from pasteboard change events. - If the events are not subscribed from, continuous listening and resource occupation may occur. - The same observer cannot subscribe to the same type of events repeatedly. Otherwise, an error will be returned. - The observer instance cannot be destroyed before the events are unsubscribed from. - The callback is executed in an asynchronous IPC thread. Therefore, pay attention to thread security. |
| [int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)](#oh_pasteboard_unsubscribe) | - | Unsubscribes from pasteboard data changes. Before calling this API, you must call **OH_Pasteboard_Subscribe**<br>to subscribe to pasteboard data changes. Unsubscribe from pasteboard data changes when they are no longer needed to release resources. |
| [bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)](#oh_pasteboard_isremotedata) | - | Checks whether the pasteboard data comes from remote devices. Typical use scenarios include cross-device pasteboard data synchronization, selecting a processing policy based on the data source in distributed scenarios, and implementing security verification of the data source. |
| [int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)](#oh_pasteboard_getdatasource) | - | Obtains the pasteboard data source. This API can be used to identify the data source or control permissions. |
| [bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)](#oh_pasteboard_hastype) | - | Checks whether the pasteboard contains data of the specified type. Typical use scenarios include checking whether the pasteboard data type is supported before pasting, selecting different processing methods based on the data type, and verifying the pasteboard data format. |
| [bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)](#oh_pasteboard_hasdata) | - | Checks whether the pasteboard contains data. Before reading data from the pasteboard, check whether the pasteboard contains data to prevent performing any operation when there is no data. |
| [OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)](#oh_pasteboard_getdata) | - | Obtains data from the pasteboard. After this function is called, the system reads the content from the pasteboard and returns the pointer to an [OH_UdmfData](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) instance. You can use **OH_UdmfData** APIs to parse data. You need to manually release the obtained data object. The delay in obtaining data from the pasteboard is affected by the data volume and network environment. Therefore, calling this API may take a long time. You are advised to call this API in non-UI threads.<br> - If the pasteboard is empty or the data format is not supported, **nullptr** is returned. - The returned **OH_UdmfData** object needs to be released by calling [OH_UdmfData_Destroy](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfdata_destroy). - If a large amount of data is pasted, you are advised to use [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) to obtain the progress. |
| [bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)](#oh_pasteboard_hasremotedata) | - | Checks whether the pasteboard data is on a remote device. Transferring data across devices takes time. If the pasteboard data is on a remote device, do not check for custom data types or read the pasteboard data on the UI thread. |
| [int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)](#oh_pasteboard_setdata) | - | Sets the unified data object in the **OH_Pasteboard** instance. After the data is written successfully, other apps can use the APIs for reading data provided by the system pasteboard to access the data. The size of the unified data object is limited by the capacity of the system pasteboard. After the data is written to the system pasteboard, the lifecycle of the data is managed by the system pasteboard. After this function is called, valid data is written to the system pasteboard, overwriting the previous data. After the data is written successfully, the callback function of all observers that have subscribed to the pasteboard data change event is triggered. Other apps can read the data through the pasteboard APIs.<br> - The size of the serialized data cannot exceed the system capacity, which varies depending on the device and is usually 128 MB. - The write operation will clear all the existing data in the pasteboard. - When a large amount of data needs to be copied, you are advised to use the delayed copy feature to improve performance. |
| [int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)](#oh_pasteboard_cleardata) | - | Clears data from the pasteboard. This API can be used to clear data from the pasteboard, for example, clearing sensitive data when exiting an app. |
| [char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)](#oh_pasteboard_getmimetypes) | - | Obtains the MIME types from the pasteboard. Typical use scenarios include determining the pasteboard data type to select a proper processing method and checking whether the data type is supported before pasting. |
| [uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)](#oh_pasteboard_getchangecount) | - | Obtains the number of pasteboard content changes. Typical use scenarios include determining whether the pasteboard content has changed, implementing incremental pasteboard data synchronization, checking whether the pasteboard content has expired, and optimizing the cache based on the change count. |
| [Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)](#oh_pasteboard_getdataparams_create) | - | Creates a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance and a pointer to it. When an app needs to obtain pasteboard data and monitor the progress (for example, in large file copy scenarios), the app can call [OH_Pasteboard_GetDataParams_SetProgressIndicator](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setprogressindicator), [OH_Pasteboard_GetDataParams_SetDestUri](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setdesturi), and [OH_Pasteboard_GetDataParams_SetFileConflictOptions](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setfileconflictoptions) to configure the progress bar, destination path for file copy, and file conflict handling options. |
| [void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)](#oh_pasteboard_getdataparams_destroy) | - | Destroys the [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. After this function is called, the **Pasteboard_GetDataParams** instance is released, and the parameter configuration becomes invalid. If the parameter object is destroyed when the pasted data is obtained, the progress callback may fail to be triggered. When the **Pasteboard_GetDataParams** instance is no longer needed, destroy it to release resources.<br> - This API must be used in pairs with [OH_Pasteboard_GetDataParams_Create](#oh_pasteboard_getdataparams_create). - The parameter object must be destroyed after [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) is called. - This API cannot be called in the progress callback function. |
| [void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params, Pasteboard_ProgressIndicator progressIndicator)](#oh_pasteboard_getdataparams_setprogressindicator) | - | Sets a progress indicator in [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md). You can use the default progress indicator as required. Typical use scenarios: Set **Pasteboard_ProgressIndicator** to **PASTEBOARD_DEFAULT** to display the default progress bar when large files need to be pasted, and to **PASTEBOARD_NONE** when a custom progress UI or silent paste is required. |
| [void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)](#oh_pasteboard_getdataparams_setdesturi) | - | Sets the destination URI for copying files. If file processing is not supported, you do not need to set this parameter. If complex file processing policies are involved or multi-path file storage is required, you are advised to leave this parameter unspecified and let the application handle file copying. This parameter is used to copy a file from the pasteboard to a specified destination URI. |
| [void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params, Pasteboard_FileConflictOptions option)](#oh_pasteboard_getdataparams_setfileconflictoptions) | - | Sets the options used to resolve file copy conflicts in a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. When calling [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress), pass the [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance with the options used to resolve file copy conflicts as a parameter. When copying a file, if a file with the same name already exists in the destination directory, you need to set a conflict handling policy.<br> - **PASTEBOARD_OVERWRITE**: Select this parameter if you want to overwrite the existing file with the latest file content. - **PASTEBOARD_SKIP**: Select this parameter if you want to retain the original file. |
| [void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params, const OH_Pasteboard_ProgressListener listener)](#oh_pasteboard_getdataparams_setprogresslistener) | - | Sets a progress listener in a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. This callback is used to receive progress updates when you need to customize a progress display UI or silently process pasteboard tasks in the background. |
| [int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)](#oh_pasteboard_progressinfo_getprogress) | - | Obtains the paste progress in a [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md) instance. Typical use scenarios include updating the UI progress bar in a custom progress callback, monitoring the pasting progress of large files, and adjusting the service logic based on the progress. |
| [void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)](#oh_pasteboard_progresscancel) | - | Defines a function for canceling the ongoing paste operation. This function is used to interrupt data transfer during the execution of [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress). After this function is called, the current paste operation will be terminated. The transferred data may be retained or cleared, depending on the specific operation status. If you need to obtain the pasteboard data after the operation is canceled, call [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) again. This function can be used when the user cancels the operation, the transfer is interrupted due to an error, or the paste operation times out.<br> - The cancellation operation is asynchronous and may not take effect immediately. - The cancellation operation is irreversible. Once the operation is canceled, you need to restart the pasting process if you want to obtain the pasteboard data. |
| [OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)](#oh_pasteboard_getdatawithprogress) | - | Obtains the pasteboard data and paste progress. Folders cannot be copied. After this function is called, the system starts to obtain data from the system pasteboard. If the pasteboard data comes from a remote device or contains a large number of files, the progress is reported through the [OH_Pasteboard_ProgressListener](capi-oh-pasteboard-h.md#oh_pasteboard_progresslistener) callback. After the data transfer is complete, the pointer to the unified data object is returned. The entire process may take a long time. You are advised to call this function in a non-UI thread. |
| [void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (\*callback)(int errorCode))](#oh_pasteboard_syncdelayeddataasync) | - | Syncs all delayed data from the app to the pasteboard. Delayed data refers to the data transfer mechanism of writing data to the pasteboard first and then loading data in delayed mode as required. Use this API together with [OH_UdmfRecordProvider_SetData](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfrecordprovider_setdata). When all delayed data is synced, an asynchronous callback is used to notify the app. When the application uses the delayed copy feature, only the data types supported by the application are written to the pasteboard. Before the application exits, it should call the [OH_Pasteboard_SetData](capi-oh-pasteboard-h.md#oh_pasteboard_setdata) API to submit all copied data or call the **OH_Pasteboard_SyncDelayedDataAsync** API to notify the pasteboard to obtain all data. The application can exit only after the data sync is complete. Otherwise, other applications may fail to obtain the data.<br> > **NOTE**<br>> - Calling this API prolongs the exit process. You are advised to directly set data to the pasteboard instead of calling the [OH_UdmfRecordProvider_SetData](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfrecordprovider_setdata) and **OH_Pasteboard_SyncDelayedDataAsync** APIs. |

## Enum type description

### Pasteboard_NotifyType

```c
enum Pasteboard_NotifyType
```

**Description**

Enumerates the data change types of the pasteboard. This enum is used to determine whether the pasteboard data change is from the local device or a remote device.

<!--Device-enum Pasteboard_NotifyType--><!--Device-enum Pasteboard_NotifyType-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

| Enum item | Description |
| -- | -- |
| NOTIFY_LOCAL_DATA_CHANGE = 1 | The pasteboard data of the local device is changed.<br><!--Device-NOTIFY_LOCAL_DATA_CHANGE = 1--><!--Device-NOTIFY_LOCAL_DATA_CHANGE = 1-End--> |
| NOTIFY_REMOTE_DATA_CHANGE = 2 | The pasteboard data of a non-local device on the network is changed.<br><!--Device-NOTIFY_REMOTE_DATA_CHANGE = 2--><!--Device-NOTIFY_REMOTE_DATA_CHANGE = 2-End--> |

### Pasteboard_FileConflictOptions

```c
enum Pasteboard_FileConflictOptions
```

**Description**

Enumerates the options used to resolve file copy conflicts. When a file with the same name already exists in the destination directory, the pasteboard handles the conflict based on the specified policy.

<!--Device-enum Pasteboard_FileConflictOptions--><!--Device-enum Pasteboard_FileConflictOptions-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

| Enum item | Description |
| -- | -- |
| PASTEBOARD_OVERWRITE = 0 | Overwrites the file with the same name in the destination directory.<br><!--Device-PASTEBOARD_OVERWRITE = 0--><!--Device-PASTEBOARD_OVERWRITE = 0-End--> |
| PASTEBOARD_SKIP = 1 | Skips the file if there is a file with the same name in the destination directory.<br><!--Device-PASTEBOARD_SKIP = 1--><!--Device-PASTEBOARD_SKIP = 1-End--> |

### Pasteboard_ProgressIndicator

```c
enum Pasteboard_ProgressIndicator
```

**Description**

Enumerates the progress indicator options. You can use the default progress indicator as required.

<!--Device-enum Pasteboard_ProgressIndicator--><!--Device-enum Pasteboard_ProgressIndicator-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

| Enum item | Description |
| -- | -- |
| PASTEBOARD_NONE = 0 | The default progress indicator is not used.<br><!--Device-PASTEBOARD_NONE = 0--><!--Device-PASTEBOARD_NONE = 0-End--> |
| PASTEBOARD_DEFAULT = 1 | The default progress indicator is used.<br><!--Device-PASTEBOARD_DEFAULT = 1--><!--Device-PASTEBOARD_DEFAULT = 1-End--> |


## Function description

### OH_Pasteboard_ProgressListener()

```c
typedef void (*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)
```

**Description**

Defines a callback to notify the app about the progress of the pasting task when the default progress indicator is not used. This callback is used to support the implementation of a custom progress UI.

<!--Device-typedef void (*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)--><!--Device-typedef void (*OH_Pasteboard_ProgressListener)(Pasteboard_ProgressInfo* progressInfo)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md)* progressInfo | Progress information. This information is reported only when [Pasteboard_ProgressIndicator](capi-oh-pasteboard-h.md#pasteboard_progressindicator) is set to **PASTEBOARD_NONE**. |

### Pasteboard_Notify()

```c
typedef void (*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)
```

**Description**

Defines a callback to be invoked when the pasteboard content changes. Implement this callback when you need to execute app-specific logic upon pasteboard content changes.

<!--Device-typedef void (*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)--><!--Device-typedef void (*Pasteboard_Notify)(void* context, Pasteboard_NotifyType type)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | Context, which is passed in by the [OH_PasteboardObserver_SetData](capi-oh-pasteboard-h.md#oh_pasteboardobserver_setdata) function. |
| [Pasteboard_NotifyType](capi-oh-pasteboard-h.md#pasteboard_notifytype) type | Data change type. For details, see [Pasteboard_NotifyType](capi-oh-pasteboard-h.md#pasteboard_notifytype). |

### Pasteboard_Finalize()

```c
typedef void (*Pasteboard_Finalize)(void* context)
```

**Description**

Defines a callback to be invoked to release the context when the pasteboard observer object is destroyed. If resources are dynamically allocated in the **Pasteboard_Notify** callback, you need to implement this callback to release the resources.

<!--Device-typedef void (*Pasteboard_Finalize)(void* context)--><!--Device-typedef void (*Pasteboard_Finalize)(void* context)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* context | Pointer to the context to release. If **context** points to dynamic memory or resources that need to be manually released, release them in the callback. If **context** points to static memory or resources that do not need to be managed, you do not need to perform any operation in the callback. |

### OH_PasteboardObserver_Create()

```c
OH_PasteboardObserver* OH_PasteboardObserver_Create()
```

**Description**

Creates an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance and a pointer to it. Typical use scenarios include listening for pasteboard content changes to implement data synchronization and triggering service logic when the pasteboard content is updated. After this function is called, the system initializes a **PasteboardObserver** instance and returns a pointer to it. After the instance is created, you need to call [OH_PasteboardObserver_SetData](capi-oh-pasteboard-h.md#oh_pasteboardobserver_setdata) to set the callback function and then call [OH_Pasteboard_Subscribe](capi-oh-pasteboard-h.md#oh_pasteboard_subscribe) to subscribe to pasteboard change events.<br>
- The caller must call [OH_PasteboardObserver_Destroy](#oh_pasteboardobserver_destroy) to release resources when the pasteboard data changes do not need to be listened for. Otherwise, memory leaks may occur.
- The observer instance does not support multi-thread concurrent access and must be created and destroyed in the same thread.

<!--Device-OH_PasteboardObserver* OH_PasteboardObserver_Create()--><!--Device-OH_PasteboardObserver* OH_PasteboardObserver_Create()-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_PasteboardObserver*](capi-pasteboard-oh-pasteboardobserver.md) | Returns a pointer to the [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance created if the operation is successful; returns **nullptr** otherwise. If this pointer is no longer required, use [OH_PasteboardObserver_Destroy](capi-oh-pasteboard-h.md#oh_pasteboardobserver_destroy) to destroy it. Otherwise, memory leak may occur. |

**Reference**:

OH_PasteboardObserver


### OH_PasteboardObserver_Destroy()

```c
int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)
```

**Description**

Destroys the OH_PasteboardObserver instance. When you no longer need to listen for clipboard data changes, call this function to destroy the observer object. Before calling this function, ensure that you have called OH_Pasteboard_Unsubscribe to cancel the subscription.

<!--Device-int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)--><!--Device-int OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_PasteboardObserver
PASTEBOARD_ErrCode


### OH_PasteboardObserver_SetData()

```c
int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)
```

**Description**

Sets a callback for the pasteboard observer. When an application needs to perform specific operations (such as updating the UI display or synchronizing data to other modules) when the pasteboard data changes, this API is used to set a callback function. After the setting is complete, the callback is triggered when the pasteboard data of the corresponding type changes. The callback is usually executed in the system thread. Therefore, pay attention to thread security. The lifecycle of the callback function must be no shorter than that of the observer.

<!--Device-int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)--><!--Device-int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. |
| void* context | Pointer to the context data, which is passed to [Pasteboard_Notify](capi-oh-pasteboard-h.md#pasteboard_notify) as the first parameter. |
| [const Pasteboard_Notify](capi-oh-pasteboard-h.md#pasteboard_notify) callback | Callback for data changes, which is triggered when the pasteboard data changes. For details, see [Pasteboard_Notify](capi-oh-pasteboard-h.md#pasteboard_notify). |
| [const Pasteboard_Finalize](capi-oh-pasteboard-h.md#pasteboard_finalize) finalize | Optional callback, which can be used to release context data when the pasteboard observer is destroyed. The default value is **nullptr**, indicating that no release operation is performed. For details, see [Pasteboard_Finalize](capi-oh-pasteboard-h.md#pasteboard_finalize). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_PasteboardObserver
Pasteboard_Notify
PASTEBOARD_ErrCode


### OH_Pasteboard_Create()

```c
OH_Pasteboard* OH_Pasteboard_Create()
```

**Description**

Creates an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance and a pointer to it. Before accessing or operating the system pasteboard, call this function to create a pasteboard instance. After the instance is created, use it in time.

<!--Device-OH_Pasteboard* OH_Pasteboard_Create()--><!--Device-OH_Pasteboard* OH_Pasteboard_Create()-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Pasteboard*](capi-pasteboard-oh-pasteboard.md) | Returns a pointer to the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance created if the operation is successful; returns **nullptr** otherwise. If this pointer is no longer required, use [OH_Pasteboard_Destroy](capi-oh-pasteboard-h.md#oh_pasteboard_destroy) to destroy it. Otherwise, memory leaks may occur. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_Destroy()

```c
void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)
```

**Description**

Destroys the [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. When access to the pasteboard is no longer required, destroy the pasteboard instance to release resources. Before destroying the pasteboard instance, ensure that all subscribers have been canceled.

<!--Device-void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)--><!--Device-void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_Subscribe()

```c
int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)
```

**Description**

Subscribes to pasteboard data changes. Typical use scenarios include listening for pasteboard content changes, implementing cross-device pasteboard data synchronization, and updating the UI when the pasteboard content changes. After this function is called, the system notifies the application using the observer callback [Pasteboard_Notify](capi-oh-pasteboard-h.md#pasteboard_notify) when the pasteboard data changes. The application can subscribe to data change events of the local device or a remote device by specifying the event type using **type**.<br>
- After this API is called to subscribe to pasteboard change events, you must call {@link OH_Pasteboard_Unsubscribe to unsubscribe from the events when the listening is no longer needed.
- The same observer instance and event type must be passed for subscribing to and unsubscribing from pasteboard change events.
- If the events are not subscribed from, continuous listening and resource occupation may occur.
- The same observer cannot subscribe to the same type of events repeatedly. Otherwise, an error will be returned.
- The observer instance cannot be destroyed before the events are unsubscribed from.
- The callback is executed in an asynchronous IPC thread. Therefore, pay attention to thread security.

<!--Device-int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)--><!--Device-int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int type | Subscribed data change type of the pasteboard. For details, see [Pasteboard_NotifyType](capi-oh-pasteboard-h.md#pasteboard_notifytype). |
| [const OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. It specifies the callback to be invoked when the pasteboard data changes. For details, see [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_Pasteboard
OH_PasteboardObserver
Pasteboard_NotifyType
PASTEBOARD_ErrCode


### OH_Pasteboard_Unsubscribe()

```c
int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)
```

**Description**

Unsubscribes from pasteboard data changes. Before calling this API, you must call **OH_Pasteboard_Subscribe**<br>to subscribe to pasteboard data changes. Unsubscribe from pasteboard data changes when they are no longer needed to release resources.

<!--Device-int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)--><!--Device-int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int type | Type of pasteboard data change subscribed to, which must be the same as the type value passed when the application subscribes to the change events. For details, see [Pasteboard_NotifyType](capi-oh-pasteboard-h.md#pasteboard_notifytype). |
| [const OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)* observer | Pointer to an [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md) instance. It specifies the callback to be invoked when the pasteboard data changes. For details, see [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_Pasteboard
OH_PasteboardObserver
Pasteboard_NotifyType
PASTEBOARD_ErrCode


### OH_Pasteboard_IsRemoteData()

```c
bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the pasteboard data comes from remote devices. Typical use scenarios include cross-device pasteboard data synchronization, selecting a processing policy based on the data source in distributed scenarios, and implementing security verification of the data source.

<!--Device-bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)--><!--Device-bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the data comes from a remote device. The value **true** means the data is from a remote device; **false** means the data is from the local device. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_GetDataSource()

```c
int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)
```

**Description**

Obtains the pasteboard data source. This API can be used to identify the data source or control permissions.

<!--Device-int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)--><!--Device-int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| char* source | Pointer to the pasteboard data source instance. You need to allocate the memory for the pointer before calling this API. The recommended size is 128 bytes. |
| unsigned int len | Memory length allocated for the source length. The value must be greater than or equal to the length of the data source string (including the string terminator). The recommended length is 128 bytes. If the memory length is insufficient, the error code **ERR_INVALID_PARAMETER** is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

[OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)
PASTEBOARD_ErrCode


### OH_Pasteboard_HasType()

```c
bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)
```

**Description**

Checks whether the pasteboard contains data of the specified type. Typical use scenarios include checking whether the pasteboard data type is supported before pasting, selecting different processing methods based on the data type, and verifying the pasteboard data format.

<!--Device-bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)--><!--Device-bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| const char* type | Data type to be checked, which includes the basic data types and custom data types. The options of the basic data types are as follows: **"text/plain"**, **"text/html"**, **"text/uri"**, **"text/want"**, and **"pixelMap"**. For details, see Macros. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the pasteboard contains data of the specified type. The value **true** means the pasteboard contains data of the specified type; the value **false** means the opposite. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_HasData()

```c
bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the pasteboard contains data. Before reading data from the pasteboard, check whether the pasteboard contains data to prevent performing any operation when there is no data.

<!--Device-bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)--><!--Device-bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns a Boolean value indicating whether the pasteboard contains data. The value **true** means the pasteboard contains data; the value **false** means the opposite. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_GetData()

```c
OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)
```

**Description**

Obtains data from the pasteboard. After this function is called, the system reads the content from the pasteboard and returns the pointer to an [OH_UdmfData](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) instance. You can use **OH_UdmfData** APIs to parse data. You need to manually release the obtained data object. The delay in obtaining data from the pasteboard is affected by the data volume and network environment. Therefore, calling this API may take a long time. You are advised to call this API in non-UI threads.<br>
- If the pasteboard is empty or the data format is not supported, **nullptr** is returned.
- The returned **OH_UdmfData** object needs to be released by calling [OH_UdmfData_Destroy](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfdata_destroy).
- If a large amount of data is pasted, you are advised to use [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) to obtain the progress.

<!--Device-OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)--><!--Device-OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Required permission**: ohos.permission.READ_PASTEBOARD

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| int* status | Output parameter, indicating the error code of the operation. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfData*](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) | Returns the pointer to an [OH_UdmfData](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) instance obtained if the operation is successful; returns a null pointer otherwise. |

**Reference**:

OH_Pasteboard
OH_UdmfData
PASTEBOARD_ErrCode


### OH_Pasteboard_HasRemoteData()

```c
bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)
```

**Description**

Checks whether the pasteboard data is on a remote device. Transferring data across devices takes time. If the pasteboard data is on a remote device, do not check for custom data types or read the pasteboard data on the UI thread.

<!--Device-bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)--><!--Device-bool OH_Pasteboard_HasRemoteData(OH_Pasteboard* pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the check result. The value **true** indicates that the pasteboard data is on a remote device, and **false** indicates the opposite. Default value: **false**. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_SetData()

```c
int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)
```

**Description**

Sets the unified data object in the **OH_Pasteboard** instance. After the data is written successfully, other apps can use the APIs for reading data provided by the system pasteboard to access the data. The size of the unified data object is limited by the capacity of the system pasteboard. After the data is written to the system pasteboard, the lifecycle of the data is managed by the system pasteboard. After this function is called, valid data is written to the system pasteboard, overwriting the previous data. After the data is written successfully, the callback function of all observers that have subscribed to the pasteboard data change event is triggered. Other apps can read the data through the pasteboard APIs.<br>
- The size of the serialized data cannot exceed the system capacity, which varies depending on the device and is usually 128 MB.
- The write operation will clear all the existing data in the pasteboard.
- When a large amount of data needs to be copied, you are advised to use the delayed copy feature to improve performance.

<!--Device-int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)--><!--Device-int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| [OH_UdmfData](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md)* data | Pointer to an [OH_UdmfData](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_Pasteboard
OH_UdmfData
PASTEBOARD_ErrCode


### OH_Pasteboard_ClearData()

```c
int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)
```

**Description**

Clears data from the pasteboard. This API can be used to clear data from the pasteboard, for example, clearing sensitive data when exiting an app.

<!--Device-int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)--><!--Device-int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). Returns **ERR_OK** if the operation is successful. Returns **ERR_INVALID_PARAMETER** if an invalid parameter is passed in. |

**Reference**:

OH_Pasteboard
PASTEBOARD_ErrCode


### OH_Pasteboard_GetMimeTypes()

```c
char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)
```

**Description**

Obtains the MIME types from the pasteboard. Typical use scenarios include determining the pasteboard data type to select a proper processing method and checking whether the data type is supported before pasting.

<!--Device-char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)--><!--Device-char **OH_Pasteboard_GetMimeTypes(OH_Pasteboard *pasteboard, unsigned int *count)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) *pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| unsigned int *count | Pointer to the number of MIME types obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| char ** | Returns a pointer to an array of all data records on the pasteboard of the MIME type if the operation is successful; returns **nullptr** otherwise. The array size is specified by the **count** parameter. |

**Reference**:

OH_Pasteboard


### OH_Pasteboard_GetChangeCount()

```c
uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)
```

**Description**

Obtains the number of pasteboard content changes. Typical use scenarios include determining whether the pasteboard content has changed, implementing incremental pasteboard data synchronization, checking whether the pasteboard content has expired, and optimizing the cache based on the change count.

<!--Device-uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)--><!--Device-uint32_t OH_Pasteboard_GetChangeCount(OH_Pasteboard *pasteboard)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) *pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the number of pasteboard content changes if this API is called successfully; otherwise, returns **0**. |

### OH_Pasteboard_GetDataParams_Create()

```c
Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)
```

**Description**

Creates a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance and a pointer to it. When an app needs to obtain pasteboard data and monitor the progress (for example, in large file copy scenarios), the app can call [OH_Pasteboard_GetDataParams_SetProgressIndicator](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setprogressindicator), [OH_Pasteboard_GetDataParams_SetDestUri](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setdesturi), and [OH_Pasteboard_GetDataParams_SetFileConflictOptions](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_setfileconflictoptions) to configure the progress bar, destination path for file copy, and file conflict handling options.

<!--Device-Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)--><!--Device-Pasteboard_GetDataParams *OH_Pasteboard_GetDataParams_Create(void)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Returns**:

| Type | Description |
| -- | -- |
| [Pasteboard_GetDataParams *](capi-pasteboard-pasteboard-getdataparams.md) | Returns a pointer to the [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance created if the operation is successful; returns **nullptr** otherwise. If this pointer is no longer required, use [OH_Pasteboard_GetDataParams_Destroy](capi-oh-pasteboard-h.md#oh_pasteboard_getdataparams_destroy) to destroy it. Otherwise, memory leaks may occur. |

**Reference**:

Pasteboard_GetDataParams


### OH_Pasteboard_GetDataParams_Destroy()

```c
void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)
```

**Description**

Destroys the [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. After this function is called, the **Pasteboard_GetDataParams** instance is released, and the parameter configuration becomes invalid. If the parameter object is destroyed when the pasted data is obtained, the progress callback may fail to be triggered. When the **Pasteboard_GetDataParams** instance is no longer needed, destroy it to release resources.<br>
- This API must be used in pairs with [OH_Pasteboard_GetDataParams_Create](#oh_pasteboard_getdataparams_create).
- The parameter object must be destroyed after [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) is called.
- This API cannot be called in the progress callback function.

<!--Device-void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)--><!--Device-void OH_Pasteboard_GetDataParams_Destroy(Pasteboard_GetDataParams* params)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |

**Reference**:

Pasteboard_GetDataParams


### OH_Pasteboard_GetDataParams_SetProgressIndicator()

```c
void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params, Pasteboard_ProgressIndicator progressIndicator)
```

**Description**

Sets a progress indicator in [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md). You can use the default progress indicator as required. Typical use scenarios: Set **Pasteboard_ProgressIndicator** to **PASTEBOARD_DEFAULT** to display the default progress bar when large files need to be pasted, and to **PASTEBOARD_NONE** when a custom progress UI or silent paste is required.

<!--Device-void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params, Pasteboard_ProgressIndicator progressIndicator)--><!--Device-void OH_Pasteboard_GetDataParams_SetProgressIndicator(Pasteboard_GetDataParams* params, Pasteboard_ProgressIndicator progressIndicator)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |
| [Pasteboard_ProgressIndicator](capi-oh-pasteboard-h.md#pasteboard_progressindicator) progressIndicator | Progress indicator to set. |

**Reference**:

Pasteboard_GetDataParams
Pasteboard_ProgressIndicator


### OH_Pasteboard_GetDataParams_SetDestUri()

```c
void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)
```

**Description**

Sets the destination URI for copying files. If file processing is not supported, you do not need to set this parameter. If complex file processing policies are involved or multi-path file storage is required, you are advised to leave this parameter unspecified and let the application handle file copying. This parameter is used to copy a file from the pasteboard to a specified destination URI.

<!--Device-void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)--><!--Device-void OH_Pasteboard_GetDataParams_SetDestUri(Pasteboard_GetDataParams* params, const char* destUri, uint32_t destUriLen)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |
| const char* destUri | Destination URI of the copied file. The path must be an absolute path, and the app must have the read and write permissions on the path. |
| uint32_t destUriLen | Length of the destination URI (including a string terminator) of the copied file, in bytes. The value must be equal to the actual length of the string pointed to by **destUri**. If the input value is **0** or does not match the actual length, the API call fails. |

**Reference**:

Pasteboard_GetDataParams


### OH_Pasteboard_GetDataParams_SetFileConflictOptions()

```c
void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params, Pasteboard_FileConflictOptions option)
```

**Description**

Sets the options used to resolve file copy conflicts in a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. When calling [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress), pass the [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance with the options used to resolve file copy conflicts as a parameter. When copying a file, if a file with the same name already exists in the destination directory, you need to set a conflict handling policy.<br>
- **PASTEBOARD_OVERWRITE**: Select this parameter if you want to overwrite the existing file with the latest file content.
- **PASTEBOARD_SKIP**: Select this parameter if you want to retain the original file.

<!--Device-void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params, Pasteboard_FileConflictOptions option)--><!--Device-void OH_Pasteboard_GetDataParams_SetFileConflictOptions(Pasteboard_GetDataParams* params, Pasteboard_FileConflictOptions option)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |
| [Pasteboard_FileConflictOptions](capi-oh-pasteboard-h.md#pasteboard_fileconflictoptions) option | Options used to resolve file copy conflicts. The default value is **PASTEBOARD_OVERWRITE**. |

**Reference**:

Pasteboard_GetDataParams Pasteboard_FileConflictOptions


### OH_Pasteboard_GetDataParams_SetProgressListener()

```c
void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params, const OH_Pasteboard_ProgressListener listener)
```

**Description**

Sets a progress listener in a [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md) instance. This callback is used to receive progress updates when you need to customize a progress display UI or silently process pasteboard tasks in the background.

<!--Device-void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params, const OH_Pasteboard_ProgressListener listener)--><!--Device-void OH_Pasteboard_GetDataParams_SetProgressListener(Pasteboard_GetDataParams* params, const OH_Pasteboard_ProgressListener listener)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |
| [const OH_Pasteboard_ProgressListener](capi-oh-pasteboard-h.md#oh_pasteboard_progresslistener) listener | Progress listener. This parameter is valid only when progressIndicator is set to **PASTEBOARD_NONE**. This parameter can be set to **NULL**, indicating that no progress callback is required. |

**Reference**:

Pasteboard_GetDataParams
OH_Pasteboard_ProgressListener


### OH_Pasteboard_ProgressInfo_GetProgress()

```c
int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)
```

**Description**

Obtains the paste progress in a [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md) instance. Typical use scenarios include updating the UI progress bar in a custom progress callback, monitoring the pasting progress of large files, and adjusting the service logic based on the progress.

<!--Device-int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)--><!--Device-int OH_Pasteboard_ProgressInfo_GetProgress(Pasteboard_ProgressInfo* progressInfo)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md)* progressInfo | Pointer to a [Pasteboard_ProgressInfo](capi-pasteboard-pasteboard-progressinfo.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Pasting progress, in percentage. The value ranges from 0 to 100. |

**Reference**:

Pasteboard_ProgressInfo


### OH_Pasteboard_ProgressCancel()

```c
void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)
```

**Description**

Defines a function for canceling the ongoing paste operation. This function is used to interrupt data transfer during the execution of [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress). After this function is called, the current paste operation will be terminated. The transferred data may be retained or cleared, depending on the specific operation status. If you need to obtain the pasteboard data after the operation is canceled, call [OH_Pasteboard_GetDataWithProgress](capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) again. This function can be used when the user cancels the operation, the transfer is interrupted due to an error, or the paste operation times out.<br>
- The cancellation operation is asynchronous and may not take effect immediately.
- The cancellation operation is irreversible. Once the operation is canceled, you need to restart the pasting process if you want to obtain the pasteboard data.

<!--Device-void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)--><!--Device-void OH_Pasteboard_ProgressCancel(Pasteboard_GetDataParams* params)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |

**Reference**:

Pasteboard_GetDataParams


### OH_Pasteboard_GetDataWithProgress()

```c
OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)
```

**Description**

Obtains the pasteboard data and paste progress. Folders cannot be copied. After this function is called, the system starts to obtain data from the system pasteboard. If the pasteboard data comes from a remote device or contains a large number of files, the progress is reported through the [OH_Pasteboard_ProgressListener](capi-oh-pasteboard-h.md#oh_pasteboard_progresslistener) callback. After the data transfer is complete, the pointer to the unified data object is returned. The entire process may take a long time. You are advised to call this function in a non-UI thread.

<!--Device-OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)--><!--Device-OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Required permission**: ohos.permission.READ_PASTEBOARD

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| [Pasteboard_GetDataParams](capi-pasteboard-pasteboard-getdataparams.md)* params | Pointer to a **Pasteboard_GetDataParams** instance. |
| int* status | Output parameter, indicating the error code of the operation. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UdmfData*](../../apis-arkdata/c-apis/capi-udmf-oh-udmfdata.md) | Returns a pointer to the **OH_UdmfData** instance obtained if the operation is successful; returns a null pointer otherwise. |

**Reference**:

OH_Pasteboard OH_PasteData PASTEBOARD_ErrCode


### OH_Pasteboard_SyncDelayedDataAsync()

```c
void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode))
```

**Description**

Syncs all delayed data from the app to the pasteboard. Delayed data refers to the data transfer mechanism of writing data to the pasteboard first and then loading data in delayed mode as required. Use this API together with [OH_UdmfRecordProvider_SetData](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfrecordprovider_setdata). When all delayed data is synced, an asynchronous callback is used to notify the app. When the application uses the delayed copy feature, only the data types supported by the application are written to the pasteboard. Before the application exits, it should call the [OH_Pasteboard_SetData](capi-oh-pasteboard-h.md#oh_pasteboard_setdata) API to submit all copied data or call the **OH_Pasteboard_SyncDelayedDataAsync** API to notify the pasteboard to obtain all data. The application can exit only after the data sync is complete. Otherwise, other applications may fail to obtain the data.<br>
> **NOTE**
> - Calling this API prolongs the exit process. You are advised to directly set data to the pasteboard instead of calling the [OH_UdmfRecordProvider_SetData](../../apis-arkdata/c-apis/capi-udmf-h.md#oh_udmfrecordprovider_setdata) and **OH_Pasteboard_SyncDelayedDataAsync** APIs.

<!--Device-void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode))--><!--Device-void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode))-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_Pasteboard* pasteboard | Pointer to an [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md) instance. |
| void (*callback)(int errorCode) | Pointer to the callback invoked when data sync is complete. **errorCode** indicates the result of the sync task. For details about the error codes, see [PASTEBOARD_ErrCode](capi-oh-pasteboard-err-code-h.md#pasteboard_errcode). |


