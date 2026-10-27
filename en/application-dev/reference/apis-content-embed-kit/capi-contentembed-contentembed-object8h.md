# ContentEmbed_Object*

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:56:01.742Z pushedAt=2026-10-16T08:36:41.832Z -->

```c
typedef struct ContentEmbed_Object* ContentEmbed_ObjectHandle
```

## Overview

Defines the pointer type of the **ContentEmbed_Object** object. When the client connects to the server, the system creates an instance of this object, calls back the [OH_ContentEmbed_Extension_OnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_onobjectattachfunc) function registered by [OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc](capi-content-embed-extension-h.md#oh_contentembed_extension_registeronobjectattachfunc), and passes the instance pointer of this type.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_extension.h](capi-content-embed-extension-h.md)
