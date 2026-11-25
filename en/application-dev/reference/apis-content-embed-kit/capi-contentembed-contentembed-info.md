# ContentEmbed_Info

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:54:00.356Z pushedAt=2026-10-16T08:34:13.880Z -->

```c
typedef struct ContentEmbed_Info ContentEmbed_Info
```

## Overview

Defines the **ContentEmbed_Info** struct. You can use [OH_ContentEmbed_GetContentEmbedInfo](capi-content-embed-proxy-h.md#oh_contentembed_getcontentembedinfo) to query all OE documents registered by server apps, use [OH_ContentEmbed_GetFormatCountFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatcountfrominfo) to obtain the number of queried [ContentEmbed_Format](capi-contentembed-contentembed-format.md) instances, and use [OH_ContentEmbed_GetFormatFromInfo](capi-content-embed-proxy-h.md#oh_contentembed_getformatfrominfo) to obtain the instance at the specified index position.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_proxy.h](capi-content-embed-proxy-h.md)
