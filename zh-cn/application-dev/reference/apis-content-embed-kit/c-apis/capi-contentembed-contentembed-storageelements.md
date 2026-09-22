# ContentEmbed_StorageElements

```c
typedef struct ContentEmbed_StorageElements ContentEmbed_StorageElements
```

## 概述

声明ContentEmbed_StorageElements结构体类型。通过{@link OH_ContentEmbed_Storage_GetElements}获取某个<br>{@link ContentEmbed_Storage}对象下所有的{@link ContentEmbed_Storage}和{@link ContentEmbed_Stream}对象集合，每个对象封装<br>成{@link ContentEmbed_StorageElement}结构体。可以通过{@link OH_ContentEmbed_StorageElements_GetCount}获取当前查询元素<br>的数量，{@link OH_ContentEmbed_StorageElements_GetElement}获取指定索引位置的{@link ContentEmbed_StorageElement}实例对象。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)

