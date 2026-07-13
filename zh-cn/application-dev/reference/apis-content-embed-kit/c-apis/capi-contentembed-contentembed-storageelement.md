# ContentEmbed_StorageElement

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## 概述

声明OE文档存储元素的结构体类型。通过[OH_ContentEmbed_StorageElement_GetName](capi-content-embed-document-h.md#oh_contentembed_storageelement_getname)获取名称、[OH_ContentEmbed_StorageElement_GetCTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getctime)获取创建时间和[OH_ContentEmbed_StorageElement_GetMTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getmtime)获取修改时间。可以通过[OH_ContentEmbed_StorageElement_IsStorage](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstorage)判断当前是否是[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)的封装对象，[OH_ContentEmbed_StorageElement_IsStream](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstream)判断当前是否是[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)的封装对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)

