# content_embed_proxy.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Provides the client application with the API for querying the OE Extension information registered by the server application, the data structures for interacting with the server OE Extension object, and the related operation APIs.

**Header file:** <ContentEmbedKit/content_embed/content_embed_proxy.h>

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | Defines the ContentEmbed_Info structure. Contains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) set information that can be obtained by the client.|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | Defines the ContentEmbed_Format structure. Contains the OEID, display name, description, icon, and file name extension of the OE Extension registered by the server application.|
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | Declares the ContentEmbed_ExtensionProxy structure. Points to the program object (client-side OE object for short) for embedding and editing the encapsulated and encapsulation documents of the OE document on the client.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Declares the structure type of an OE document. The encapsulated and encapsulation documents contain the metadata, content, and storage structure of the embedded document.|
| [ContentEmbed_Capability](capi-contentembed-contentembed-capability.md) | ContentEmbed_Capability | Declares the ContentEmbed_Capability structure.|

### Macros

| Name| Description|
| -- | -- |
| MAX_NAME_LENGTH (1 * 1024) | Defines the maximum number of characters allowed in the name field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since**: 24|
| MAX_DESCRIPTION_LENGTH (1 * 1024) | Defines the maximum number of characters allowed in the description field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since**: 24|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)](#oh_contentembed_createcontentembedinfo) | - | Creates a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)](#oh_contentembed_destroycontentembedinfo) | - | Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | Obtains the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the region settings.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | Destroys a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and region settings.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | Obtains the OEID of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | Obtains the localized display name and description of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | Obtains the list of file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | Creates an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | Destroys an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | Callback function type for notifying the client when the OE document is updated.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | Callback function type for notifying the client when an error occurs in the OE document.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | Callback function type for notifying the client when the OE document editing is complete.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).|
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | Callback function type when the OE Extension is stopped.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | Registers the callback function for updating the client's OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | Registers the callback function for triggering an error when the client's OE document is edited.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | Registers the callback function for completing the editing of the client's OE document.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | Registers the callback function for stopping the OE Extension to the client's OE object.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | Connects to the server's OE Extension and establishes a communication channel with the OE Extension.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | Disconnects the communication channel from the OE Extension.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | Obtains the snapshot image of the current OE document from the client's OE object for preview or thumbnail display.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | Requests the client's OE object to instruct the OE Extension instance to enter the edit mode.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | Queries the current editing state and modification state of the OE document of the server-side OE Extension instance.|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | Obtains the capabilities of the server-side OE Extension instance. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | Obtains the associated OE document object from the client-side OE object.<br> The OE document object is created in [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) mode.<br> When the OE document is no longer needed, you can call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it.|

## Function Description

### OH_ContentEmbed_CreateContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)
```

**Description**

Creates an [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br> You can destroy the instance by calling [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) **info | Output parameter. This pointer points to the newly created [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_DestroyContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)
```

**Description**

Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**Description**

Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the region settings.

**Required permissions**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const char *locale | [Locale ID](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. If the locale is empty, the system locale setting is used by default.|
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Output parameter. This pointer points to the ContentEmbed_Info object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_PERMISSION_DENIED: Permission verification failed.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetFormatCountFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)
```

**Description**

Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|
| uint32_t *count | Output parameter. Number of stored [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetFormatFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)
```

**Description**

Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object.|
| uint32_t index | Index of the format to be obtained, starting from 0.|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter. This pointer points to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameters.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_CreateContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)
```

**Description**

Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter. This pointer points to the newly created [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameters.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_DestroyContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)
```

**Description**

Destroys an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**Description**

Obtains an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and region settings.

**Required permission**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const char *oeid | Unique identifier string of the document format.|
| const char *locale | [Locale ID](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. If the locale is empty, the system locale setting is used by default.|
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Output parameter. The pointer points to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_PERMISSION_DENIED: Permission verification failed.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetOEidFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)
```

**Description**

Obtains the OEID of the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| char *oeid | Output parameter. Character array for storing the identifier string of the OEID. The recommended array length is [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetNameAndDescriptionFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)
```

**Description**

