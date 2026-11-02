# ContentEmbed_ExtensionContext*

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:47:10.307Z pushedAt=2026-10-16T08:04:45.883Z -->

```c
typedef struct ContentEmbed_ExtensionContext* ContentEmbed_ExtensionContextHandle
```

## Overview

Defines the pointer type of the OE extension context object. This pointer object is used to carry and manage the running context of the OE extension in the **ContentEmbed** extension process.<br>You can obtain the context from the OE extension instance by calling [OH_ContentEmbed_Extension_GetContentEmbedContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontentembedcontext). You can use [OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext) to obtain the AbilityRuntime context, start the UIAbility using [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) or [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions), and destroy the OE extension using [OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability).

**Since**: 24

**Related module**: [ContentEmbed](capi-contentembed.md)

**Header file**: [content_embed_extension.h](capi-content-embed-extension-h.md)
