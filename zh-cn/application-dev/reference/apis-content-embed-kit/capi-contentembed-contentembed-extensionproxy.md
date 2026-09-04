# ContentEmbed_ExtensionProxy

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_ExtensionProxy ContentEmbed_ExtensionProxy
```

## 概述

声明ContentEmbed_ExtensionProxy结构体类型。用于指向OE文档在客户端封装的文档嵌入和编辑的程序对象（简称客户端OE对象）。在OE文档嵌入和编辑场景中，作为客户端OE对象的句柄，用于调用文档嵌入、编辑等相关接口。开发者通过[OH_ContentEmbed_CreateExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_createextensionproxy)创建客户端OE对象，使用[OH_ContentEmbed_Proxy_StartWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)建立与服务端的通信后，使用[OH_ContentEmbed_Proxy_GetSnapshot](capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)获取OE文档快照图，通过[OH_ContentEmbed_Proxy_DoEdit](capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit)实现编辑功能。通信结束后，使用[OH_ContentEmbed_Proxy_StopWork](capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork)断开连接，通过[OH_ContentEmbed_DestroyExtensionProxy](capi-content-embed-proxy-h.md#oh_contentembed_destroyextensionproxy)销毁实例。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_proxy.h](capi-content-embed-proxy-h.md)
