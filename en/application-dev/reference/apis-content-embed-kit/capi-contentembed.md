# ContentEmbed

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

The **ContentEmbed** module provides the Object Editor (OE) framework to support document embedding and collaborative editing between apps.<br>The module adopts the client-server architecture. The server app implements OE extension through the extension API. The client app queries the OE extension registered by the server app through the proxy API and interacts with the OE extension.<br>An embedded document (OE document for short) implemented by using the OE technology may be presented as a thumbnail or a snapshot on a client UI, or may be serialized into binary data in OE format and stored in the memory or a file (referred to as an OE format file).

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24
## Files

| Name| Description|
| -- | -- |
| [content_embed_common.h](capi-content-embed-common-h.md) | Defines the error codes of the **ContentEmbed** module and enumerates the capabilities supported by embedded documents.|
| [content_embed_document.h](capi-content-embed-document-h.md) | Provides the data structures and corresponding operation APIs related to the embedded documents (OE documents) implemented using the OE technology.<br>This module uses the hierarchical storage structure of **Document**-**Storage**-**Stream**. **Document** is the top-level container. **Storage** is similar to a directory in a file system and can contain the sub-storage and stream. **Stream** is similar to a file and supports binary data read and write.|
| [content_embed_extension.h](capi-content-embed-extension-h.md) | Defines the data structures and operation APIs related to the OE extension in server apps and provides capabilities such as OE extension instance lifecycle management, client OE object association and callback registration, and snapshot obtaining and editing. This module is applicable to document embedding and editing on the server.|
| [content_embed_proxy.h](capi-content-embed-proxy-h.md) | Provides client apps with APIs for querying the OE extension information registered by server apps, data structures for interacting with the server OE extension object, and related operation APIs. This module is applicable to scenarios where client apps need to query the OE extension information registered by server apps and interact with the server OE extension object. For example, APIs provided by this module can be used to create a proxy, register a callback, edit a document, or obtain a snapshot.|
