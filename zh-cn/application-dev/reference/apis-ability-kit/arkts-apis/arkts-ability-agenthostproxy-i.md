# AgentHostProxy

AgentHostProxy用于从 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)服务端向客户端发送数据或安全认证请求。

> **说明：**
> 
> - 本模块接口需要在主线程中使用，不支持在Worker、TaskPool等子线程中使用。
@interface AgentHostProxy

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## authorize

```TypeScript
authorize(handshakeData: string): void
```

从[AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)服务端给客户端发送安全认证请求。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handshakeData | string | 是 | 待发送到客户端的安全认证数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-ipc消息发送失败) | Failed to send the IPC message. |

## sendData

```TypeScript
sendData(data: string): void
```

从[AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)服务端给客户端发送数据。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 待发送到[AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)客户端的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-ipc消息发送失败) | Failed to send the IPC message. |
