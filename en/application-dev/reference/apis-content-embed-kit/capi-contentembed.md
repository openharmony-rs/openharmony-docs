# ContentEmbed

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

The ContentEmbed module provides the Object Editor (OE) framework and technologies to support document embedding and collaborative editing between applications.<br> An embedded document (OE document for short) implemented by using the OE technology may be presented as a thumbnail or a snapshot on a client UI, or may be serialized into a segment of binary data in a standard format and stored in a memory or a file (referred to as an OE format file).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24
## Files

| Name| Description|
| -- | -- |
| [content_embed_common.h](capi-content-embed-common-h.md) | Provides the error code definitions for the ContentEmbed module and the type enumeration descriptions for the capabilities supported by embedded documents.|
| [content_embed_document.h](capi-content-embed-document-h.md) | Provides the data structures and corresponding operation APIs related to the embedded documents (OE documents) implemented using the OE technology.|
| [content_embed_extension.h](capi-content-embed-extension-h.md) | Defines the data structures and operation APIs related to the OE Extension of the server application.|
| [content_embed_proxy.h](capi-content-embed-proxy-h.md) | Provides the client application with the API for querying the OE Extension information registered by the server application, the data structures for interacting with the server OE Extension object, and the related operation APIs.|
