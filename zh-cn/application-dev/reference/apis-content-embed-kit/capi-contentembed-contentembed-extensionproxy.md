# ContentEmbed_ExtensionProxy
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct ContentEmbed_ExtensionProxy ContentEmbed_ExtensionProxy
```

## 概述

声明OE对象结构体类型。作为客户端与OE Extension之间的通信代理，负责与服务端进行交互。每个 OE 文档在客户端中都会对应一个相应的 OE 对象，用于管理该文档的相关操作与状态。

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

**所在头文件：** [content_embed_proxy.h](capi-content-embed-proxy-h.md)
