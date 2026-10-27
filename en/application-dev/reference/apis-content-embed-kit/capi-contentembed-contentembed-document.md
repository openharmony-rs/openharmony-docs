# ContentEmbed_Document

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:46:21.200Z pushedAt=2026-10-16T08:03:00.232Z -->

```c
typedef struct ContentEmbed_Document ContentEmbed_Document
```

## Overview

Defines the struct of an OE document. This struct encapsulates the metadata, content, and storage structure of an embedded document. It is used to manage the data of embedded documents in a unified manner within an app, facilitating access, parsing, and storage of the embedded documents.<br>You can select a method based on the data source:<br>Use [OH_ContentEmbed_CreateDocumentByOEid](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyoeid) if you have the OEID.<br>Use [OH_ContentEmbed_CreateDocumentByFile](capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile) if you have the source file and need to embed or link it.<br>Use [OH_ContentEmbed_LoadDocumentFromFile](capi-content-embed-document-h.md#oh_contentembed_loaddocumentfromfile) if you have a saved OE file.

**Since**: 24

**Relevant module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_document.h](capi-content-embed-document-h.md)
