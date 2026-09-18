# createAbilityConnectionSession

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createAbilityConnectionSession

```TypeScript
function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,
        connectOptions: ConnectOptions): number
```

创建应用间的协同会话。协同会话用于管理跨设备通信的连接状态，需要先在两端设备分别创建会话，然后通过connect建立连接。

**起始版本：** 18

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO and ohos.permission.SET_NETWORK_INFO and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceName | string | 是 | 应用设置的服务名称（两端必须一致），最大长度为256字符。 |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 表示应用上下文。 |
| peerInfo | [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | 是 | 对端的协同信息。 |
| connectOptions | [ConnectOptions](arkts-distributedservice-abilityconnectionmanager-connectoptions-i.md) | 是 | 应用设置的连接选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 成功创建的协同会话ID，用于后续的connect、acceptConnect、sendMessage、sendData、disconnect等接口调用。取值范围是大于100的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: Failed to call the API due to limited device capabilities. |

**示例**

```TypeScript
在设备A上，调用createAbilityConnectionSession()接口创建协同会话并返回sessionId。
```

```TypeScript
在设备B上，对于createAbilityConnectionSession接口的调用，可在应用被拉起后触发协同生命周期函数onCollaborate时，在onCollaborate内进行。
```
