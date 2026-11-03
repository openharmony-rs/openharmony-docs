# content_embed_proxy.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Provides client apps with APIs for querying the OE extension information registered by server apps, data structures for interacting with the server OE extension object, and related operation APIs. This module is applicable to scenarios where client apps need to query the OE extension information registered by server apps and interact with the server OE extension object. For example, APIs provided by this module can be used to create a proxy, register a callback, edit a document, or obtain a snapshot.

**File to include:** <ContentEmbedKit/content_embed/content_embed_proxy.h>

**Library:** libcontent_embed_ndk.so

**System capability:** SystemCapability.ContentEmbed.ObjectEditor

**Since:** 24

**Related module:** [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | Defines the **ContentEmbed_Info** struct. You can use [OH_ContentEmbed_GetContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_getcontentembedinfo) to query all OE documents registered by server apps, use [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo) to obtain the number of queried [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances, and use [OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo) to obtain the instance at the specified index position.|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | Defines the **ContentEmbed_Format** struct, which contains information about the OE document registered by the server app OE extension. Specifically, you can use [OH_ContentEmbed_GetOEidFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getoeidfromformat) to obtain the OEID, [OH_ContentEmbed_GetNameAndDescriptionFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getnameanddescriptionfromformat) to obtain the name and description, [OH_ContentEmbed_GetIconFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_geticonfromformat) to obtain the icon, and [OH_ContentEmbed_GetFileNameExtensionsFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getfilenameextensionsfromformat) to obtain the file name extensions.|
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | Defines the **ContentEmbed_ExtensionProxy** struct. This struct points to the program object (client OE object for short) that encapsulates the document embedding and editing functions of the OE document on the client. In the OE document embedding and editing scenarios, this struct serves as the handle to the client OE object and is used to call APIs related to document embedding and editing. You can use [OH_ContentEmbed_CreateExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_createextensionproxy) to create a client OE object, use [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish communication with the server, use [OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot) to obtain the snapshot of the OE document, and use [OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit) to implement the editing function. After the communication is complete, use [OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork) to terminate the connection and call [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to destroy the instance.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines the struct of an OE document. This struct encapsulates the metadata, content, and storage structure of an embedded document. It is used to manage the data of embedded documents in a unified manner within an app, facilitating access, parsing, and storage of the embedded documents.<br>You can select a method based on the data source:<br>Use [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid) if you have the OEID.<br>Use [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile) if you have the source file and need to embed or link it.<br>Use [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) if you have a saved OE file.|
| [ContentEmbed_Capability](capi-contentembed-contentembed-capability.md) | ContentEmbed_Capability | Defines the **ContentEmbed_Capability** struct.|

### Macros

| Name| Description|
| -- | -- |
| MAX_NAME_LENGTH (1 * 1024) | Defines the maximum number of characters allowed for the name field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since:** 24|
| MAX_DESCRIPTION_LENGTH (1 * 1024) | Defines the maximum number of characters allowed for the description field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since:** 24|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)](#oh_contentembed_createcontentembedinfo) | - | Creates a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br>You can destroy the instance by calling [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)](#oh_contentembed_destroycontentembedinfo) | - | Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the locale settings. Call this method when an app needs to query the registered OE extension formats on the device.<br>Before calling this method, create an instance using [OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo). After calling this method, you can traverse the format information using [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo) and [OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br>You can destroy an instance by calling [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | Destroys a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | Obtains a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and locale settings. Call this method when an app needs to obtain the localized format of a specific OE extension based on the known OEID. Before calling this method, create an instance by calling [OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | Obtains the OEID of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | Obtains the localized display name and description of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | Obtains the file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br>You can destroy the instance by calling[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks. After the instance is created, its lifecycle is managed by the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. You need to destroy the instance by calling [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy). Do not call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) separately to destroy the instance. Otherwise, the instance will be released repeatedly.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. This API can also be called to destroy the [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance associated during proxy creation. After the instance is destroyed, the document pointer obtained by calling [OH_ContentEmbed_Proxy_GetDocument](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getdocument) becomes invalid. The proxy cannot be destroyed when it is dispatching a callback.|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | Defines the callback function for notifying the client when the OE document is updated.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | Defines the callback function for notifying the client when an OE document error occurs.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | Defines the callback function for notifying the client when the editing of an OE document is complete.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | Defines the callback function for notifying the client when the OE extension is stopped.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | Registers the callback function for OE document update with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | Registers the callback function for OE document errors with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | Registers the callback function for OE document editing completion with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | Registers the callback function for OE extension stop with the client OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | Connects to the server OE extension and establishes a communication channel with the OE extension. Before calling this API, register the necessary client callback functions by calling [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc), [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc), [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc), and [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc). This method is used to establish a communication channel. If communication is not required, call the [OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork) disconnect the channel.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | Disconnects the communication channel with the OE extension. This method must be called after a communication channel is established by calling [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to disconnect the established connection.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | Obtains the snapshot image of the current OE document from the client OE object for preview or thumbnail display. You must call [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish a communication channel with the OE extension before obtaining the snapshot. It is recommended that you call [OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability) to check whether the OE extension instance on the server supports the snapshot capability before calling this method.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | Requests the OE Extension instance to enter edit mode by the client OE object. You must call [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish a communication channel with the OE extension instance first. Otherwise, the request will fail. It is recommended that you call [OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability) to check whether the OE extension instance on the server supports the editing capability before calling this method.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | Queries the current editing state and modification status of an OE document in the OE extension instance on the server.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | Obtains the capabilities of the OE extension instance on the server. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). This API is used to check whether the server supports the corresponding capabilities before calling [OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot) or [OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | Obtains the OE document object associated with the client OE object.<br>The OE document object is created by calling [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile).<br>The lifecycle of this document object is managed by the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. You need to destroy the instance by calling [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy). Do not call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) separately to destroy the instance. Otherwise, the instance will be released repeatedly.|

## Function Description

### OH_ContentEmbed_CreateContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)
```

**Description**

Creates a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br>You can destroy the instance by calling [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) **info |  Pointer to the newly created [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_DestroyContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)
```

**Description**

Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**Description**

Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the locale settings. Call this method when an app needs to query the registered OE extension formats on the device.<br>Before calling this method, create an instance using [OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo). After calling this method, you can traverse the format information using [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo) and [OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo).

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| const char *locale | [Locale ID](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. If the parameter is not specified, the system locale is used by default.|
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info |  Pointer to the **ContentEmbed_Info** object. This is an output parameter. You need to create an instance by calling [OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo) first.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetFormatCountFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)
```

**Description**

Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|
| uint32_t *count |  Number of stored [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetFormatFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)
```

**Description**

Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|
| uint32_t index | Index of the element to be obtained, starting from 0. The value range is [0, **count** – 1], where **count** can be obtained through [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo).|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format |  Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance whose **info** index is **index**. This is an output parameter. The format instance obtained by using this method does not need to be destroyed by calling [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_CreateContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)
```

**Description**

Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br>You can destroy an instance by calling [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format |  Pointer to the newly created [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_DestroyContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)
```

**Description**

Destroys a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**Description**

Obtains a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and locale settings. Call this method when an app needs to obtain the localized format of a specific OE extension based on the known OEID. Before calling this method, create an instance by calling [OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat).

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| const char *oeid | Unique identifier of the document format.|
| const char *locale | [Locale ID](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. If the parameter is not specified, the system locale is used by default.|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format |  Pointer to the **ContentEmbed_Format** object. This is an output parameter. You need to create an instance by calling [OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat) first.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetOEidFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)
```

**Description**

Obtains the OEID of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| char *oeid |  Array of OEIDs. This is an output parameter. It is recommended that the array length be [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetNameAndDescriptionFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)
```

**Description**

Obtains the localized display name and description of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| char *name |  Array of names. This is an output parameter. It is recommended that the array length be [MAX_NAME_LENGTH](#macros).|
| char *description |  Array of descriptions. This is an output parameter. It is recommended that the array length be [MAX_DESCRIPTION_LENGTH](#macros).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetIconFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)
```

**Description**

Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **icon |  Pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance for storing the icon. This is an output parameter.<br>             You need to destroy the instance by calling [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to avoid memory leaks.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.|

### OH_ContentEmbed_GetFileNameExtensionsFromFormat()

```c
char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)
```

**Description**

Obtains the file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| unsigned int *count |  Number of returned file name extensions. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| char** | Pointer to the array of file name extensions. The memory for this array is managed internally by the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance and is valid before the format object is destroyed. You do not need to free the memory separately.|

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**Description**

Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br>You can destroy the instance by calling[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks. After the instance is created, its lifecycle is managed by the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. You need to destroy the instance by calling [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy). Do not call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) separately to destroy the instance. Otherwise, the instance will be released repeatedly.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to an OE document instance.|
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy |  Pointer to the newly created [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. This is an output parameter.|
| void *contextPtr | Pointer to a UIAbility context instance, which is used to pass UIAbility context information. You must pass a valid pointer to the UIAbility context object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. This API can also be called to destroy the [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance associated during proxy creation. After the instance is destroyed, the document pointer obtained by calling [OH_ContentEmbed_Proxy_GetDocument](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getdocument) becomes invalid. The proxy cannot be destroyed when it is dispatching a callback.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_ClientCallbackOnUpdateFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Defines the callback function for notifying the client when the OE document is updated.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

### OH_ContentEmbed_ClientCallbackOnErrorFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
```

**Description**

Defines the callback function for notifying the client when an OE document error occurs.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) error | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode).|

### OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
```

**Description**

Defines the callback function for notifying the client when the editing of an OE document is complete.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| bool dataModified | Whether the OE document data has been modified. The value **true** indicates that the OE document has been modified, and **false** indicates the opposite.|

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Defines the callback function for notifying the client when the OE extension is stopped.<br>You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

### OH_ContentEmbed_Proxy_RegisterOnUpdateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)
```

**Description**

Registers the callback function for OE document update with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) onUpdateFunc | [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**Description**

Registers the callback function for OE document errors with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)
```

**Description**

Registers the callback function for OE document editing completion with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) onEditingFinishedFunc | [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)
```

**Description**

Registers the callback function for OE extension stop with the client OE object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) onExtensionStoppedFunc | [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) callback function to be registered.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Connects to the server OE extension and establishes a communication channel with the OE extension. Before calling this API, register the necessary client callback functions by calling [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc), [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc), [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc), and [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc). This method is used to establish a communication channel. If communication is not required, call the [OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork) disconnect the channel.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The required client callback is not registered.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.<br>     **CE_ERR_CONNECT_LIMIT_EXCEED**: The number of OE extension connections exceeds the limit.<br>     **CE_ERR_FILE_NOT_GRANT**: The file is not authorized.<br>     **CE_ERR_DISK_FULL**: The disk space is insufficient.|

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Disconnects the communication channel with the OE extension. This method must be called after a communication channel is established by calling [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to disconnect the established connection.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**Description**

Obtains the snapshot image of the current OE document from the client OE object for preview or thumbnail display. You must call [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish a communication channel with the OE extension before obtaining the snapshot. It is recommended that you call [OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability) to check whether the OE extension instance on the server supports the snapshot capability before calling this method.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **snapshot |  Pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance for storing the document snapshot. This is an output parameter.<br>        You need to destroy the instance by calling [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to avoid memory leaks.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: The pointer is null.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.<br>     **CE_ERR_EXTENSION_NOT_SUPPORT**: The OE extension does not support this capability.|

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Requests the OE Extension instance to enter edit mode by the client OE object. You must call [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish a communication channel with the OE extension instance first. Otherwise, the request will fail. It is recommended that you call [OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability) to check whether the OE extension instance on the server supports the editing capability before calling this method.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.<br>     **CE_ERR_EXTENSION_NOT_SUPPORT**: The OE extension does not support this capability.|

### OH_ContentEmbed_Proxy_GetEditStatus()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)
```

**Description**

Queries the current editing state and modification status of an OE document in the OE extension instance on the server.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| bool *isEditing |  Whether the OE document is being edited. This is an output parameter. The value **true** indicates that the document is being edited, and **false** indicates the opposite.|
| bool *isModified |  Whether the OE document has been modified. This is an output parameter. The value **true** indicates that the document has been modified, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**Description**

Obtains the capabilities of the OE extension instance on the server. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). This API is used to check whether the server supports the corresponding capabilities before calling [OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot) or [OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| uint32_t *bitmask |  Capabilities of the OE Extension instance on the server. This is an output parameter. The value is a combination of values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the OE document object associated with the client OE object.<br>The OE document object is created by calling [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile).<br>The lifecycle of this document object is managed by the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. You need to destroy the instance by calling [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy). Do not call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) separately to destroy the instance. Otherwise, the instance will be released repeatedly.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument |  Pointer to the OE document instance. This is an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | Returns an error code.<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>     **CE_ERR_IN_DLP_SANDBOX**: The app is in the DLP sandbox and does not support this operation.|
