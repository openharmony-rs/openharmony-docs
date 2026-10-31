# ContentEmbed_StorageElement

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## 概述

声明OE文档存储元素的结构体类型。通过[OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement)从[ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md)获取该对象实例后，可通过[OH_ContentEmbed_StorageElement_GetName](capi-content-embed-document-h.md#oh_contentembed_storageelement_getname)获取名称、[OH_ContentEmbed_StorageElement_GetCTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getctime)获取创建时间和[OH_ContentEmbed_StorageElement_GetMTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getmtime)获取修改时间。<br>通过[OH_ContentEmbed_StorageElement_IsStorage](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstorage)判断当前元素是[ContentEmbed_Storage](capi-contentembed-contentembed-storage.md)的封装对象后，可以使用[OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage)在OE文档中获取一个子Storage对象。<br>通过[OH_ContentEmbed_StorageElement_IsStream](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstream)判断当前元素是[ContentEmbed_Stream](capi-contentembed-contentembed-stream.md)的封装对象后，可以使用[OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream)在OE文档中获取一个Stream对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)
