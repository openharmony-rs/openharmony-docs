# ContentEmbed_Document

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_Document ContentEmbed_Document
```

## 概述

声明OE文档结构体类型。封装了被嵌入文档的元数据、内容和存储结构，用于在应用中统一管理嵌入文档的数据，便于对嵌入文档进行访问、解析与存储。<br>开发者可根据数据来源选取：<br>拥有OEID时使用[OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid)；<br>拥有源文件并需嵌入/链接时使用[OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)；<br>拥有已保存的OE格式文件时使用[OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile)。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_document.h](capi-content-embed-document-h.md)
