# ContentEmbed_Format

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:53:32.891Z pushedAt=2026-10-16T08:32:06.752Z -->

```c
typedef struct ContentEmbed_Format ContentEmbed_Format
```

## Overview

Defines the **ContentEmbed_Format** struct, which contains information about the OE document registered by the server app OE extension. Specifically, you can use [OH_ContentEmbed_GetOEidFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getoeidfromformat) to obtain the OEID, [OH_ContentEmbed_GetNameAndDescriptionFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getnameanddescriptionfromformat) to obtain the name and description, [OH_ContentEmbed_GetIconFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_geticonfromformat) to obtain the icon, and [OH_ContentEmbed_GetFileNameExtensionsFromFormat](capi-content-embed-proxy-h.md#oh_contentembed_getfilenameextensionsfromformat) to obtain the file name extensions.

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_proxy.h](capi-content-embed-proxy-h.md)
