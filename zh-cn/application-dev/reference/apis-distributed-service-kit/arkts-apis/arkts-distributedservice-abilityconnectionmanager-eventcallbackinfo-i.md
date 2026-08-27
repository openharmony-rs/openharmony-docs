# EventCallbackInfo

回调方法的接收信息。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## data

```TypeScript
data?: ArrayBuffer
```

表示接收的字节流。触发receiveData事件时存在，包含接收到的二进制数据。其他事件类型下不存在。

**类型：** ArrayBuffer

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## msg

```TypeScript
msg?: string
```

表示接收的消息。触发receiveMessage事件时存在，包含接收到的文本消息内容。其他事件类型下不存在。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: DisconnectReason
```

表示断连原因。触发disconnect事件时存在，用于标识具体的断连原因。其他事件类型下不存在。

**类型：** [DisconnectReason](arkts-distributedservice-abilityconnectionmanager-disconnectreason-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## sessionId

```TypeScript
sessionId: number
```

表示当前事件对应的协同会话ID。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
