# content_embed_proxy.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

为客户端应用提供服务端应用注册的OE Extension信息查询接口和与服务端OE Extension对象交互的数据结构及相关操作接口。适用于客户端应用需要查询服务端OE Extension信息、与OE Extension对象进行交互（如创建代理、注册回调、编辑文档、获取快照等）的场景。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_proxy.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | 声明ContentEmbed_Info结构体类型。通过[OH_ContentEmbed_GetContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_getcontentembedinfo)查询当前所有服务端应用注册的OE文档信息，然后通过[OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo)获取当前查询[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量，并通过[OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo)获取指定索引位置的实例对象。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | 声明ContentEmbed_Format结构体类型，包含服务端应用OE Extension注册的OE文档信息。具体可通过[OH_ContentEmbed_GetOEidFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getoeidfromformat)获取OEID、[OH_ContentEmbed_GetNameAndDescriptionFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getnameanddescriptionfromformat)获取名称和描述、[OH_ContentEmbed_GetIconFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_geticonfromformat)获取图标和[OH_ContentEmbed_GetFileNameExtensionsFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getfilenameextensionsfromformat)获取文件扩展名列表。 |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | 声明ContentEmbed_ExtensionProxy结构体类型。用于指向OE文档在客户端封装的文档嵌入和编辑的程序对象（简称客户端OE对象）。在OE文档嵌入和编辑场景中，作为客户端OE对象的句柄，用于调用文档嵌入、编辑等相关接口。开发者通过[OH_ContentEmbed_CreateExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_createextensionproxy)创建客户端OE对象，使用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与服务端的通信后，使用[OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)获取OE文档快照图，通过[OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit)实现编辑功能。通信结束后，使用[OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork)断开连接，通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | 声明OE文档结构体类型。封装了被嵌入文档的元数据、内容和存储结构，用于在应用中统一管理嵌入文档的数据，便于对嵌入文档进行访问、解析与存储。<br>开发者可根据数据来源选取：<br>拥有OEID时使用[OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid)；<br>拥有源文件并需嵌入/链接时使用[OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)；<br>拥有已保存的OE格式文件时使用[OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile)。 |
| [ContentEmbed_Capability](capi-contentembed-contentembed-capability.md) | ContentEmbed_Capability | 声明ContentEmbed_Capability结构体类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_NAME_LENGTH (1 * 1024) | 定义[ContentEmbed_Format](capi-contentembed-contentembed-format.md)中名称字段的最大字符数限制。<br>**起始版本：** 24 |
| MAX_DESCRIPTION_LENGTH (1 * 1024) | 定义[ContentEmbed_Format](capi-contentembed-contentembed-format.md)中描述字段的最大字符数限制。<br>**起始版本：** 24 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)](#oh_contentembed_createcontentembedinfo) | - | 创建[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)](#oh_contentembed_destroycontentembedinfo) | - | 销毁[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | 根据区域设置获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。当应用需要查询当前设备上已注册的OE Extension格式列表时调用。<br>调用前需先通过[OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo)创建实例，调用后可通过[OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo)和[OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo)遍历格式信息。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | 获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | 从[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中获取指定索引位置的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | 创建[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | 销毁[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | 根据OEID和区域设置获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。当应用已知特定OE Extension的OEID，需要获取其本地化格式信息时调用。调用前需先通过[OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat)创建实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的OEID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | 从[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例中获取其本地化的显示名称和描述信息。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的图标。 |
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的文件扩展名列表。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | 创建[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例，以避免内存泄漏。创建成功后该文档对象的生命周期由[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象管理，应通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)统一销毁，请勿单独调用[OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁，否则会导致重复释放。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | 销毁[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。该接口会同时销毁创建代理时关联的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例，销毁后通过[OH_ContentEmbed_Proxy_GetDocument](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getdocument)获取的文档指针将失效。当代理正在派发回调时无法销毁。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | OE文档更新时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | OE文档错误时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | OE文档编辑完成时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | OE Extension停止时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)将此函数注册到客户端OE对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | 向客户端OE对象注册OE文档更新时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | 向客户端OE对象注册OE文档触发错误时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | 向客户端OE对象注册OE文档编辑完成时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | 向客户端OE对象注册OE Extension停止时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | 连接服务端OE Extension，建立与OE Extension的通信通道。调用前需先通过[OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc)、[OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc)、[OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc)和[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)接口注册必要的客户端回调函数。本方法用于建立通信通道，无需通信时请调用[OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork)断开通道。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | 断开与OE Extension的通信通道。须在[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立通信通道之后调用，用于断开已建立的连接。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | 从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示。须先调用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与OE Extension的通信通道后才能获取快照，建议在调用前通过[OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)获取服务端OE Extension实例是否支持快照能力。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | 客户端OE对象请求OE Extension实例进入编辑模式。须先调用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与OE Extension的通信通道，否则无法请求进入编辑模式。建议在调用前通过[OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)获取服务端OE Extension实例是否支持编辑能力。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | 查询服务端OE Extension实例对OE文档的当前编辑状态和修改状态。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | 获取服务端OE Extension实例拥有的能力，以位掩码形式返回，各位的含义参见[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)。用于在调用[OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)、[OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit)接口前确认服务端是否支持相应能力。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | 从客户端OE对象获取其关联的OE文档对象。<br>该OE文档对象通过[OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid)、[OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)或[OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile)方式创建。<br>该文档对象的生命周期由[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象管理，应通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)统一销毁，请勿单独调用[OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁，否则会导致重复释放。 |

## 函数说明

### OH_ContentEmbed_CreateContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedInfo(ContentEmbed_Info **info)
```

**描述**

创建[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedinfo)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) **info | 输出参数。该指针指向新创建的[ContentEmbed_Info](capi-contentembed-contentembed-info.md)对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_DestroyContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedInfo(ContentEmbed_Info *info)
```

**描述**

销毁[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | 指向[ContentEmbed_Info](capi-contentembed-contentembed-info.md)对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**描述**

根据区域设置获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。当应用需要查询当前设备上已注册的OE Extension格式列表时调用。<br>调用前需先通过[OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo)创建实例，调用后可通过[OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo)和[OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo)遍历格式信息。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *locale | [表示区域ID的字符串](../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成，例如"zh-Hans-CN"。当locale为空时，默认使用系统区域设置。 |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | 输出参数。该指针指向ContentEmbed_Info对象。需先通过[OH_ContentEmbed_CreateContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedinfo)创建实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_PERMISSION_DENIED：表示权限校验失败。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetFormatCountFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)
```

**描述**

获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | 指向[ContentEmbed_Info](capi-contentembed-contentembed-info.md)对象指针。 |
| uint32_t *count | 输出参数。存储[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetFormatFromInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)
```

**描述**

从[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中获取指定索引位置的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | 指向[ContentEmbed_Info](capi-contentembed-contentembed-info.md)对象指针。 |
| uint32_t index | 要获取的元素的索引位置，从0开始计数，取值范围[0, count-1]，其中count可通过[OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo)获取。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | 输出参数。获取成功后，返回指向info索引为index的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的指针。通过该方法获取的format实例不需要调用[OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat)进行销毁。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_CreateContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)
```

**描述**

创建[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | 输出参数。该指针指向新创建的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_DestroyContentEmbedFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)
```

**描述**

销毁[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**描述**

根据OEID和区域设置获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。当应用已知特定OE Extension的OEID，需要获取其本地化格式信息时调用。调用前需先通过[OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat)创建实例。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *oeid | 文档格式的唯一标识符字符串。 |
| const char *locale | [表示区域ID的字符串](../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成，例如"zh-Hans-CN"。当locale为空时，默认使用系统区域设置。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 输出参数。该指针指向ContentEmbed_Format对象。需先通过[OH_ContentEmbed_CreateContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_createcontentembedformat)创建实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_PERMISSION_DENIED：表示权限校验失败。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetOEidFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)
```

**描述**

获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的OEID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象指针。 |
| char *oeid | 输出参数。用于存储标识符OEID字符串的字符数组。建议数组长度为[MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetNameAndDescriptionFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)
```

**描述**

从[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例中获取其本地化的显示名称和描述信息。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象指针。 |
| char *name | 输出参数。用于存储名称的字符数组。建议数组长度为[MAX_NAME_LENGTH](#宏定义)。 |
| char *description | 输出参数。用于存储描述信息的字符数组。建议数组长度为[MAX_DESCRIPTION_LENGTH](#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetIconFromFormat()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)
```

**描述**

获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的图标。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象指针。 |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **icon | 输出参数。用于存储图标的[OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md)实例指针。<br>             开发者需要调用[OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)销毁，以避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。 |

### OH_ContentEmbed_GetFileNameExtensionsFromFormat()

```c
char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)
```

**描述**

获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的文件扩展名列表。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象指针。 |
| unsigned int *count | 输出参数。存储返回的文件扩展名数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| char** | 返回文件扩展名字符串数组的指针。该数组内存由[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例内部管理，在销毁Format对象前有效，开发者无需单独释放。 |

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**描述**

创建[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例，以避免内存泄漏。创建成功后该文档对象的生命周期由[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象管理，应通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)统一销毁，请勿单独调用[OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁，否则会导致重复释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档实例的指针。 |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy | 输出参数。该指针指向新创建的[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象。 |
| void *contextPtr | 上下文实例的指针，用于传递UIAbility上下文信息。开发者需传入有效的UIAbilityContext对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

销毁[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。该接口会同时销毁创建代理时关联的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例，销毁后通过[OH_ContentEmbed_Proxy_GetDocument](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getdocument)获取的文档指针将失效。当代理正在派发回调时无法销毁。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_ClientCallbackOnUpdateFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

OE文档更新时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc)将此函数注册到客户端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

### OH_ContentEmbed_ClientCallbackOnErrorFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
```

**描述**

OE文档错误时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc)将此函数注册到客户端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) error | 表示发生的错误码，详细定义参见[ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode)。 |

### OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
```

**描述**

OE文档编辑完成时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc)将此函数注册到客户端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| bool dataModified | 表示OE文档数据是否被修改。true表示OE文档已修改；false表示未修改。 |

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

OE Extension停止时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)将此函数注册到客户端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

### OH_ContentEmbed_Proxy_RegisterOnUpdateFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)
```

**描述**

向客户端OE对象注册OE文档更新时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc) onUpdateFunc | 要注册的[OH_ContentEmbed_ClientCallbackOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonupdatefunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**描述**

向客户端OE对象注册OE文档触发错误时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | 要注册的[OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)
```

**描述**

向客户端OE对象注册OE文档编辑完成时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc) onEditingFinishedFunc | 要注册的[OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackoneditingfinishedfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)
```

**描述**

向客户端OE对象注册OE Extension停止时的回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc) onExtensionStoppedFunc | 要注册的[OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonextensionstoppedfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

连接服务端OE Extension，建立与OE Extension的通信通道。调用前需先通过[OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc)、[OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc)、[OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc)和[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)接口注册必要的客户端回调函数。本方法用于建立通信通道，无需通信时请调用[OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork)断开通道。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_PERMISSION_DENIED：表示权限校验失败。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED：表示必要的客户端回调未注册。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。<br>     CE_ERR_CONNECT_LIMIT_EXCEED：表示OE Extension连接超出限制。<br>     CE_ERR_FILE_NOT_GRANT：表示文件未被授权。<br>     CE_ERR_DISK_FULL：表示磁盘空间不足。 |

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

断开与OE Extension的通信通道。须在[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立通信通道之后调用，用于断开已建立的连接。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_PERMISSION_DENIED：表示权限校验失败。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_SYSTEM_ABNORMAL：表示系统服务异常。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**描述**

从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示。须先调用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与OE Extension的通信通道后才能获取快照，建议在调用前通过[OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)获取服务端OE Extension实例是否支持快照能力。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md) **snapshot | 输出参数。用于存储文档快照的[OH_PixelmapNative](../apis-arkgraphics2d/capi-drawing-oh-pixelmapnative.md)实例指针。<br>        开发者需要调用[OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)销毁，以避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示出现空指针错误。<br>     CE_ERR_EXTENSION_ERROR：表示OE Extension发生错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。<br>     CE_ERR_EXTENSION_NOT_SUPPORT：表示OE Extension不支持该能力。 |

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

客户端OE对象请求OE Extension实例进入编辑模式。须先调用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与OE Extension的通信通道，否则无法请求进入编辑模式。建议在调用前通过[OH_ContentEmbed_Proxy_GetCapability](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)获取服务端OE Extension实例是否支持编辑能力。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_EXTENSION_ERROR：表示OE Extension发生错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。<br>     CE_ERR_EXTENSION_NOT_SUPPORT：表示OE Extension不支持该能力。 |

### OH_ContentEmbed_Proxy_GetEditStatus()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)
```

**描述**

查询服务端OE Extension实例对OE文档的当前编辑状态和修改状态。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| bool *isEditing | 输出参数。表示OE文档是否正在编辑。true表示正在编辑；false表示未在编辑。 |
| bool *isModified | 输出参数。表示OE文档是否已被修改。true表示已修改；false表示未修改。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_EXTENSION_ERROR：表示OE Extension发生错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**描述**

获取服务端OE Extension实例拥有的能力，以位掩码形式返回，各位的含义参见[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)。用于在调用[OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)、[OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit)接口前确认服务端是否支持相应能力。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| uint32_t *bitmask | 输出参数。表示服务端OE Extension实例拥有的能力，由[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)中的值组合而成。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_EXTENSION_ERROR：表示OE Extension发生错误。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**描述**

从客户端OE对象获取其关联的OE文档对象。<br>该OE文档对象通过[OH_ContentEmbed_CreateDocumentByOEid](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid)、[OH_ContentEmbed_CreateDocumentByFile](./capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)或[OH_ContentEmbed_LoadDocumentFromFile](./capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile)方式创建。<br>该文档对象的生命周期由[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象管理，应通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)统一销毁，请勿单独调用[OH_ContentEmbed_DestroyDocument](./capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁，否则会导致重复释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | 输出参数。用于存储OE文档实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |
