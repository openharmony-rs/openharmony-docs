# content_embed_document.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @wanxiaoguo-->
<!--Designer: @zhuwei;@weiguoning-->
<!--Tester: @yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

提供OE技术实现的被嵌入文档（简称OE文档）相关数据结构及对应操作接口。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_document.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | 声明OE文档结构体类型。封装了被嵌入文档的元数据、内容和存储结构。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) | ContentEmbed_Storage | 声明OE文档Storage结构体类型。类似于文件系统中的目录，Storage对象的父对象必须是另一个Storage对象或根Storage对象。 |
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) | ContentEmbed_StorageElement | 声明OE文档存储元素的结构体类型。包含名称、类型、时间等信息。 |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) | ContentEmbed_StorageElements | 声明ContentEmbed_StorageElements结构体类型。包含[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)集合信息。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) | ContentEmbed_Stream | 声明OE文档Stream结构体类型。类似于文件系统中的文件，可对其进行读取或写入，且Stream对象只能存在于Storage对象中。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_PATH_LENGTH (4 * 1024) | 表示支持文件路径的最大长度。<br>**起始版本：** 24 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyoeid) | 使用提供的标识符OEID创建一个新的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyfile) | 从源文件创建一个新的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)](#oh_contentembed_loaddocumentfromfile) | 通过已存在的OE格式文件加载[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)](#oh_contentembed_document_read) | 从OE文档对象的指定偏移位置读取原始二进制数据到缓冲区。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)](#oh_contentembed_document_getoeid) | 从OE文档对象获取标识符OEID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)](#oh_contentembed_document_islinking) | OE文档是否以链接方式创建。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)](#oh_contentembed_document_getnativefilepath) | 从OE文档中获取客户端沙箱目录下存储的被嵌入源文件路径。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)](#oh_contentembed_document_getrootstorage) | 从OE文档对象获取根[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)](#oh_contentembed_document_flush) | 将OE文档中数据落盘至OE格式文件。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_createstorage) | 根据OE文档父Storage对象和名称创建子[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_getstorage) | 从OE文档父Storage对象和名称获取子[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_createstream) | 在OE文档父Storage对象和名称创建[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_getstream) | 从OE文档父Storage对象和名称获取子[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)](#oh_contentembed_storage_deleteentry) | 从OE文档父Storage对象删除指定名称的子Storage对象或子Stream对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)](#oh_contentembed_storage_deleteallentry) | 从OE文档Storage对象删除所有条目，包括子Storage对象和子Stream对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)](#oh_contentembed_destroystorage) | 销毁OE文档[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象实例并回收内存。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)](#oh_contentembed_stream_read) | 从OE文档Stream对象的当前位置读取指定长度的数据到缓冲区。读取成功后，Stream对象的偏移量会按实际读取的字节数递增。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)](#oh_contentembed_stream_write) | 将指定长度的数据从缓冲区写入OE文档Stream对象的当前位置。写入成功后，Stream对象的偏移量会按实际写入的字节数递增。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)](#oh_contentembed_stream_seek) | 将OE文档Stream对象的当前读取位置设置为指定的偏移量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)](#oh_contentembed_stream_getposition) | 获取OE文档Stream对象的当前位置偏移量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)](#oh_contentembed_stream_getsize) | 获取OE文档Stream对象的总大小，单位为字节。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)](#oh_contentembed_destroystream) | 销毁OE文档[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象实例并回收内存。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)](#oh_contentembed_destroydocument) | 销毁[ContentEmbed_Document](capi-contentembed-contentembed-document.md)对象实例并回收内存。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_getoeid) | 获取OE文档Storage对象的标识符OEID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)](#oh_contentembed_storage_setoeid) | 设置OE文档Storage对象的标识符OEID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)](#oh_contentembed_storageelements_create) | 创建并初始化[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例。<br> 开发者可通过[OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storageelements_destroy) | 销毁[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例并回收其占用的内存。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storage_getelements) | 获取OE文档Storage对象中的元素列表。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)](#oh_contentembed_storageelements_getcount) | 获取[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例的元素数量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)](#oh_contentembed_storageelements_getelement) | 获取[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例的指定索引位置的元素。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)](#oh_contentembed_storageelement_getname) | 获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的名称。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)](#oh_contentembed_storageelement_getctime) | 获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的创建时间戳，单位为毫秒。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)](#oh_contentembed_storageelement_getmtime) | 获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的最后修改时间戳，单位为毫秒。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)](#oh_contentembed_storageelement_isstorage) | 检查[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例是否为OE文档Storage对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)](#oh_contentembed_storageelement_isstream) | 检查[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例是否为OE文档Stream对象。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)](#oh_contentembed_storage_copyto) | 将源OE文档Storage对象中的所有子Storage对象和Stream对象复制到目标OE文档Storage对象。 |

## 函数说明

### OH_ContentEmbed_CreateDocumentByOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByOEid(const char *oeid, ContentEmbed_Document **document)
```

**描述**

使用提供的标识符OEID创建一个新的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *oeid | 用于唯一表示OE文档的标识符OEID，建议数组长度为[MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | 输出参数。该指针指向新创建的OE文档对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_CreateDocumentByFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)
```

**描述**

从源文件创建一个新的[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *srcFilePath | 源文件路径。 |
| size_t length | 源文件路径字符串的长度，不包括终止符。 |
| bool isLinking | 是否以链接方式创建OE文档。true表示以链接方式创建OE文档，当服务端编辑OE文档时，源文件也会被修改；<br>                  false表示以嵌入方式创建OE文档，当客户端请求服务端编辑OE文档时，会先拷贝一份临时文件到客户端应用沙箱目录。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | 输出参数。该指针指向新创建的OE文档对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。<br>     CE_ERR_INVALID_LINKING_PATH：表示链接文件在应用沙箱中，无法创建链接。 |

### OH_ContentEmbed_LoadDocumentFromFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)
```

**描述**

通过已存在的OE格式文件加载[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例。<br> 开发者可通过[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *srcFilePath | 源文件路径，指向要加载的OE格式文件。 |
| size_t length | 源文件路径字符串的长度，不包括终止符。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | 输出参数。该指针指向新创建的OE文档对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)
```

**描述**

从OE文档对象的指定偏移位置读取原始二进制数据到缓冲区。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *buffer | 输出参数。用于存储从OE文档读取的数据的缓冲区。 |
| size_t length | 缓冲区的大小，单位为字节。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| size_t offset | 从OE文档开始读取的字节偏移位置，从0开始。 |
| size_t *readSize | 输出参数。实际读取的数据长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetOEid(const ContentEmbed_Document *document, char *oeid)
```

**描述**

从OE文档对象获取标识符OEID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| char *oeid | 输出参数。用于存储OEID值的字符数组。建议数组长度为[MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_IsLinking()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)
```

**描述**

OE文档是否以链接方式创建。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| bool *isLinking | 输出参数。true表示以链接方式创建OE文档；false表示嵌入方式创建OE文档。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_GetNativeFilePath()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)
```

**描述**

从OE文档中获取客户端沙箱目录下存储的被嵌入源文件路径。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| char *nativeFilePath | 输出参数。用于存储源文件路径的字符数组。建议数组长度为[MAX_PATH_LENGTH](#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_GetRootStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)
```

**描述**

从OE文档对象获取根[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **storage | 输出参数。调用成功后，该指针指向OE文档根Storage对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_Flush()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)
```

**描述**

将OE文档中数据落盘至OE格式文件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_FILE_OPERATION_FAILED：表示文件操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CreateStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**描述**

根据OE文档父Storage对象和名称创建子[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE文档父Storage对象指针。<br>                      当需要从父Storage对象删除指定的子Storage对象时，可以调用[OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry)。<br>                      当需要从父Storage对象删除所有的子Storage对象时，可以调用[OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry)。 |
| const char *name | 要创建的子Storage的名称。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | 输出参数。调用成功后，该指针指向新创建的OE文档子Storage对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败，可能是parentStorage无效或名称无效。<br>     CE_ERR_NULL_POINTER：表示返回空指针，可能是childStorage创建失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示存储操作失败，可能是磁盘空间不足。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**描述**

从OE文档父Storage对象和名称获取子[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE文档父Storage对象指针。 |
| const char *name | 要获取的子Storage的名称。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | 输出参数。调用成功后，该指针指向找到的OE文档子Storage对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CreateStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**描述**

在OE文档父Storage对象和名称创建[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE文档父Storage对象指针。<br>                      当需要从父Storage对象删除指定的子Stream对象时，可以调用[OH_ContentEmbed_Storage_DeleteEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteentry)。<br>                      当需要从父Storage对象删除所有的子Stream对象时，可以调用[OH_ContentEmbed_Storage_DeleteAllEntry](capi-content-embed-document-h.md#oh_contentembed_storage_deleteallentry)。 |
| const char *name | 要创建的Stream的名称，用于标识和查找该Stream。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | 输出参数。调用成功后，该指针指向新创建的OE文档Stream对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示OE格式文件流操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**描述**

从OE文档父Storage对象和名称获取子[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象。<br> 开发者可通过[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE文档父Storage对象指针。 |
| const char *name | 要获取的OE文档Stream对象的名称。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | 输出参数。调用成功后，该指针指向找到的OE文档Stream对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示OE格式文件流操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_DeleteEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)
```

**描述**

从OE文档父Storage对象删除指定名称的子Storage对象或子Stream对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE文档父Storage对象指针。 |
| const char *name | 要删除的子Storage对象或子Stream对象的名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_FILE_OPERATION_FAILED：表示OE格式文件操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_DeleteAllEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)
```

**描述**

从OE文档Storage对象删除所有条目，包括子Storage对象和子Stream对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE文档Storage对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)
```

