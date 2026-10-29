# ContentEmbed_ExtensionInstanceHandle

```c
typedef struct ContentEmbed_ExtensionInstanceHandle ContentEmbed_ExtensionInstanceHandle
```

## 概述

声明OE Extension实例对象指针类型。需要在[OH_AbilityRuntime_OnNativeExtensionCreate](../../apis-ability-kit/c-apis/capi-extension-ability-h.md#变量)函数实现里通过 [OH_ContentEmbed_Extension_GetExtensionInstance](capi-content-embed-extension-h.md#oh_contentembed_extension_getextensioninstance)方法，在OE Extension被系统启动时获取OE Extension实例对象。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_extension.h](capi-content-embed-extension-h.md)

