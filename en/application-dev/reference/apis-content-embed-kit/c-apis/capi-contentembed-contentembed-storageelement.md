# ContentEmbed_StorageElement

```c
typedef struct ContentEmbed_StorageElement ContentEmbed_StorageElement
```

## Overview

Defines the structure type of a storage element in an OE document. Use {@link OH_ContentEmbed_StorageElement_GetName} to get the name,<br>{@link OH_ContentEmbed_StorageElement_GetCTime} to get the creation time,<br>and {@link OH_ContentEmbed_StorageElement_GetMTime} to get the modification time.<br>Use {@link OH_ContentEmbed_StorageElement_IsStorage} to determine if the current object is an encapsulation<br>of {@link ContentEmbed_Storage}, and {@link OH_ContentEmbed_StorageElement_IsStream} to determine if it is an<br>encapsulation of {@link ContentEmbed_Stream}.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)

