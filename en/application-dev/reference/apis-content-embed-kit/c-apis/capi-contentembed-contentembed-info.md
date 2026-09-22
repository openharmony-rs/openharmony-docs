# ContentEmbed_Info

```c
typedef struct ContentEmbed_Info ContentEmbed_Info
```

## Overview

Declares the ContentEmbed_Info structure. Use {@link OH_ContentEmbed_GetContentEmbedInfo} to query the<br>OE document information registered by all server-side applications for the current session.<br>Then, use {@link OH_ContentEmbed_GetFormatCountFromInfo} to obtain the count of {@link ContentEmbed_Format}<br>instances in the current query result, and use {@link OH_ContentEmbed_GetFormatFromInfo} to retrieve the instance object at the specified index.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_proxy.h](capi-content-embed-proxy-h.md)

