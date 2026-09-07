# ContentEmbed_ExtensionInstance

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_ExtensionInstance ContentEmbed_ExtensionInstance
```

## 概述

声明OE Extension实例的结构体类型。管理扩展的生命周期、回调注册和客户端OE对象关联等核心功能。适用于服务端应用需要嵌入OE扩展能力并完成扩展与客户端OE文档之间生命周期同步、回调监听及对象关联绑定的场景。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_extension.h](capi-content-embed-extension-h.md)
