# AgentExtensionConnectCallback（系统接口）

开发者可以通过AgentExtensionConnectCallback中提供的回调接口来接收服务端发送的数据和安全认证请求，以及感知AgentExtensionAbility服务端的断开连接操作。

**起始版本：** 24

<!--Device-unnamed-export interface AgentExtensionConnectCallback--><!--Device-unnamed-export interface AgentExtensionConnectCallback-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## onAuth

```TypeScript
onAuth(handshakeData: string): void
```

接收来自AgentExtensionAbility服务端的安全认证的回调接口。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AgentExtensionConnectCallback-onAuth(handshakeData: string): void--><!--Device-AgentExtensionConnectCallback-onAuth(handshakeData: string): void-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handshakeData | string | 是 | 接收到的来自AgentExtensionAbility服务端的安全认证数据。 |

## onData

```TypeScript
onData(data: string): void
```

接收来自AgentExtensionAbility服务端的数据的回调接口。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AgentExtensionConnectCallback-onData(data: string): void--><!--Device-AgentExtensionConnectCallback-onData(data: string): void-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 接收到的来自AgentExtensionAbility服务端的数据。 |

## onDisconnect

```TypeScript
onDisconnect(): void
```

与AgentExtensionAbility服务端断开连接时触发的回调接口。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AgentExtensionConnectCallback-onDisconnect(): void--><!--Device-AgentExtensionConnectCallback-onDisconnect(): void-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

