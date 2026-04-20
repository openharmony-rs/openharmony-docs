# ContentEmbed

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @wanxiaoguo-->
<!--Designer: @zhuwei;@weiguoning-->
<!--Tester: @yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

内容嵌入（ContentEmbed）模块提供对象编辑（Object Editor，简称OE）功能框架与技术，支持应用间文档的嵌入与协同编辑。<br> 通过OE技术实现的被嵌入文档（简称OE文档），在客户端界面中可能呈现为缩略图或者快照（Snapshot），也可能以标准格式序列化为一段二进制数据保存在内存或者某个文件（称为OE格式文件）中。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [content_embed_common.h](capi-content-embed-common-h.md) | 提供内容嵌入模块的错误码定义和嵌入文档支持能力的类型枚举描述。 |
| [content_embed_document.h](capi-content-embed-document-h.md) | 提供OE技术实现的被嵌入文档（简称OE文档）相关数据结构及对应操作接口。 |
| [content_embed_extension.h](capi-content-embed-extension-h.md) | 定义服务端应用OE Extension相关数据结构和操作接口。 |
| [content_embed_proxy.h](capi-content-embed-proxy-h.md) | 为客户端应用提供服务端应用注册的OE Extension信息查询接口和与服务端OE Extension对象交互的数据结构及相关操作接口。 |
