# content_embed_proxy.h

## Overview

Provides the client application with the API for querying the OE Extension information registered by the server application, the data structures for interacting with the server OE Extension object, and the related operation APIs.

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | Declares the ContentEmbed_Info structure. Use {@link OH_ContentEmbed_GetContentEmbedInfo} to query the<br>OE document information registered by all server-side applications for the current session.<br>Then, use {@link OH_ContentEmbed_GetFormatCountFromInfo} to obtain the count of {@link ContentEmbed_Format}<br>instances in the current query result, and use {@link OH_ContentEmbed_GetFormatFromInfo} to retrieve the instance object at the specified index. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | Declares the ContentEmbed_Info structure. which contains OE document information registered by server-side applications for the OE Extension. Specifically, you can use {@link OH_ContentEmbed_GetOEidFromFormat} to<br>obtain the OEID, {@link OH_ContentEmbed_GetNameAndDescriptionFromFormat} to get the name and description,<br>{@link OH_ContentEmbed_GetIconFromFormat} to retrieve the icon, and<br>{@link OH_ContentEmbed_GetFileNameExtensionsFromFormat} to obtain the list of file extensions. |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | Declares the ContentEmbed_ExtensionProxy structure. Points to the program object (client-side OE object for short) for embedding and editing the client-side encapsulated and encapsulation documents of the OE. |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | Declares the structure type of an OE document. Encapsulates the metadata, content, and storage structure of the embedded document. |
| [ContentEmbed_Capability](capi-contentembed-contentembed-capability.md) | ContentEmbed_Capability | Declares the ContentEmbed_Capability structure. |

### Macro

| Name | Description |
| -- | -- |
| MAX_NAME_LENGTH (1 * 1024) | Defines the maximum number of characters allowed in the name field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since**: 24 |
| MAX_DESCRIPTION_LENGTH (1 * 1024) | Defines the maximum number of characters allowed in the description field in [ContentEmbed_Format](capi-contentembed-contentembed-format.md).<br>**Since**: 24 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)](#oh_contentembed_createcontentembedinfo) | - | Creates an [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. <br>You can destroy the instance by calling [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)](#oh_contentembed_destroycontentembedinfo) | - | Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the region settings. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. <br>You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | Destroys an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | Obtains an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and region settings. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | Obtains the OEID of the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | Obtains the localized display name and description from a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | Obtains the list of file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. <br>You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | Callback function type for notifying the client when the OE document is updated. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | Callback function type for notifying the client when an error occurs in the OE document. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | Callback function type for notifying the client when the OE document editing is complete. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc). |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | Callback function type when the OE Extension stops. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc). |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | Registers the callback function for updating an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document with the client. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | Registers the callback function for triggering an error when an error occurs in the document of the client's object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | Registers the callback function for the client to be invoked when an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document is edited. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | Registers the callback function for stopping the OE Extension to the client's OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | Connects to the server-side OE Extension and establishes a communication channel with the OE Extension. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | Disconnects the communication channel with the OE Extension. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | Obtains the snapshot image of the current OE document from the client OE object for preview or thumbnail display. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | Requests the OE Extension instance to enter the edit mode from the client's OE object. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | Queries the current editing state and modification state of the OE document by the server-side OE Extension instance. |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | Obtains the capabilities of the server-side OE Extension instance. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | Obtains the associated OE document object from the client's OE object. <br>The OE document object is created in [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) mode. <br>When the OE document is no longer needed, call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)( ContentEmbed_ExtensionProxy *proxy) | Callback function type for notifying the client when the OE document is updated. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)( ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error) | Callback function type for notifying the client when an error occurs in the OE document. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)( ContentEmbed_ExtensionProxy *proxy, bool dataModified) | Callback function type for notifying the client when the OE document editing is complete. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).<br>**Since**: 24 |
| void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)( ContentEmbed_ExtensionProxy *proxy) | Callback function type when the OE Extension stops. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).<br>**Since**: 24 |

## Function description