Obtains the localized display name and description from a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| char *name | Output parameter. Character array for storing the name. The recommended array length is [MAX_NAME_LENGTH](#macros).|
| char *description | Output parameter. Character array for storing the description. The recommended array length is [MAX_DESCRIPTION_LENGTH](#macros).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetIconFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)
```

**Description**

Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **icon | Output parameter. Pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance that stores the icon.<br>             You need to call [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to destroy the instance to avoid memory leaks.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.|

### OH_ContentEmbed_GetFileNameExtensionsFromFormat()

```c
char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)
```

**Description**

Obtains the list of file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object.|
| unsigned int *count | Output parameter. Stores the number of returned file name extensions.|

**Returns:**

| Type| Description|
| -- | -- |
| char** | Pointer to the array of strings that indicate the file name extensions.|

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**Description**

Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to an OE document instance.|
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy | Output parameter. This pointer points to the newly created [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| void *contextPtr | Pointer to the context instance, which is used to transfer the application context information.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_ClientCallbackOnUpdateFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Callback function type for notifying the client when the OE document is updated.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

### OH_ContentEmbed_ClientCallbackOnErrorFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
```

**Description**

Callback function type for notifying the client when an error occurs in the OE document.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) error | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode).|

### OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
```

**Description**

Callback function type for notifying the client when the OE document editing is complete.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| bool dataModified | Indicates whether the OE document data has been modified. The value true indicates that the OE document has been modified, and false indicates that the OE document has not been modified.|

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Callback function type when the OE Extension stops.<br> You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

### OH_ContentEmbed_Proxy_RegisterOnUpdateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)
```

**Description**

Registers the callback function for updating an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document with the client.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) onUpdateFunc | [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**Description**

Registers the callback function for triggering an error when an error occurs in the document of the client's object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)
```

**Description**

Registers the callback function for the client to be invoked when an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document is edited.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) onEditingFinishedFunc | [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)
```

**Description**

Registers the callback function for stopping the OE Extension to the client's OE object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) onExtensionStoppedFunc | [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) callback function to be registered.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Connects to the server-side OE Extension and establishes a communication channel with the OE Extension.

**Required permissions**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_PERMISSION_DENIED: Permission verification failed.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED: Necessary client callbacks are not registered.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: The operation is not supported because the application is in the DLP sandbox.<br>     CE_ERR_CONNECT_LIMIT_EXCEED: The number of connected OE Extensions exceeds the upper limit.<br>     CE_ERR_FILE_NOT_GRANT: The file is not granted.<br>     CE_ERR_DISK_FULL: The disk is full.|

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Disconnects the communication channel with the Object Editor Extension.

**Required permissions**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_PERMISSION_DENIED: Permission verification failed.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_SYSTEM_ABNORMAL: The system service is abnormal.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**Description**

Obtains the snapshot image of the current Object Editor document from the client Object Editor object for preview or thumbnail display.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **snapshot | Output parameter. Pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance that stores the document snapshot.<br>        You need to call [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to destroy the instance to avoid memory leaks.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_NULL_POINTER: A null pointer is returned.<br>     CE_ERR_EXTENSION_ERROR: An error occurs in the OE Extension.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.<br>     CE_ERR_EXTENSION_NOT_SUPPORT: The OE Extension does not support this capability.|

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Requests the OE Extension instance to enter the edit mode from the client's OE object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_EXTENSION_ERROR: An error occurs in the OE Extension.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.<br>     CE_ERR_EXTENSION_NOT_SUPPORT: The OE Extension does not support this capability.|

### OH_ContentEmbed_Proxy_GetEditStatus()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)
```

**Description**

Queries the current editing state and modification state of the OE document by the server-side OE Extension instance.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| bool *isEditing | Output parameter. Indicates whether the content embedded document is being edited. true: being edited; false: not being edited.|
| bool *isModified | Output parameter. Indicates whether the content embedded in the document has been modified. The value true indicates that the password has been changed, and the value false indicates that the password has not been changed.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The specific error code is returned:<br>     CE_ERR_OK: Operations are successful.<br>     CE_ERR_PARAM_INVALID: Parameter check failed.<br>     CE_ERR_EXTENSION_ERROR: An error occurred in the OE Extension.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**Description**

Obtains the capabilities of the server-side OE Extension instance. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| uint32_t *bitmask | Output parameter. Indicates the capabilities of the server-side OE Extension instance, which are composed of the values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The following error codes are returned:<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: Failed to check the parameter.<br>     CE_ERR_EXTENSION_ERROR: An error occurs in the OE Extension.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the associated OE document object from the client's OE object.<br> The OE document object is created in [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) mode.<br> When the OE document is no longer needed, call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object.|
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter. Pointer to the pointer that stores the OE document instance.|

**Returns:**

| Type| Description|
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | A specific error code is returned.<br>     CE_ERR_OK: The operation is successful.<br>     CE_ERR_PARAM_INVALID: The parameter check fails.<br>     CE_ERR_DEVICE_NOT_SUPPORTED: The device is not supported.<br>     CE_ERR_IN_DLP_SANDBOX: This operation is not supported because the application is in the DLP sandbox.|
