# Message(定义ArkTS的EAWorker消息)

Message类提供EAWorker消息通信相关的类型。 Message表示消息队列中的一个消息，消息可以携带数据和回调函数。构造消息时需要指定MessageHandler来指定消息处理的逻辑。

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
| [Message(定义ArkTS的EAWorker消息)](arkts-na-concurrency-message-c.md) | 表示消息队列中的一个消息，可携带数据和回调函数，发送至MessageHandler进行处理。 |

