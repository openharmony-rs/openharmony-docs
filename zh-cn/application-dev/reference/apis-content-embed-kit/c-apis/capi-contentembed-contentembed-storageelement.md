# ContentEmbed_StorageElement

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## 概述

声明OE文档存储元素的结构体类型。通过{@link OH_ContentEmbed_StorageElement_GetName}获取名称、<br>{@link OH_ContentEmbed_StorageElement_GetCTime}获取创建时间和{@link OH_ContentEmbed_StorageElement_GetMTime}获取修改<br>时间。可以通过{@link OH_ContentEmbed_StorageElement_IsStorage}判断当前是否是{@link ContentEmbed_Storage}的封装对象，<br>{@link OH_ContentEmbed_StorageElement_IsStream}判断当前是否是{@link ContentEmbed_Stream}的封装对象。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)