**描述**

销毁OE文档[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象实例并回收内存。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE文档Storage对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)
```

**描述**

从OE文档Stream对象的当前位置读取指定长度的数据到缓冲区。读取成功后，Stream对象的偏移量会按实际读取的字节数递增。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |
| unsigned char **buffer | 输出参数。指向存储读取数据的缓冲区的指针。函数内部将分配内存，调用者需要负责释放。 |
| size_t length | 要读取的数据的最大字节数。 |
| size_t *num | 输出参数。实际读取的数据项数量，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示流操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Write()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)
```

**描述**

将指定长度的数据从缓冲区写入OE文档Stream对象的当前位置。写入成功后，Stream对象的偏移量会按实际写入的字节数递增。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |
| const unsigned char *data | 输入参数。指向要写入数据的缓冲区的指针。 |
| size_t length | 要写入的数据的字节数。 |
| size_t *num | 输出参数。实际写入的数据项数量，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示流操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Seek()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)
```

**描述**

将OE文档Stream对象的当前读取位置设置为指定的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |
| size_t position | 要设置的Stream对象相对起始位置的偏移量，单位为字节，从0开始。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示OE格式文件流相关操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_GetPosition()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)
```

**描述**

获取OE文档Stream对象的当前位置偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |
| size_t *position | 输出参数。存储Stream对象相对起始位置的偏移量，单位为字节，从0开始。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示OE格式文件流相关操作失败。<br>     CE_ERR_FILE_OPERATION_FAILED：表示文件操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_GetSize()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)
```

**描述**

获取OE文档Stream对象的总大小，单位为字节。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |
| size_t *size | 输出参数。存储OE文档Stream对象的总字节大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_STREAM_OPERATION_FAILED：表示OE格式文件流相关操作失败。<br>     CE_ERR_FILE_OPERATION_FAILED：表示文件操作失败。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)
```