### OH_ContentEmbed_CreateContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)
```

**Description**

Creates an [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. <br>You can destroy the instance by calling [OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo) to avoid memory leaks.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) **info | Output parameter. This pointer points to the newly created [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_DestroyContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)
```

**Description**

Destroys a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**Description**

Obtains a [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance based on the region settings.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Required permission**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *locale | Locale ID, which consists of the language, script, and country/region, for example, **zh-Hans- CN**. If the locale is empty, the system locale setting is used by default. |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Output parameter. This pointer points to the ContentEmbed_Info object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode) - Permission verification failed.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetFormatCountFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)
```

**Description**

Obtains the number of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |
| uint32_t *count | Output parameter. Number of stored [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetFormatFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)
```

**Description**

Obtains the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index from the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | Pointer to the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) object. |
| uint32_t index | Represents the index of the internal array within the [ContentEmbed_Info](capi-contentembed-contentembed-info.md) instance. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter. Upon successful retrieval, returns a pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance at the specified index in info. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameters.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_CreateContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)
```

**Description**

Creates a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance. <br>You can destroy the instance using [OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat) to avoid memory leaks.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | Output parameter. This pointer points to the newly created [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameters.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_DestroyContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)
```

**Description**

Destroys an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**Description**

Obtains an [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance based on the OEID and region settings.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Required permission**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *oeid | Unique identifier string of the document format. |
| const char *locale | Locale ID, which consists of the language, script, and country/region, for example, **zh-Hans- CN**. If the locale is empty, the system locale setting is used by default. |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Output parameter. The pointer points to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode) - Permission verification failed.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetOEidFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)
```

**Description**

Obtains the OEID of the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| char *oeid | Output parameter. Character array for storing the identifier string of the OEID. The recommended array length is [MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义). |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetNameAndDescriptionFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)
```

**Description**

Obtains the localized display name and description from a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| char *name | Output parameter. Character array for storing the name. The recommended array length is [MAX_NAME_LENGTH](capi-content-embed-proxy-h.md#宏定义). |
| char *description | Output parameter. Character array for storing the description. The recommended array length is [MAX_DESCRIPTION_LENGTH](capi-content-embed-proxy-h.md#宏定义). |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetIconFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)
```

**Description**

Obtains the icon of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| OH_PixelmapNative **icon | Output parameter. Pointer to the {@link OH_PixelmapNative} instance that stores the icon.<br>    <br>You need to call {@link OH_PixelmapNative_Destroy} to destroy the instance to avoid memory leaks. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>          </ul> |

### OH_ContentEmbed_GetFileNameExtensionsFromFormat()

```c
char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)
```

**Description**

Obtains the list of file name extensions of a [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | Pointer to the [ContentEmbed_Format](capi-contentembed-contentembed-format.md) object. |
| unsigned int *count | Output parameter. Stores the number of returned file name extensions. |

**Returns**:

| Type | Description |
| -- | -- |
| char** | Pointer to the array of strings that indicate the file name extensions. |

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**Description**

Creates a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance. <br>You can destroy the instance using [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to avoid memory leaks.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | Pointer to an OE document instance. |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy | Output parameter. This pointer points to the newly created [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| void *contextPtr | Pointer to the context instance, which is used to transfer the application context information. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>          </ul> |

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Destroys a [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_ClientCallbackOnUpdateFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Callback function type for notifying the client when the OE document is updated. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Represents a pointer to an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance which will be set in. |

### OH_ContentEmbed_ClientCallbackOnErrorFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
```

**Description**

Callback function type for notifying the client when an error occurs in the OE document. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Represents a pointer to an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance which will be set in. |
| ContentEmbed_ErrorCode error | Error code. For details, see [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode). |

### OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
```

**Description**

Callback function type for notifying the client when the OE document editing is complete. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Represents a pointer to an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance which will be set in. |
| bool dataModified | Indicates whether the OE document data has been modified. The value true indicates that the OE document has been modified, and false indicates that the OE document has not been modified. |

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Callback function type when the OE Extension stops. <br>You need to implement this function and register it with the client's OE object through [OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | Represents a pointer to an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) instance which will be set in. |

### OH_ContentEmbed_Proxy_RegisterOnUpdateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)
```

**Description**

Registers the callback function for updating an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document with the client.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) onUpdateFunc | [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**Description**

Registers the callback function for triggering an error when an error occurs in the document of the client's object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)
```

**Description**

Registers the callback function for the client to be invoked when an [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) document is edited.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) onEditingFinishedFunc | [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)
```

**Description**

Registers the callback function for stopping the OE Extension to the client's OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) onExtensionStoppedFunc | [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) callback function to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Connects to the server-side OE Extension and establishes a communication channel with the OE Extension.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Required permission**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode) - Permission verification failed.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode) - Necessary client callbacks are not registered.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is not supported because the application is in the DLP sandbox.      </li>      <li>[CE_ERR_CONNECT_LIMIT_EXCEED](capi-content-embed-common-h.md#contentembed_errorcode) - The number of connected OE Extensions exceeds the upper limit.</li>      <li>[CE_ERR_FILE_NOT_GRANT](capi-content-embed-common-h.md#contentembed_errorcode) - The file is not granted.</li>      <li>[CE_ERR_DISK_FULL](capi-content-embed-common-h.md#contentembed_errorcode) - The disk is full.</li>          </ul> |

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Disconnects the communication channel with the OE Extension.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Required permission**: ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode) - Permission verification failed.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode) - The system service is abnormal.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**Description**

