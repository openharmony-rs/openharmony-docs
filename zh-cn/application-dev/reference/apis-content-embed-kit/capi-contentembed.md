# ContentEmbed

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

内容嵌入（ContentEmbed）模块提供对象编辑（Object Editor，简称OE）功能框架，支持应用间文档的嵌入与协同编辑。<br>模块采用客户端-服务端架构：服务端应用通过扩展（extension）接口实现OE Extension；客户端应用通过代理（proxy）接口查询服务端应用注册的OE Extension信息并与该OE Extension交互。<br>通过OE技术实现的被嵌入文档（简称OE文档），在客户端界面可呈现为缩略图或快照（Snapshot），或以OE格式序列化为二进制数据，保存在内存或文件（称为OE格式文件）中。

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [content_embed_common.h](capi-content-embed-common-h.md) | 提供内容嵌入模块的错误码定义和嵌入文档支持能力枚举。 |
| [content_embed_document.h](capi-content-embed-document-h.md) | 提供通过OE技术实现的被嵌入文档（简称OE文档）的数据结构及操作接口。<br>本模块核心概念采用Document-Storage-Stream层级存储结构，其中Document为顶层容器，Storage类似于文件系统中的目录可包含子Storage和Stream，Stream类似于文件支持二进制数据读写。 |
| [content_embed_extension.h](capi-content-embed-extension-h.md) | 定义服务端应用OE Extension相关数据结构和操作接口，提供OE Extension实例生命周期管理、客户端OE对象关联与回调注册、快照获取及编辑操作等能力，适用于在服务端处理文档嵌入与编辑场景。 |
| [content_embed_proxy.h](capi-content-embed-proxy-h.md) | 为客户端应用提供服务端应用注册的OE Extension信息查询接口和与服务端OE Extension对象交互的数据结构及相关操作接口。适用于客户端应用需要查询服务端OE Extension信息、与OE Extension对象进行交互（如创建代理、注册回调、编辑文档、获取快照等）的场景。 |
