# content_embed_document.h
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 概述

提供OE文档相关数据结构及对应操作接口。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_document.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) | ContentEmbed_Document | 声明OE文档结构体类型。表示一个可嵌入的复合文档对象，封装了文档的元数据、内容和存储结构。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) | ContentEmbed_Storage | 声明OE格式文件目录结构体类型。表示复合文档中的层级容器，类似普通文件系统里的目录，用来组织和管理Stream或其他子Storage。 |
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) | ContentEmbed_StorageElement | 声明ContentEmbed_StorageElement结构体类型。表示复合文档中的一个元素，可能是Stream或Storage。 |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) | ContentEmbed_StorageElements | 声明ContentEmbed_StorageElements结构体类型。表示ContentEmbed_StorageElement的集合。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) | ContentEmbed_Stream | 声明OE格式文件流结构体类型。表示复合文档中存储原始二进制数据的基本单元，类似普通文件系统里的文件。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_PATH_LENGTH (4 * 1024) | 表示支持文件路径的最大长度。<br>**起始版本：** 24 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByHmid(const char *hmid, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyhmid) | 使用提供的HMID创建一个新的OE文档实例。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)](#oh_contentembed_createdocumentbyfile) | 从源文件创建一个新的OE文档实例。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)](#oh_contentembed_loaddocumentfromfile) | 通过已存在的OE格式文件加载OE文档实例。加载成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)](#oh_contentembed_document_read) | 从OE文档对象的指定偏移位置读取数据到缓冲区。读取的数据是OE文档的原始二进制内容。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetHmid(const ContentEmbed_Document *document, char *hmid)](#oh_contentembed_document_gethmid) | 从OE文档对象获取系统可识别标识符HMID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)](#oh_contentembed_document_islinking) | 源文件是否链接到OE文档。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetNativeFilePath(const ContentEmbed_Document *document, char *nativeFilePath)](#oh_contentembed_document_getnativefilepath) | 从OE文档中获取客户端沙箱目录下存储的被嵌入源文件路径。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)](#oh_contentembed_document_getrootstorage) | 从OE文档对象获取OE格式文件根目录。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件根目录，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)](#oh_contentembed_document_flush) | 将OE文档数据写入并保存至OE格式文件。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_createstorage) | 根据OE格式文件父目录和名称创建OE格式文件子目录。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件子目录，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)](#oh_contentembed_storage_getstorage) | 从OE格式文件父目录获取OE格式文件子目录。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件子目录，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_createstream) | 在OE格式文件父目录创建OE格式文件流。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁OE格式文件流，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)](#oh_contentembed_storage_getstream) | 从OE格式文件父目录获取OE格式文件流。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁OE格式文件流，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)](#oh_contentembed_storage_deleteentry) | 从OE格式文件目录删除指定名称的子存储容器或OE格式文件流。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)](#oh_contentembed_storage_deleteallentry) | 从OE格式文件父目录删除所有条目，包括子存储容器和OE格式文件流。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)](#oh_contentembed_destroystorage) | 销毁OE格式文件目录实例并回收内存。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)](#oh_contentembed_stream_read) | 从OE格式文件流的当前位置读取指定长度的数据到缓冲区。读取成功后，流的当前位置将向前移动实际读取的字节数。调用者负责释放缓冲区以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)](#oh_contentembed_stream_write) | 将指定长度的数据从缓冲区写入OE格式文件流的当前位置。写入成功后，流的当前位置将向前移动实际写入的字节数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)](#oh_contentembed_stream_seek) | 将OE格式文件流的当前读取位置设置为指定的偏移量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)](#oh_contentembed_stream_getposition) | 获取OE格式文件流的当前位置。该位置是从OE格式文件流的起始位置开始计算的字节数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)](#oh_contentembed_stream_getsize) | 获取OE格式文件流的总大小（以字节为单位）。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)](#oh_contentembed_destroystream) | 销毁OE格式文件流实例并回收内存。调用此函数后，该OE格式文件流指针将失效，不得再使用。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)](#oh_contentembed_destroydocument) | 销毁OE格式文档实例并回收内存。调用此函数后，该OE格式文档指针将失效，不得再使用。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetHmid(ContentEmbed_Storage *storage, char *hmid, size_t hmidSize)](#oh_contentembed_storage_gethmid) | 获取OE格式文件目录的系统可识别标识符HMID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetHmid(ContentEmbed_Storage *storage, char *hmid, size_t hmidSize)](#oh_contentembed_storage_sethmid) | 设置OE格式文件目录的系统可识别标识符HMID。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)](#oh_contentembed_storageelements_create) | 创建并初始化ContentEmbed_StorageElements实例，用于存储和管理OE格式文件目录中的元素列表。创建成功后，调用者负责通过调用[OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy)销毁实例，以避免内存泄漏。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storageelements_destroy) | 销毁ContentEmbed_StorageElements实例并回收其占用的内存。调用此函数后，该ContentEmbed_StorageElements指针将失效，不得再使用。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)](#oh_contentembed_storage_getelements) | 获取OE格式文件目录中的元素列表。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)](#oh_contentembed_storageelements_getcount) | 获取ContentEmbed_StorageElements实例的元素数量。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)](#oh_contentembed_storageelements_getelement) | 获取ContentEmbed_StorageElements实例的指定索引位置的元素。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)](#oh_contentembed_storageelement_getname) | 获取ContentEmbed_StorageElement实例的名称。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)](#oh_contentembed_storageelement_getctime) | 获取ContentEmbed_StorageElement实例的创建时间戳，时间戳为自Unix纪元（1970年1月1日）以来的毫秒数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)](#oh_contentembed_storageelement_getmtime) | 获取ContentEmbed_StorageElement实例的最后修改时间戳，时间戳为自Unix纪元（1970年1月1日）以来的毫秒数。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)](#oh_contentembed_storageelement_isstorage) | 检查ContentEmbed_StorageElement实例是否为OE格式文件目录类型。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)](#oh_contentembed_storageelement_isstream) | 检查ContentEmbed_StorageElement实例是否为OE格式文件流类型。 |
| [ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)](#oh_contentembed_storage_copyto) | 将源OE格式文件目录中的所有子目录和数据流（包括所有嵌套的子目录）复制到目标OE格式文件目录。 |

## 函数说明

### OH_ContentEmbed_CreateDocumentByHmid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByHmid(const char *hmid, ContentEmbed_Document **document)
```

**描述**

使用提供的HMID创建一个新的OE文档实例。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *hmid | 表示HMID值，是用于唯一表示OE文档的字符串，长度不应超过[MAX_HMID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | 输出参数。该指针指向新创建的OE文档对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。   <br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_CreateDocumentByFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_CreateDocumentByFile(const char *srcFilePath, size_t length, bool isLinking, ContentEmbed_Document **document)
```

**描述**

从源文件创建一个新的OE文档实例。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *srcFilePath | 源文件路径，指向要创建OE文档的本地文件系统路径。 |
| size_t length | 源文件路径字符串的长度，不包括终止符。 |
| bool isLinking | 是否以链接方式创建OE文档。当isLinking为true时，表示以链接方式创建OE文档。当服务端编辑OE文档时，源文件也会被修改。如果源文件被移动、删除或者重命名时，OE文档拉起编辑会失败，如果用户在文管中恢复原始源文件需要应用进行授权。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) **document | 输出参数。该指针指向新创建的OE文档对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。   <br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。<br>     返回[CE_ERR_INVALID_LINKING_PATH](capi-content-embed-common-h.md#contentembed_errorcode)表示尝试链接到不允许被链接目录中的文件。 |

### OH_ContentEmbed_LoadDocumentFromFile()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_LoadDocumentFromFile(const char *srcFilePath, size_t length, ContentEmbed_Document **document)
```

**描述**

通过已存在的OE格式文件加载OE文档实例。加载成功后，调用者负责通过调用[OH_ContentEmbed_DestroyDocument](capi-content-embed-document-h.md#oh_contentembed_destroydocument)销毁实例，以避免内存泄漏。

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
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。   <br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Read(uint8_t *buffer, size_t length, ContentEmbed_Document *document, size_t offset, size_t *readSize)
```

**描述**

从OE文档对象的指定偏移位置读取数据到缓冲区。读取的数据是OE文档的原始二进制内容。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *buffer | 输出参数。用于存储从OE文档读取的数据的缓冲区。 |
| size_t length | 缓冲区的大小。 |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| size_t offset | 从OE文档开始读取的字节偏移位置。 |
| size_t *readSize | 输出参数。实际读取的数据长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_GetHmid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetHmid(const ContentEmbed_Document *document, char *hmid)
```

**描述**

从OE文档对象获取系统可识别标识符HMID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| char *hmid | 输出参数。用于存储HMID值的字符数组。数组大小应至少为[MAX_HMID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_IsLinking()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_IsLinking(const ContentEmbed_Document *document, bool *isLinking)
```

**描述**

源文件是否链接到OE文档。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| bool *isLinking | 输出参数。true表示链接模式，false表示内容复制模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

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
| char *nativeFilePath | 输出参数。用于存储源文件路径的字符数组。数组大小应至少为[MAX_PATH_LENGTH](#宏定义)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_GetRootStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_GetRootStorage(ContentEmbed_Document *document, ContentEmbed_Storage **storage)
```

**描述**

从OE文档对象获取OE格式文件根目录。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件根目录，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **storage | 输出参数。调用成功后，该指针指向OE格式文件根目录。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Document_Flush()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Document_Flush(const ContentEmbed_Document *document)
```

**描述**

将OE文档数据写入并保存至OE格式文件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE文档对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_FILE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示文件操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CreateStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**描述**

根据OE格式文件父目录和名称创建OE格式文件子目录。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件子目录，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE格式文件父目录对象指针。 |
| const char *name | 要创建的子目录的名称。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | 输出参数。调用成功后，该指针指向新创建的OE格式文件子目录。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败，可能是parentStorage无效或名称无效。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针，可能是childStorage创建失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示存储操作失败，可能是磁盘空间不足。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStorage(const ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Storage **childStorage)
```

**描述**

从OE格式文件父目录获取OE格式文件子目录。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStorage](capi-content-embed-document-h.md#oh_contentembed_destroystorage)销毁OE格式文件子目录，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE格式文件父目录对象指针。 |
| const char *name | 要获取的子目录的名称。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) **childStorage | 输出参数。调用成功后，该指针指向找到的OE格式文件子目录。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CreateStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CreateStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**描述**

在OE格式文件父目录创建OE格式文件流。创建成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁OE格式文件流，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE格式文件父目录对象指针。 |
| const char *name | 要创建的OE格式文件流的名称，用于标识和查找该OE格式文件流。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | 输出参数。调用成功后，该指针指向新创建的OE格式文件流。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件流操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetStream(ContentEmbed_Storage *parentStorage, const char *name, ContentEmbed_Stream **childStream)
```

**描述**

从OE格式文件父目录获取OE格式文件流。获取成功后，调用者负责通过调用[OH_ContentEmbed_DestroyStream](capi-content-embed-document-h.md#oh_contentembed_destroystream)销毁OE格式文件流，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE格式文件父目录对象指针。 |
| const char *name | 要获取OE格式文件流的名称，应与创建时使用的名称一致。 |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) **childStream | 输出参数。调用成功后，该指针指向找到的OE格式文件流。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件流操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_DeleteEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteEntry(ContentEmbed_Storage *parentStorage, const char *name)
```

**描述**

从OE格式文件目录删除指定名称的子存储容器或OE格式文件流。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *parentStorage | 指向OE格式文件目录对象指针。 |
| const char *name | 要删除的子存储容器或OE格式文件流的名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_FILE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_DeleteAllEntry()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_DeleteAllEntry(ContentEmbed_Storage *storage)
```

**描述**

从OE格式文件父目录删除所有条目，包括子存储容器和OE格式文件流。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE格式文件目录对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件目录相关操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStorage(ContentEmbed_Storage *storage)
```

**描述**

销毁OE格式文件目录实例并回收内存。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE格式文件目录对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Read()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Read(ContentEmbed_Stream *stream, unsigned char **buffer, size_t length, size_t *num)
```

**描述**

从OE格式文件流的当前位置读取指定长度的数据到缓冲区。读取成功后，流的当前位置将向前移动实际读取的字节数。调用者负责释放缓冲区以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |
| unsigned char **buffer | 输出参数。指向存储读取数据的缓冲区的指针。函数内部将分配内存，调用者需要负责释放。 |
| size_t length | 要读取的数据的最大字节数。 |
| size_t *num | 输出参数。实际读取的数据项数量（以字节为单位）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示流操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Write()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Write(ContentEmbed_Stream *stream, const unsigned char *data, size_t length, size_t *num)
```

**描述**

将指定长度的数据从缓冲区写入OE格式文件流的当前位置。写入成功后，流的当前位置将向前移动实际写入的字节数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |
| const unsigned char *data | 输入参数。指向要写入数据的缓冲区的指针。 |
| size_t length | 要写入的数据的字节数。 |
| size_t *num | 输出参数。实际写入的数据项数量（以字节为单位）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示流操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_Seek()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_Seek(ContentEmbed_Stream *stream, size_t position)
```

**描述**

将OE格式文件流的当前读取位置设置为指定的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |
| size_t position | 要设置的位置偏移量（单位：字节），从OE格式文件流的起始位置开始计算。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件流相关操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_GetPosition()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetPosition(ContentEmbed_Stream *stream, size_t *position)
```

**描述**

获取OE格式文件流的当前位置。该位置是从OE格式文件流的起始位置开始计算的字节数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |
| size_t *position | 输出参数。存储当前位置偏移量（单位：字节）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件流相关操作失败。<br>     返回[CE_ERR_FILE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示文件操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Stream_GetSize()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Stream_GetSize(ContentEmbed_Stream *stream, size_t *size)
```

**描述**

获取OE格式文件流的总大小（以字节为单位）。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |
| size_t *size | 输出参数。存储OE格式文件流的总字节大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STREAM_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示OE格式文件流相关操作失败。<br>     返回[CE_ERR_FILE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示文件操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyStream(ContentEmbed_Stream *stream)
```

**描述**

销毁OE格式文件流实例并回收内存。调用此函数后，该OE格式文件流指针将失效，不得再使用。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) *stream | 指向OE格式文件流对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_DestroyDocument()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_DestroyDocument(ContentEmbed_Document *document)
```

**描述**

销毁OE格式文档实例并回收内存。调用此函数后，该OE格式文档指针将失效，不得再使用。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Document](capi-contentembed-contentembed-document.md) *document | 指向OE格式文档对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetHmid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetHmid(ContentEmbed_Storage *storage, char *hmid, size_t hmidSize)
```

**描述**

获取OE格式文件目录的系统可识别标识符HMID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE格式文件目录对象指针。 |
| char *hmid | 输出参数。用于存储HMID值的字符数组。数组大小应至少为[MAX_HMID_LENGTH](capi-content-embed-common-h.md#宏定义)。 |
| size_t hmidSize | hmid缓冲区的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_SetHmid()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_SetHmid(ContentEmbed_Storage *storage, char *hmid, size_t hmidSize)
```

**描述**

设置OE格式文件目录的系统可识别标识符HMID。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE格式文件目录对象指针。 |
| char *hmid | 要设置的HMID值的字符数组。 |
| size_t hmidSize | hmid字符串的长度，不包括终止符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_Create()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Create(ContentEmbed_StorageElements **storageElements)
```

**描述**

创建并初始化ContentEmbed_StorageElements实例，用于存储和管理OE格式文件目录中的元素列表。创建成功后，调用者负责通过调用[OH_ContentEmbed_StorageElements_Destroy](capi-content-embed-document-h.md#oh_contentembed_storageelements_destroy)销毁实例，以避免内存泄漏。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) **storageElements | 输出参数。调用成功后，该指针将指向ContentEmbed_StorageElements实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_Destroy()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_Destroy(ContentEmbed_StorageElements *storageElements)
```

**描述**

销毁ContentEmbed_StorageElements实例并回收其占用的内存。调用此函数后，该ContentEmbed_StorageElements指针将失效，不得再使用。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向ContentEmbed_StorageElements实例指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_GetElements()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_GetElements(const ContentEmbed_Storage *storage, ContentEmbed_StorageElements *storageElements)
```

**描述**

获取OE格式文件目录中的元素列表。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *storage | 指向OE格式文件目录对象指针。 |
| [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 存储OE格式文件目录中的元素列表。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_GetCount()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetCount(const ContentEmbed_StorageElements *storageElements, size_t *count)
```

**描述**

获取ContentEmbed_StorageElements实例的元素数量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向ContentEmbed_StorageElements实例指针 |
| size_t *count | 输出参数。存储元素集合中的元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElements_GetElement()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElements_GetElement(const ContentEmbed_StorageElements *storageElements, size_t index, ContentEmbed_StorageElement **storageElement)
```

**描述**

获取ContentEmbed_StorageElements实例的指定索引位置的元素。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) *storageElements | 指向ContentEmbed_StorageElements实例指针 |
| size_t index | 要获取的元素的索引位置，从0开始计数。 |
| [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) **storageElement | 输出参数。指向ContentEmbed_StorageElement实例指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetName()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetName(const ContentEmbed_StorageElement *storageElement, char *name, size_t nameSize)
```

**描述**

获取ContentEmbed_StorageElement实例的名称。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | 指向ContentEmbed_StorageElement实例指针。 |
| char *name | 输出参数。用于存储元素名称字符串。 |
| size_t nameSize | 表示name缓冲区的大小（单位：字节）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetCTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetCTime(const ContentEmbed_StorageElement *element, uint64_t *ctime)
```

**描述**

获取ContentEmbed_StorageElement实例的创建时间戳，时间戳为自Unix纪元（1970年1月1日）以来的毫秒数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| storageElement | 指向ContentEmbed_StorageElement实例指针。 |
| uint64_t *ctime | 输出参数。指向存储元素的创建时间戳（单位：毫秒）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_GetMTime()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_GetMTime(const ContentEmbed_StorageElement *element, uint64_t *mtime)
```

**描述**

获取ContentEmbed_StorageElement实例的最后修改时间戳，时间戳为自Unix纪元（1970年1月1日）以来的毫秒数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| storageElement | 指向ContentEmbed_StorageElement实例指针。 |
| uint64_t *mtime | 输出参数。指向存储元素的最后修改时间戳（单位：毫秒）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_IsStorage()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStorage(const ContentEmbed_StorageElement *storageElement, bool *isStorage)
```

**描述**

检查ContentEmbed_StorageElement实例是否为OE格式文件目录类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) *storageElement | 指向ContentEmbed_StorageElement实例指针。 |
| bool *isStorage | 输出参数。true表示是OE格式文件目录，false表示不是。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_StorageElement_IsStream()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_StorageElement_IsStream(const ContentEmbed_StorageElement *element, bool *isStream)
```

**描述**

检查ContentEmbed_StorageElement实例是否为OE格式文件流类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| storageElement | 指向ContentEmbed_StorageElement实例指针。 |
| bool *isStream | 输出参数。true表示是OE格式文件流，false表示不是。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |

### OH_ContentEmbed_Storage_CopyTo()

```c
ContentEmbed_ErrorCode OH_ContentEmbed_Storage_CopyTo(ContentEmbed_Storage *srcStorage, ContentEmbed_Storage *destStorage)
```

**描述**

将源OE格式文件目录中的所有子目录和数据流（包括所有嵌套的子目录）复制到目标OE格式文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *srcStorage | 指向源OE格式文件目录对象指针。 |
| [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) *destStorage | 指向目标OE格式文件目录对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ContentEmbed_ErrorCode](capi-content-embed-common-h.md#contentembed_errorcode) | 返回特定的错误码。<br>     返回[CE_ERR_OK](capi-content-embed-common-h.md#contentembed_errorcode)表示操作成功。<br>     返回[CE_ERR_PARAM_INVALID](capi-content-embed-common-h.md#contentembed_errorcode)表示参数检查失败。<br>     返回[CE_ERR_NULL_POINTER](capi-content-embed-common-h.md#contentembed_errorcode)表示意外空指针。<br>     返回[CE_ERR_DEVICE_NOT_SUPPORTED](capi-content-embed-common-h.md#contentembed_errorcode)表示设备不支持。<br>     返回[CE_ERR_STORAGE_OPERATION_FAILED](capi-content-embed-common-h.md#contentembed_errorcode)表示存储操作失败。<br>     返回[CE_ERR_IN_DLP_SANDBOX](capi-content-embed-common-h.md#contentembed_errorcode)表示应用在DLP沙箱中，不支持此操作。 |
