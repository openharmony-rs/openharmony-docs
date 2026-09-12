# ContentEmbed_Storage

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_Storage ContentEmbed_Storage
```

## 概述

声明OE文档Storage结构体类型。类似于文件系统中的目录，用于组织和管理OE文档中的层级数据，除根Storage外，Storage对象的父对象必须是另一个Storage对象，适用于需要嵌套存储和组织文档元素的场景。<br>基于[ContentEmbed_Document](capi-contentembed-contentembed-document.md)实例，然后通过[OH_ContentEmbed_Document_GetRootStorage](capi-content-embed-document-h.md#oh_contentembed_document_getrootstorage)获取根Storage对象。<br>基于Storage对象和名称使用[OH_ContentEmbed_Storage_CreateStorage](capi-content-embed-document-h.md#oh_contentembed_storage_createstorage)在OE文档中创建一个子Storage对象，或使用[OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage)在OE文档中获取一个子Storage对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)
