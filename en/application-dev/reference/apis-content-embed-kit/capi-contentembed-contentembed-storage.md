# ContentEmbed_Storage

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:56:30.267Z pushedAt=2026-10-16T08:43:38.972Z -->

```c
typedef struct ContentEmbed_Storage ContentEmbed_Storage
```

## Overview

Defines the **Storage** struct of an OE document. Similar to a directory in a file system, this struct is used to organize and manage hierarchical data in an OE document. Except for the root storage, the parent object of a storage object must be another storage object. This is applicable to scenarios where nested storage and document element organization are required.<br>Create a [ContentEmbed_Document](capi-contentembed-contentembed-document.md) instance and then obtain the root storage object using [OH_ContentEmbed_Document_GetRootStorage](capi-content-embed-document-h.md#oh_contentembed_document_getrootstorage).<br>Use [OH_ContentEmbed_Storage_CreateStorage](capi-content-embed-document-h.md#oh_contentembed_storage_createstorage) to create a sub-storage object in the OE document based on the storage object and name, or use [OH_ContentEmbed_Storage_GetStorage](capi-content-embed-document-h.md#oh_contentembed_storage_getstorage) to obtain a sub-storage object from the OE document.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)
