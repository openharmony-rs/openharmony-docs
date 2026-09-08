# ContentEmbed_ExtensionInstance*

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_ExtensionInstance* ContentEmbed_ExtensionInstanceHandle
```

## 概述

声明OE Extension实例对象指针类型。需要在[OH_AbilityRuntime_OnNativeExtensionCreate](../apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate)函数实现里通过[OH_ContentEmbed_Extension_GetExtensionInstance](capi-content-embed-extension-h.md#oh_contentembed_extension_getextensioninstance)方法，在OE Extension被系统启动时获取OE Extension实例对象。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_extension.h](capi-content-embed-extension-h.md)
