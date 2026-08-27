# AgentProxy（系统接口）

AgentExtensionAbility的代理对象，用于向AgentExtensionAbility等发送消息。@interface AgentProxy

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## authorize

```TypeScript
authorize(handshakeData: string): void
```

向AgentExtensionAbility发送鉴权。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handshakeData | string | 是 | 要发送的握手数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-ipc消息发送失败) | Failed to send the IPC message. |

## sendData

```TypeScript
sendData(data: string): void
```

向AgentExtensionAbility发送数据。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 要发送的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-ipc消息发送失败) | Failed to send the IPC message. |
