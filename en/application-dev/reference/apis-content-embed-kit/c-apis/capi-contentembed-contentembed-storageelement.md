# ContentEmbed_StorageElement

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## Overview

Defines the structure type of a storage element in an OE document. Use [OH_ContentEmbed_StorageElement_GetName](capi-content-embed-document-h.md#oh_contentembed_storageelement_getname) to get the name, [OH_ContentEmbed_StorageElement_GetCTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getctime) to get the creation time, and [OH_ContentEmbed_StorageElement_GetMTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getmtime) to get the modification time. Use [OH_ContentEmbed_StorageElement_IsStorage](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstorage) to determine if the current object is an encapsulation of [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md), and [OH_ContentEmbed_StorageElement_IsStream](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstream) to determine if it is an encapsulation of [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md).

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)

