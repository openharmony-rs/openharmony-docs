# ContentEmbed_Info

```c
typedef struct ContentEmbed_Info ContentEmbed_Info
```

## Overview

Declares the ContentEmbed_Info structure. Use [OH_ContentEmbed_GetContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_getcontentembedinfo) to query the OE document information registered by all server-side applications for the current session. Then, use [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo) to obtain the count of [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances in the current query result, and use [OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo) to retrieve the instance object at the specified index.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_proxy.h](capi-content-embed-proxy-h.md)

