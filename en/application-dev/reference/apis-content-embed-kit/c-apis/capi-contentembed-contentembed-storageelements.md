# ContentEmbed_StorageElements

```c
typedef struct ContentEmbed_StorageElements ContentEmbed_StorageElements
```

## Overview

Declares the ContentEmbed_StorageElements structure. Use {@link OH_ContentEmbed_Storage_GetElements} to retrieve the collection of all {@link ContentEmbed_Storage} and<br>{@link ContentEmbed_Stream} objects under a specific {@link ContentEmbed_Storage} object, with each object<br>encapsulated as a {@link ContentEmbed_StorageElement} struct.<br>Use {@link OH_ContentEmbed_StorageElements_GetCount} to get the number of elements in the current query,<br>and {@link OH_ContentEmbed_StorageElements_GetElement} to obtain the {@link ContentEmbed_StorageElement} instance object at a specified index position.

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)

