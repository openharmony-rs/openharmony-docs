# ContentEmbed_Info

```c
typedef struct ContentEmbed_Info ContentEmbed_Info
```

## 概述

声明ContentEmbed_Info结构体类型。通过{@link OH_ContentEmbed_GetContentEmbedInfo}查询当前所有服务端应用注册的<br>OE文档信息，然后通过{@link OH_ContentEmbed_GetFormatCountFromInfo}获取当前查询{@link ContentEmbed_Format}实例的数量，<br>并通过{@link OH_ContentEmbed_GetFormatFromInfo}获取指定索引位置的实例对象。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_proxy.h](capi-content-embed-proxy-h.md)

