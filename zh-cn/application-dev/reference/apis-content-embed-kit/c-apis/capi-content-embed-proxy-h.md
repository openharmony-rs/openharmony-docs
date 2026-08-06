# content_embed_proxy.h

## 概述

为客户端应用提供服务端应用注册的OE Extension信息查询接口和与服务端OE Extension对象交互的数据结构及相关操作接口。

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) | ContentEmbed_Info | 声明ContentEmbed_Info结构体类型。通过{@link OH_ContentEmbed_GetContentEmbedInfo}查询当前所有服务端应用注册的OE文档信息，然后通过{@link OH_ContentEmbed_GetFormatCountFromInfo}获取当前查询{@link ContentEmbed_Format}实例的数量，并通过{@link OH_ContentEmbed_GetFormatFromInfo}获取指定索引位置的实例对象。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) | ContentEmbed_Format | 声明ContentEmbed_Format结构体类型，包含服务端应用OE Extension注册的OE文档信息。具体可通过{@link OH_ContentEmbed_GetOEidFromFormat}获取OEID、{@link OH_ContentEmbed_GetNameAndDescriptionFromFormat}获取名称和描述、{@link OH_ContentEmbed_GetIconFromFormat}获取图标和{@link OH_ContentEmbed_GetFileNameExtensionsFromFormat}获取文件扩展名列表。 |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) | ContentEmbed_ExtensionProxy | 声明ContentEmbed_ExtensionProxy结构体类型。用于指向OE文档在客户端封装的文档嵌入和编辑的程序对象（简称客户端OE对象）。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | 声明OE文档结构体类型。封装了被嵌入的文档的元数据、内容和存储结构。 |
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
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)](#oh_contentembed_getcontentembedinfo) | - | 根据区域设置获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatCountFromInfo(const ContentEmbed_Info *info, uint32_t *count)](#oh_contentembed_getformatcountfrominfo) | - | 获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetFormatFromInfo(const ContentEmbed_Info *info, uint32_t index, ContentEmbed_Format **format)](#oh_contentembed_getformatfrominfo) | - | 从[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例中获取指定索引位置的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateContentEmbedFormat(ContentEmbed_Format **format)](#oh_contentembed_createcontentembedformat) | - | 创建[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyContentEmbedFormat](capi-content-embed-proxy-h.md#oh_contentembed_destroycontentembedformat)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyContentEmbedFormat(ContentEmbed_Format *format)](#oh_contentembed_destroycontentembedformat) | - | 销毁[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)](#oh_contentembed_getcontentembedformatbyoeidandlocale) | - | 根据OEID和区域设置获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetOEidFromFormat(const ContentEmbed_Format *format, char *oeid)](#oh_contentembed_getoeidfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的OEID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetNameAndDescriptionFromFormat(const ContentEmbed_Format *format, char *name, char *description)](#oh_contentembed_getnameanddescriptionfromformat) | - | 从[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例中获取其本地化的显示名称和描述信息。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_GetIconFromFormat(const ContentEmbed_Format *format, OH_PixelmapNative **icon)](#oh_contentembed_geticonfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的图标。 |
| [char** OH_ContentEmbed_GetFileNameExtensionsFromFormat(const ContentEmbed_Format *format, unsigned int *count)](#oh_contentembed_getfilenameextensionsfromformat) | - | 获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的文件扩展名列表。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)](#oh_contentembed_createextensionproxy) | - | 创建[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_destroyextensionproxy) | - | 销毁[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnUpdateFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonupdatefunc) | OH_ContentEmbed_ClientCallbackOnUpdateFunc | OE文档更新时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnUpdateFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronupdatefunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnErrorFunc)(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)](#oh_contentembed_clientcallbackonerrorfunc) | OH_ContentEmbed_ClientCallbackOnErrorFunc | OE文档错误时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronerrorfunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc)(ContentEmbed_ExtensionProxy *proxy, bool dataModified)](#oh_contentembed_clientcallbackoneditingfinishedfunc) | OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc | OE文档编辑完成时通知客户端的回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeroneditingfinishedfunc)将此函数注册到客户端OE对象。 |
| [typedef void (\*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_clientcallbackonextensionstoppedfunc) | OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc | OE Extension停止时回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)将此函数注册到客户端OE对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnUpdateFunc onUpdateFunc)](#oh_contentembed_proxy_registeronupdatefunc) | - | 向客户端OE对象注册OE文档更新时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)](#oh_contentembed_proxy_registeronerrorfunc) | - | 向客户端OE对象注册OE文档触发错误时回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnEditingFinishedFunc onEditingFinishedFunc)](#oh_contentembed_proxy_registeroneditingfinishedfunc) | - | 向客户端OE对象注册OE文档编辑完成时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc onExtensionStoppedFunc)](#oh_contentembed_proxy_registeronextensionstoppedfunc) | - | 向客户端OE对象注册OE Extension停止时的回调函数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_startwork) | - | 连接服务端OE Extension，建立与OE Extension的通信通道。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_stopwork) | - | 断开与OE Extension的通信通道。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)](#oh_contentembed_proxy_getsnapshot) | - | 从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)](#oh_contentembed_proxy_doedit) | - | 客户端OE对象请求OE Extension实例进入编辑模式。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetEditStatus(ContentEmbed_ExtensionProxy *proxy, bool *isEditing, bool *isModified)](#oh_contentembed_proxy_geteditstatus) | - | 查询服务端OE Extension实例对OE文档的当前编辑状态和修改状态。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)](#oh_contentembed_proxy_getcapability) | - | 获取服务端OE Extension实例拥有的能力，以位掩码形式返回，各位的含义参见[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)](#oh_contentembed_proxy_getdocument) | - | 从客户端OE对象获取其关联的OE文档对象。<br>该OE文档对象通过{@link OH_ContentEmbed_CreateDocumentByOEid}、{@link OH_ContentEmbed_CreateDocumentByFile}或{@link OH_ContentEmbed_LoadDocumentFromFile}方式创建。<br>当该OE文档不再需要时，应调用{@link OH_ContentEmbed_DestroyDocument}将其销毁。 |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)：表示返回空指针。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

### OH_ContentEmbed_GetContentEmbedInfo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedInfo(const char *locale, ContentEmbed_Info *info)
```

**描述**

根据区域设置获取[ContentEmbed_Info](capi-contentembed-contentembed-info.md)实例。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *locale | 表示区域ID的字符串，由语言、脚本、国家地区组成，例如"zh-Hans-CN"。当locale为空时，默认使用系统区域设置。 |
| [ContentEmbed_Info](capi-contentembed-contentembed-info.md) *info | 输出参数。该指针指向ContentEmbed_Info对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode)：表示权限校验失败。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)：表示系统服务工作异常。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| uint32_t index | 要获取的format的索引位置，从0开始。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) **format | 输出参数。获取成功后，返回指向info索引为index的[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)：表示返回空指针。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

### OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(const char *oeid, const char *locale, ContentEmbed_Format *format)
```

**描述**

根据OEID和区域设置获取[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *oeid | 文档格式的唯一标识符字符串。 |
| const char *locale | 表示区域ID的字符串，由语言、脚本、国家地区组成，例如"zh-Hans-CN"。当locale为空时，默认使用系统区域设置。 |
| [ContentEmbed_Format](capi-contentembed-contentembed-format.md) *format | 输出参数。该指针指向[ContentEmbed_Format](capi-contentembed-contentembed-format.md)对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode)：表示权限校验失败。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)：表示系统服务工作异常。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| char *oeid | 输出参数。用于存储标识符OEID字符串的字符数组。建议数组长度为{@link MAX_OEID_LENGTH}。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| char *name | 输出参数。用于存储名称的字符数组。建议数组长度为{@link MAX_NAME_LENGTH}。 |
| char *description | 输出参数。用于存储描述信息的字符数组。建议数组长度为{@link MAX_DESCRIPTION_LENGTH}。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| OH_PixelmapNative **icon | 输出参数。用于存储图标的{@link OH_PixelmapNative}实例指针。<br>开发者需要调用{@link OH_PixelmapNative_Destroy}销毁，以避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)：表示返回空指针。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>         </ul> |

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
| char** | 返回文件扩展名字符串数组的指针。 |

