# OH_CommonEvent

## 概述

本模块是公共事件服务（Common Event Service）对外开放的 C 语言 API 模块，为应用提供基于"发布—订阅"模型的跨进程事件通信能力：发布者发布一个公共事件后，系统根据事件名称将事件投递给所有已订阅该事件的订阅者，从而实现应用之间、应用与系统之间的解耦通信。

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_commonevent.h](capi-oh-commonevent-h.md) | 本模块定义了发布、订阅/取消订阅公共事件、事件回调数据访问、有序事件控制等关键操作函数，以及错误码枚举与核心数据类型定义。 |
| [oh_commonevent_support.h](capi-oh-commonevent-support-h.md) | 提供系统定义的公共事件常量。 |