**描述**

销毁OE文档[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象实例并回收内存。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE文档Stream对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)
```

**描述**

销毁[ContentEmbed_Document](capi-contentembed-contentembed-document.md)对象实例并回收内存。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**描述**

获取OE文档Storage对象的标识符OEID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE文档Storage对象指针。 |
| char *oeid | 输出参数。用于存储标识符OEID的字符数组，建议数组长度为[MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |
| size_t oeidSize | OEID数组的长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_SetOEid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetOEid(ContentEmbed_Storage *storage, char *oeid, size_t oeidSize)
```

**描述**

设置OE文档Storage对象的标识符OEID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE文档Storage对象指针。 |
| char *oeid | 要设置的标识符OEID的字符数组，建议数组长度为[MAX_OEID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |
| size_t oeidSize | OEID数组的长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_Create()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)
```

**描述**

创建并初始化[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例。<br> 开发者可通过[OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) **storageElements | 输出参数。调用成功后，该指针将指向[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_Destroy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)
```

**描述**

销毁[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例并回收其占用的内存。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetElements()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)
```

**描述**

获取OE文档Storage对象中的元素列表。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE文档Storage对象指针。 |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 存储OE文档Storage对象中的元素列表。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示OE格式文件目录相关操作失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_GetCount()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)
```

**描述**

获取[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例的元素数量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例指针。 |
| size_t *count | 输出参数。存储元素集合中的元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_GetElement()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)
```

**描述**

获取[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例的指定索引位置的元素。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)实例指针。 |
| size_t index | 要获取的元素的索引位置，从0开始计数。 |
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) **storageElement | 输出参数。指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetName()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)
```

**描述**

获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的名称。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | 指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |
| char *name | 输出参数。用于存储元素名称字符串。 |
| size_t nameSize | 表示name缓冲区的大小，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetCTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)
```

**描述**

获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的创建时间戳，单位为毫秒。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | 指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |
| uint64_t *ctime | 输出参数。指向元素的创建时间戳，单位为毫秒。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetMTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)
```

**描述**

获取[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例的最后修改时间戳，单位为毫秒。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | 指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |
| uint64_t *mtime | 输出参数。指向元素的最后修改时间戳，单位为毫秒。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_IsStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)
```

**描述**

检查[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例是否为OE文档Storage对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | 指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |
| bool *isStorage | 输出参数。true表示是OE文档Storage对象；false表示不是OE文档Storage对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_IsStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)
```

**描述**

检查[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例是否为OE文档Stream对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *element | 指向[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例指针。 |
| bool *isStream | 输出参数。true表示是OE文档Stream对象；false表示不是OE文档Stream对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CopyTo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)
```

**描述**

将源OE文档Storage对象中的所有子Storage对象和Stream对象复制到目标OE文档Storage对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *srcStorage | 指向源OE文档Storage对象指针。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *destStorage | 指向目标OE文档Storage对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码：<br>     CE_ERR_OK：表示操作成功。<br>     CE_ERR_PARAM_INVALID：表示参数检查失败。<br>     CE_ERR_NULL_POINTER：表示返回空指针。<br>     CE_ERR_STORAGE_OPERATION_FAILED：表示存储操作失败。<br>     CE_ERR_DEVICE_NOT_SUPPORTED：表示设备不支持。<br>     CE_ERR_IN_DLP_SANDBOX：表示应用在DLP沙箱中，不支持此操作。 |


