# ContentEmbed_Stream

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_Stream ContentEmbed_Stream
```

## 概述

声明OE文档Stream结构体类型。类似于文件系统中的文件，可对其进行读取或写入，且Stream对象只能存在于Storage对象中。适用于在Storage对象中对OE文档内容进行流式读取或写入的场景。基于Storage对象和名称使用[OH_ContentEmbed_Storage_CreateStream](capi-content-embed-document-h.md#oh_contentembed_storage_createstream)在OE文档中创建一个Stream对象，或使用[OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream)在OE文档中获取一个Stream对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)