Obtains the snapshot image of the current OE document from the client OE object for preview or thumbnail display.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| OH_PixelmapNative **snapshot | Output parameter. Pointer to the {@link OH_PixelmapNative} instance that stores the document<br>    snapshot.<br>    <br>You need to call {@link OH_PixelmapNative_Destroy} to destroy the instance to avoid memory leaks. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode) - A null pointer is returned.</li>      <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode) - An error occurs in the OE Extension.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>      <li>[CE_ERR_EXTENSION_NOT_SUPPORT](capi-content-embed-common-h.md#contentembed_errorcode) - The OE Extension does not support this capability.</li>          </ul> |

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**Description**

Requests the OE Extension instance to enter the edit mode from the client's OE object.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode) - An error occurs in the OE Extension.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>      <li>[CE_ERR_EXTENSION_NOT_SUPPORT](capi-content-embed-common-h.md#contentembed_errorcode) - The OE Extension does not support this capability.</li>          </ul> |

### OH_ContentEmbed_Proxy_GetEditStatus()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)
```

**Description**

Queries the current editing state and modification state of the OE document by the server-side OE Extension instance.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| bool *isEditing | Output parameter. Indicates whether the content embedded document is being edited. true: being edited; false: not being edited. |
| bool *isModified | Output parameter. Indicates whether the content embedded in the document has been modified. The value true indicates that the password has been changed, and the value false indicates that the password has not been changed. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - Operations are successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Parameter check failed.</li>      <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode) - An error occurred in the OE Extension.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**Description**

Obtains the capabilities of the server-side OE Extension instance. The capabilities are returned in the form of bit masks. For details about the meaning of each bit, see [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| uint32_t *bitmask | Output parameter. Indicates the capabilities of the server-side OE Extension instance, which are composed of the values in [ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode). |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - Failed to check the parameter.</li>      <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode) - An error occurs in the OE Extension.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**Description**

Obtains the associated OE document object from the client's OE object. <br>The OE document object is created in [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid), [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), or [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) mode. <br>When the OE document is no longer needed, call [OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument) to destroy it.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | Pointer to the [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) object. |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | Output parameter. Pointer to the pointer that stores the OE document instance. |

**Returns**:

| Type | Description |
| -- | -- |
| ContentEmbed_ErrorCode | <ul>      <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode) - The operation is successful.</li>      <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode) - The parameter check fails.</li>      <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode) - The device is not supported.</li>      <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode) - This operation is not supported because the application is in      the DLP sandbox.</li>          </ul> |


