# EventCallbackInfo

回调方法的接收信息。

**起始版本：** 18

<!--Device-abilityConnectionManager-interface EventCallbackInfo--><!--Device-abilityConnectionManager-interface EventCallbackInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## data

```TypeScript
data?: ArrayBuffer
```

表示接收的字节流。

**类型：** ArrayBuffer

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-data?: ArrayBuffer--><!--Device-EventCallbackInfo-data?: ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## msg

```TypeScript
msg?: string
```

表示接收的消息。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-msg?: string--><!--Device-EventCallbackInfo-msg?: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: DisconnectReason
```

表示断连原因。

**类型：** DisconnectReason

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-reason?: DisconnectReason--><!--Device-EventCallbackInfo-reason?: DisconnectReason-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## sessionId

```TypeScript
sessionId: number
```

表示当前事件对应的协同会话ID。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-sessionId: int--><!--Device-EventCallbackInfo-sessionId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

