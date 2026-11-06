# ContentEmbed_Stream

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:57:45.569Z pushedAt=2026-10-16T09:06:58.234Z -->

```c
typedef struct ContentEmbed_Stream ContentEmbed_Stream
```

## Overview

Defines the **Stream** struct of an OE document. Similar to a file in the file system, data can be read from or written to this struct. A stream object can exist only in a storage object. This struct is applicable to scenarios where OE document content is read or written in stream mode in a storage object. Use [OH_ContentEmbed_Storage_CreateStream](capi-content-embed-document-h.md#oh_contentembed_storage_createstream) to create a stream object in the OE document based on the storage object and name, or use [OH_ContentEmbed_Storage_GetStream](capi-content-embed-document-h.md#oh_contentembed_storage_getstream) to obtain a stream object from the OE document.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)
