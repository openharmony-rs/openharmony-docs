# ContentEmbed_ExtensionProxy

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:49:47.974Z pushedAt=2026-10-16T08:23:11.383Z -->

```c
typedef struct ContentEmbed_ExtensionProxy ContentEmbed_ExtensionProxy
```

## Overview

Defines the ContentEmbed_ExtensionProxy struct. This struct points to the program object (client OE object for short) that encapsulates the document embedding and editing functions of the OE document on the client. In the OE document embedding and editing scenarios, this struct serves as the handle to the client OE object and is used to call APIs related to document embedding and editing. You can use [OH_ContentEmbed_CreateExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_createextensionproxy) to create a client OE object, use [OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to establish communication with the server, use [OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot) to obtain the snapshot of the OE document, and use [OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit) to implement the editing function. After the communication is complete, use [OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork) to terminate the connection and call [OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy) to destroy the instance.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_proxy.h](capi-content-embed-proxy-h.md)
