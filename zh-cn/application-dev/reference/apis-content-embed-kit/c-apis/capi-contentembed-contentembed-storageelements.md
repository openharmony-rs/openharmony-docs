# ContentEmbed_StorageElements

```c
typedef struct ContentEmbed_StorageElements ContentEmbed_StorageElements
```

## 概述

声明ContentEmbed_StorageElements结构体类型。通过[OH_ContentEmbed_Storage_GetElements](capi-content-embed-document-h.md#oh_contentembed_storage_getelements)获取某个[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)对象下所有的[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)和[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)对象集合，每个对象封装成[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)结构体。可以通过[OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount)获取当前查询元素的数量，[OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement)获取指定索引位置的[ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md)实例对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)

