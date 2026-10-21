# ContentEmbed_StorageElements

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:57:19.994Z pushedAt=2026-10-16T08:56:52.161Z -->

```c
typedef struct ContentEmbed_StorageElements ContentEmbed_StorageElements
```

## Overview

Defines the **ContentEmbed_StorageElements** struct. This struct obtains all [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) and [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) objects under a [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object through [OH_ContentEmbed_Storage_GetElements](capi-content-embed-document-h.md#oh_contentembed_storage_getelements). Each object is encapsulated into a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) struct. You can use [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount) to obtain the number of elements in the current query and [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement) to obtain the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance object at a specified index position.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)
