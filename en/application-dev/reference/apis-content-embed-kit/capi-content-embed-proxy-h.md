# content_embed_proxy.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=062c28151b892e304a4ebc8988ff611dc5ebc4e9 translatedAt=2026-07-22T12:03:06.719Z pushedAt=2026-07-23T05:57:14.873Z -->

## Overview

Provides the client application with the API for querying the OE Extension information registered by the server application, the data structures for interacting with the server OE Extension object, and the related operation APIs.

**File to include:** <ContentEmbedKit/content_embed/content_embed_proxy.h>

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | Defines a **ContentEmbed_Info** struct, which contains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) information that can be obtained by the client. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | Defines a **ContentEmbed_Format** struct, which contains the OEID, display name, description, icon, and file extension information registered by the server application OE Extension. |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | Defines a **ContentEmbed_ExtensionProxy** struct, which points to the document embedding and editing object (client OE object) encapsulated by the OE document on the client. |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Defines a struct for the OE documents, which encapsulates the metadata, content, and storage structure of the embedded document. |
| [ContentEmbed_Capability](capi-contentembed-contentembed-capability.md) | ContentEmbed_Capability | Defines a **ContentEmbed_Capability** struct. |

### Macros

| Name | Description |
| -- | -- |
| MAX_NAME_LENGTH (1 * 1024) | Defines the maximum length of the name field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since:** 24 |
| MAX_DESCRIPTION_LENGTH (1 * 1024) | Defines the maximum length of the description field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since:** 24 |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)](#oh_contentembed_createcontentembedinfo) | - | Creates a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leak. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)](#oh_contentembed_destroycontentembedinfo) | - | Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the locale. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index position from a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leak. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | Destroys a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | Obtains a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and locale. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | Obtains the OEID of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | Obtains the localized display name and description from a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | Obtains the file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leak. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | This callback function is triggered to notify the client when the OE document is updated.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | This callback function is triggered to notify the client when an error occurs in the OE document.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | This callback function is triggered to notify the client when editing of the OE document is finished.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | This callback function is triggered when the OE Extension stops.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc). |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | Registers a callback function for OE document updates with the client OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | Registers a callback function for OE document errors with the client OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | Registers a callback function for OE document editing completion with the client OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | Registers a callback function to be triggered when the OE Extension stops with the client OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | Connects to the server OE Extension and establishes a communication channel with it. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | Disconnects from the communication channel with the OE Extension. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | Obtains the current OE document snapshot from the client OE object for preview or thumbnail display. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | Requests the OE Extension instance to enter editing mode by the client OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | Queries the current editing status and modification status of the OE document from the server OE Extension instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | Obtains the capabilities of the server OE Extension instance, returned as a bitmask. For details, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | Obtains the OE document object associated with the client OE object from the client OE object.<br> The OE document object is created through [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile).<br> When the OE document is no longer needed, call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it. |

## Function Description

### OH_ContentEmbed_CreateContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)
```

**Description**

Creates a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leak.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) **info | Output parameter, which is a pointer to the newly created [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_DestroyContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)
```

**Description**

Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**Description**

Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the locale.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| const char *locale | [Locale information](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. When **locale** is null, the system locale setting is used by default. |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Output parameter, which is a pointer to the **ContentEmbed_Info** object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetFormatCountFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)
```

**Description**

Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |
| uint32_t *count | Output parameter, which stores the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetFormatFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)
```

**Description**

Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the index position from a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| const [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |
| uint32_t index | Index of the format to obtain. The value starts from **0**. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter, which is a pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_CreateContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)
```

**Description**

Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leak.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter, which is a pointer to the newly created [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_DestroyContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)
```

**Description**

Destroys a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**Description**

Obtains a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and locale.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| const char *oeid | Unique ID of the document format, in string format. |
| const char *locale | [Locale information](../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. When **locale** is null, the system locale setting is used by default. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Output parameter, which is a pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetOEidFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)
```

**Description**

Obtains the OEID of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| char *oeid | Output parameter, which is a character array used to store the OEID string. The recommended array length is [MAX_OEID_LENGTH](capi-content-embed-common-h.md#macros). |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetNameAndDescriptionFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)
```

**Description**

Obtains the localized display name and description from a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| char *name | Output parameter, which is a character array used to store the name. The recommended array length is [MAX_NAME_LENGTH](#macros). |
| char *description | Output parameter, which is a character array used to store the description. The recommended array length is [MAX_DESCRIPTION_LENGTH](#macros). |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetIconFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)
```

**Description**

Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **icon | Output parameter, which is a pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance used to store the icon.<br>             You need to call [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to destroy it to avoid memory leak. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device. |

### OH_ContentEmbed_GetFileNameExtensionsFromFormat()

```c
char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)
```

**Description**

Obtains the file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| unsigned int *count | Output parameter, which is used to store the number of file name extensions returned. |

**Returns**

| Type | Description |
| -- | -- |
| char** | Pointer to an array of file name extensions returned, in string format. |

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**Description**

Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.<br> You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leak.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to an OE document instance. |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy | Output parameter, which is a pointer to the newly created [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| void *contextPtr | Pointer to a context instance, which is used to pass the application context information. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_ClientCallbackOnUpdateFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

This callback function is triggered to notify the client when the OE document is updated.<br> You need to implement this function and register it with the client OE object through  [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

### OH_ContentEmbed_ClientCallbackOnErrorFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
```

**Description**

This callback function is triggered to notify the client when an error occurs in the OE document.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) error | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode). |

### OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
```

**Description**

This callback function is triggered to notify the client when editing of the OE document is finished.<br> You need to implement this function and register it with the client OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| bool dataModified | Whether the OE document data has been modified. The value **true** indicates the OE document has been modified, and **false** indicates otherwise. |

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

This callback function is triggered when the OE Extension stops.<br> You need to implement this function and register it with the client OE object through  [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

### OH_ContentEmbed_Proxy_RegisterOnUpdateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)
```

**Description**

Registers a callback function for OE document updates with the client OE object.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) onUpdateFunc | The [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) callback function to register. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**Description**

Registers a callback function for OE document errors with the client OE object.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | The [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) callback function to register. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)
```

**Description**

Registers a callback function for OE document editing completion with the client OE object.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) onEditingFinishedFunc | The [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) callback function to register. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)
```

**Description**

Registers a callback function to be triggered when the OE Extension stops with the client OE object.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) onExtensionStoppedFunc | The [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) callback function to register. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Connects to the server OE Extension and establishes a communication channel with it.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED**: The required client callback is not registered.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications.<br>     **CE_ERR_CONNECT_LIMIT_EXCEED**: The number of OE Extension connections exceeds the limit.<br>     **CE_ERR_FILE_NOT_GRANT**: The file is unauthorized.<br>     **CE_ERR_DISK_FULL**: The disk is full. |

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Disconnects from the communication channel with the OE Extension.

**Required permissions:** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_PERMISSION_DENIED**: The permission verification fails.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_SYSTEM_ABNORMAL**: The system service is abnormal.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**Description**

Obtains the current OE document snapshot from the client OE object for preview or thumbnail display. 

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **snapshot | Output parameter, which is a pointer to the [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) instance pointer for storing the document snapshot.<br>        You need to call [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to destroy it to avoid memory leak. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_NULL_POINTER**: A null pointer is returned.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE Extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications.<br>     **CE_ERR_EXTENSION_NOT_SUPPORT**: This capability is not supported by the OE Extension. |

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Requests the OE Extension instance to enter editing mode by the client OE object.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE Extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications.<br>     **CE_ERR_EXTENSION_NOT_SUPPORT**: This capability is not supported by the OE Extension. |

### OH_ContentEmbed_Proxy_GetEditStatus()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)
```

**Description**

Queries the current editing status and modification status of the OE document from the server OE Extension instance.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| bool *isEditing | Output parameter, which indicates whether the content-embedded document is being edited. The value **true** indicates the document is being edited, and **false** means the opposite. |
| bool *isModified | Output parameter, which indicates whether the content-embedded document has been modified. The value **true** means the document has been modified, and **false** means the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE Extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**Description**

Obtains the capabilities of the server OE Extension instance, returned as a bitmask. For details, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| uint32_t *bitmask | Output parameter, which indicates the capabilities of the server OE Extension instance. This parameter includes the values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_EXTENSION_ERROR**: An error occurs in the OE Extension.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the OE document object associated with the client OE object from the client OE object.<br> The OE document object is created through [OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile).<br> When the OE document is no longer needed, call [OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it.

**Since**: 24

**Parameters**

| Name | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter, which is a pointer to the OE document instance. |

**Returns**

| Type | Description |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | The error codes are as follows:<br>     **CE_ERR_OK**: The operation is successful.<br>     **CE_ERR_PARAM_INVALID**: The parameter check fails.<br>     **CE_ERR_DEVICE_NOT_SUPPORTED**: This operation is not supported on the device.<br>     **CE_ERR_IN_DLP_SANDBOX**: This operation is not supported for DLP sandbox applications. |