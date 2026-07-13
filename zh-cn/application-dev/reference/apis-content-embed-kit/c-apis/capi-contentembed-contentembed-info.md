# ContentEmbed_Info

```c
typedef struct ContentEmbed_Info ContentEmbed_Info
```

## 概述

声明ContentEmbed_Info结构体类型。通过[OH_ContentEmbed_GetContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_getcontentembedinfo)查询当前所有服务端应用注册的OE文档信息，然后通过[OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo)获取当前查询[ContentEmbed_Format](capi-contentembed-contentembed-format.md)实例的数量，并通过[OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo)获取指定索引位置的实例对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_proxy.h](capi-content-embed-proxy-h.md)

