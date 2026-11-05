# ContentEmbed_StorageElement

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:56:57.555Z pushedAt=2026-10-16T08:49:47.351Z -->

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## Overview

Defines the storage element struct of an OE document. After obtaining the object instance from [ContentEmbed_StorageElements](capi-contentembed-contentembed-storageelements.md) using [OH_ContentEmbed_StorageElements_GetElement](capi-content-embed-document-h.md#oh_contentembed_storageelements_getelement), you can use [OH_ContentEmbed_StorageElement_GetName](capi-content-embed-document-h.md#oh_contentembed_storageelement_getname) to obtain the name, [OH_ContentEmbed_StorageElement_GetCTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getctime) to obtain the creation time, and [OH_ContentEmbed_StorageElement_GetMTime](capi-content-embed-document-h.md#oh_contentembed_storageelement_getmtime) to obtain the modification time.<br>After checking whether the current element is an encapsulated object of [ContentEmbed_Storage](capi-contentembed-contentembed-storage.md) by using [OH_ContentEmbed_StorageElement_IsStorage](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstorage), you can use [OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage) to obtain a sub-storage object from the OE document.<br>After checking whether the current element is an encapsulated object of [ContentEmbed_Stream](capi-contentembed-contentembed-stream.md) using [OH_ContentEmbed_StorageElement_IsStream](capi-content-embed-document-h.md#oh_contentembed_storageelement_isstream), you can use [OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream) to obtain a stream object from the OE document.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)
