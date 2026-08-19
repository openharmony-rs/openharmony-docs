# MessageHandler(定义ArkTS的EAWorker消息处理器)

MessageHandler类提供EAWorker消息通信相关的类型。 MessageHandler用于定义消息（Message）的处理逻辑，不同消息可以由不同的MessageHandler处理。 MessageHandler提供消息调度和队列管理能力，包括发送消息、检查消息队列、移除待执行消息等操作。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export namespace concurrency--><!--Device-unnamed-export namespace concurrency-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MessageHandler(定义ArkTS的EAWorker消息处理器)](arkts-na-concurrency-messagehandler-c.md) | 处理消息并提供消息调度能力。不同消息可由不同的MessageHandler处理。 |

