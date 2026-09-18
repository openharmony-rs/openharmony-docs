# ContentEmbed_StorageElements

```c
typedef struct ContentEmbed_StorageElements ContentEmbed_StorageElements
```

## Overview

Declares the ContentEmbed_StorageElements structure. Use [OH_ContentEmbed_Storage_GetElements](capi-content-embed-document-h.md#oh_contentembed_storage_getelements) to retrieve the collection of all [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) and [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) objects under a specific [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) object, with each object encapsulated as a [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) struct. Use [OH_ContentEmbed_StorageElements_GetCount](capi-content-embed-document-h.md#oh_contentembed_storageelements_getcount) to get the number of elements in the current query, and [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement) to obtain the [ContentEmbed_StorageElement](capi-contentembed-contentembed-storageelement.md) instance object at a specified index position.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)

