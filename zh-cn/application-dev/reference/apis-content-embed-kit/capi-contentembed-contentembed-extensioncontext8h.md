# ContentEmbed_ExtensionContext*

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_ExtensionContext* ContentEmbed_ExtensionContextHandle
```

## 概述

声明OE Extension上下文对象指针类型。该指针对象用于在ContentEmbed Extension流程中承载和管理OE Extension的运行上下文信息。<br>可通过[OH_ContentEmbed_Extension_GetContentEmbedContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontentembedcontext)从OE Extension实例获取，支持通过[OH_ContentEmbed_Extension_GetContext](capi-content-embed-extension-h.md#oh_contentembed_extension_getcontext)获取AbilityRuntime上下文、[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)启动自身UIAbility及[OH_ContentEmbed_Extension_ContextTerminateAbility](capi-content-embed-extension-h.md#oh_contentembed_extension_contextterminateability)销毁OE Extension等操作。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_extension.h](capi-content-embed-extension-h.md)