### OH_ContentEmbed_CreateExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateExtensionProxy(ContentEmbed_Document *document, ContentEmbed_ExtensionProxy **proxy, void *contextPtr)
```

**描述**

创建[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。<br>开发者可通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档实例的指针。 |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) **proxy | 输出参数。该指针指向新创建的[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象。 |
| void *contextPtr | 上下文实例的指针，用于传递应用上下文信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)：表示返回空指针。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_DestroyExtensionProxy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyExtensionProxy(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

销毁[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)实例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

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
| (ContentEmbed_ExtensionProxy \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

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
| (ContentEmbed_ExtensionProxy \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
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
| (ContentEmbed_ExtensionProxy \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| bool dataModified | 表示OE文档数据是否被修改。true表示OE文档已修改；false表示未修改。 |

### OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc()

```c
typedef void (*OH_ContentEmbed_ClientCallbackOnExtensionStoppedFunc)(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

OE Extension停止时回调函数类型。<br>开发者需要实现此函数并通过[OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc](capi-content-embed-proxy-h.md#oh_contentembed_proxy_registeronextensionstoppedfunc)将此函数注册到客户端OE对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (ContentEmbed_ExtensionProxy \*proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_RegisterOnErrorFunc()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_RegisterOnErrorFunc(ContentEmbed_ExtensionProxy *proxy, OH_ContentEmbed_ClientCallbackOnErrorFunc onErrorFunc)
```

**描述**

向客户端OE对象注册OE文档触发错误时回调函数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc) onErrorFunc | 要注册的[OH_ContentEmbed_ClientCallbackOnErrorFunc](capi-content-embed-proxy-h.md#oh_contentembed_clientcallbackonerrorfunc)回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_StartWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StartWork(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

连接服务端OE Extension，建立与OE Extension的通信通道。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode)：表示权限校验失败。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED](capi-content-embed-common-h.md#contentembed_errorcode)：表示必要的客户端回调未注册。</li><br>     <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)：表示系统服务异常。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>     <li>[CE_ERR_CONNECT_LIMIT_EXCEED](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension连接数超出限制。</li><br>     <li>[CE_ERR_FILE_NOT_GRANT](capi-content-embed-common-h.md#contentembed_errorcode)：表示文件未被授权。</li><br>     <li>[CE_ERR_DISK_FULL](capi-content-embed-common-h.md#contentembed_errorcode)：表示磁盘已满。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_StopWork()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_StopWork(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

断开与OE Extension的通信通道。

**需要权限：** ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_PERMISSION_DENIED](capi-content-embed-common-h.md#contentembed_errorcode)：表示权限校验失败。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_SYSTEM_ABNORMAL](capi-content-embed-common-h.md#contentembed_errorcode)：表示系统服务异常。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_GetSnapshot()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetSnapshot(ContentEmbed_ExtensionProxy *proxy, OH_PixelmapNative **snapshot)
```

**描述**

从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| OH_PixelmapNative **snapshot | 输出参数。用于存储文档快照的{@link OH_PixelmapNative}实例指针。<br>开发者需要调用{@link OH_PixelmapNative_Destroy}销毁，以避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)：表示返回空指针。</li><br>     <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension发生错误。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>     <li>[CE_ERR_EXTENSION_NOT_SUPPORT](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension不支持该能力。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_DoEdit()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_DoEdit(ContentEmbed_ExtensionProxy *proxy)
```

**描述**

客户端OE对象请求OE Extension实例进入编辑模式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension发生错误。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>     <li>[CE_ERR_EXTENSION_NOT_SUPPORT](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension不支持该能力。</li><br>         </ul> |

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
| bool *isEditing | 输出参数。表示内容嵌入文档是否正在编辑。true表示正在编辑；false表示未在编辑。 |
| bool *isModified | 输出参数。表示内容嵌入文档是否已被修改。true表示已修改；false表示未修改。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension发生错误。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_GetCapability()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetCapability(ContentEmbed_ExtensionProxy *proxy, uint32_t *bitmask)
```

**描述**

获取服务端OE Extension实例拥有的能力，以位掩码形式返回，各位的含义参见[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| uint32_t *bitmask | 输出参数。表示服务端OE Extension实例拥有的能力，由[ContentEmbed_CapabilityCode](capi-content-embed-common-h.md#contentembed_capabilitycode)中的值组合而成。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_EXTENSION_ERROR](capi-content-embed-common-h.md#contentembed_errorcode)：表示OE Extension发生错误。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |

### OH_ContentEmbed_Proxy_GetDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Proxy_GetDocument(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_Document **ceDocument)
```

**描述**

从客户端OE对象获取其关联的OE文档对象。<br>该OE文档对象通过{@link OH_ContentEmbed_CreateDocumentByOEid}、{@link OH_ContentEmbed_CreateDocumentByFile}或{@link OH_ContentEmbed_LoadDocumentFromFile}方式创建。<br>当该OE文档不再需要时，应调用{@link OH_ContentEmbed_DestroyDocument}将其销毁。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md) *proxy | 指向[ContentEmbed_ExtensionProxy](capi-contentembed-contentembed-extensionproxy.md)对象的指针。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **ceDocument | 输出参数。用于存储OE文档实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | <ul><br>     <li>[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)：表示操作成功。</li><br>     <li>[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)：表示参数检查失败。</li><br>     <li>[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)：表示设备不支持。</li><br>     <li>[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)：表示应用在DLP沙箱中，不支持此操作。</li><br>         </ul> |


